# Crowd-Funding-Platform
The Crowd Funding Platform project is a user-friendly app connecting creators and investors. It lets entrepreneurs create funding campaigns, allows investors to browse and invest, and offers personalized dashboards. The purpose of this project is to evaluate your programming and logical skills. Each task comes with a predefined description and examples to assist you.

## Project Description
The Crowd Funding Platform project aims to create a user-friendly application connecting idea creators with potential investors. It allows entrepreneurs to create project campaigns with funding goals, while investors can browse and invest in projects they find compelling. The platform  offers personalized dashboards for investors to track their investments, it also includes features like project addition, feedback, and error handling for a seamless user experience. This project provides an opportunity to enhance skills in data modeling, database querying, error handling, and API design.

## Step-by-Step Process of Live Project Execution

## Task 1: Creating a New Project: Building the Foundation for Innovation
In this task, you will implement a POST "/project" endpoint to add a new project to the system. Users will submit project details in JSON format, including the title, description, category, funding goal, and current funding status.

Upon successful addition, the endpoint will respond with the project details, including the newly generated project ID, creation date, and update date.Where createdAt and updatedAt date will be set to current date and currentFunding will be set to 0.00 initially.

The input JSON should include the following details:

    {   
        "title": "My Healthcare Project",   
        "description": "A great healthcare initiative",   
        "category": "Healthcare",   
        "fundingGoal": 50000.00,   
        "currentFunding": 0.00 
    }

This task will handle exceptions, specifically : 1)"All fields must be provided.":No input data can be null or empty. 2)"Funding goal must be a positive non-zero value.":funding goal cannot be negative or 0. 3)"Project with the same title already exists.":when a project with the same title already exists.

Upon successful addition of the project in the "projects" table, the response will include the project details as follows:

    {   
        "id": 1,   
        "title": "My Healthcare Project",   
        "description": "A great healthcare initiative",   
        "category": "Healthcare",   
        "fundingGoal": 50000.00,   
        "currentFunding": 0.00,   
        "createdAt": "2023-07-22",   
        "updatedAt": "2023-07-22" 
    }

By implementing this task you will learn to handle user input in the form of JSON and process it to create and store project details in a database table. You will also learn to handle exceptions, specifically when a project with the same title already exists. The response formatting will involve sending meaningful success and failure messages along with appropriate HTTP status codes.

## Task 2: Embarking on the Quest for Creativity: Discovering All Projects
In this task, you will implement a GET endpoint "/project" to retrieve all projects from the system. The endpoint will respond with a JSON array containing details of all projects stored in the "projects" table. If no projects are found, a failure response will be sent, indicating that no projects are available for funding.

Output: If projects are found, the response will be in JSON format containing an array of project details:

    [   
        {         
            "id": 1,         
            "title": "My Healthcare Project",         
            "description": "A great healthcare initiative",         
            "category": "Healthcare",         
            "fundingGoal": 50000.00,         
            "currentFunding": 0.00,         
            "createdAt": "2023-07-22",         
            "updatedAt": "2023-07-22"    
        } 
    ]

If no projects are available, a failure response will be sent:

    {   
        "success":false,   
        "message": "No projects found for funding" 
    } 

By implementing this you will learn to fetch data from a database table and format it as JSON for response. You will also learn to handle cases where no projects are available, sending an appropriate failure response. This task will help you to understand how to retrieve and display data to users through RESTful endpoints.

## Task 3: Navigating the Sea of Categories: Unveiling Projects by Category
In this task, you will implement a GET endpoint "/project?category={category}" to retrieve all projects with a specific category. Users will provide the category as a query parameter. The endpoint will respond with a JSON array containing project details for projects belonging to the specified category. If no projects are found, a false response will be sent.

Input: Category provided as a query parameter, for example: /project?category=Healthcare

Output: If projects with the specified category are found, the response will be in JSON format containing an array of project details, like this:

    [   
        {     
            "id": 1,     
            "title": "My Healthcare Project",     
            "description": "A great healthcare initiative",     
            "category": "Healthcare",     
            "fundingGoal": 50000.00,     
            "currentFunding": 0.00,     
            "createdAt": "2023-07-22",     
            "updatedAt": "2023-07-22"   
        } 
    ]

If no projects with the specified category are available, a failure response will be sent:

    {   
        "success":false,   
        "message": "No projects of this category found" 
    }

By implementing this you will learn to implement API parameterization by extracting query parameters from the request URL. You will also practice retrieving and displaying specific data based on user input.

## Task 4: Navigating the Project Realm: Project Details and Feedback
In this task, you will implement a GET endpoint "/project/{project_id}" to retrieve project details along with feedback (if available) based on a given project_id. Users will provide the project_id as a path parameter. The endpoint will respond with project details and feedback (if available) in JSON format. If the specified project_id is not found in the "projects" table, a failure response will be sent.

Input: project_id provided as a path parameter, for example: /project/1

Output: If the project_id is found, the response will include project details along with feedback (if available):

    {   
        "id": 1,   
        "title": "My Healthcare Project",   
        "description": "A great healthcare initiative",   
        "category": "Healthcare",   
        "fundingGoal": 50000.00,   
        "currentFunding": 0.00,   
        "createdAt": "2023-07-22",   
        "updatedAt": "2023-07-22",   
        "feedbacks": [] 
    }

If feedback is available for the project, the response will include the feedback details as :

    {     
        "id": 1,     
        "title": "My Healthcare Project",     
        "description": "A great healthcare initiative",     
        "category": "Healthcare",     
        "fundingGoal": 50000.00,     
        "currentFunding": 0.00,     
        "createdAt": "2023-07-22",     
        "updatedAt": "2023-07-22",     
        "feedbacks": [         
            {             
                "feedbackId": 1,             
                "projectId": 1,             
                "investorId": 1,             
                "rating": 4,             
                "comment": "This project looks promising!",             
                "timestamp": "2023-07-22T11:53:25.150964"         
            }     
        ] 
    }

If the specified project_id is not found, a failure response will be sent:

    {   
        "success":false,   
        "message": "No project with project id {project_id} found" 
    }

By implementing this you will learn to handle path parameters, which allow fetching specific resources based on identifiers. You will also understand how to include related data (feedback in this case) in the response if available, or send a message indicating the absence of feedback.

## Task 5: Retrieving All Investors 
The task demonstrates the implementation of a Get endpoint "/investor" that facilitates the retrieval of information about all investors. This API endpoint is designed to return a list of Investor objects from the database.

The task has conditional statement checks whether the list of investors retrieved from the database is empty. If the list is empty, it means no investors were found, and a custom response JSON is prepared to indicate this.

The success JSON response include:

    [     
        {         
            "investorId": 1,         
            "investorName": "John Doe",         
            "email": "john.doe@example.com",         
            "totalInvestedAmount": 5000.00     
        },     
        {         
            "investorId": 2,         
            "investorName": "Jane Smith",         
            "email": "jane.smith@example.com",         
            "totalInvestedAmount": 0.00     
        },     
        {         
            "investorId": 3,         
            "investorName": "Michael Johnson",         
            "email": "michael.johnson@example.com",         
            "totalInvestedAmount": 0.00     
        },     
        {         
            "investorId": 4,         
            "investorName": "Emily Brown",         
            "email": "emily.brown@example.com",         
            "totalInvestedAmount": 0.00     
        },     
        {         
            "investorId": 9,         
            "investorName": "William Garcia",         
            "email": "william.garcia@example.com",         
            "totalInvestedAmount": 0.00     
        },     
        {         
            "investorId": 10,         
            "investorName": "Ava Martinez",         
            "email": "ava.martinez@example.com",         
            "totalInvestedAmount": 0.00     
        } 
    ]

The failure response include when no investor data found include:

    {    
        "success":false,    
        "message":"Investor  not found." 
    }

By understanding and implementing this code, you will gain valuable experience in building APIs for retrieving data from a database and handling various scenarios that may arise during API interactions.

## Task 6: Paving the Path for Prosperous Collaborations: Facilitating Investor Investments
This task focuses on enabling investors to make investments in the projects listed on the platform. You will have a static list of 10 investors which is  stored in the "investors" table.

To make an investment, investors can provide the project_id, investor_id, and the investment amount through a POST request to the endpoint "/investor/investment".

Input:

    {
        "project_id": 1,
        "investor_id": 1,
        "amount": 5000.00
    }

Validation and Response:

Upon receiving the investment request, the system will perform the following validations:

Check if the project with the specified project_id exists in the "projects" table. If not found, respond with:

    {
        "success":false,
        "message": "No projects with project id "+{projectId}+ " found"
    }

Check if the investor with the specified investor_id exists in the "investors" table. If not found, respond with:

    {
        "success":false",
        "message": "Investor with ID " + {investorId} + " not found."
    }

Check that none of the input is null:

    {
        "success":false",
        "message":"All fields must be provided."
    }

Check that the amount is not null, then it should not be negative or non zero:

    {
        "success":false",
        "message":"Investment amount must be a positive non-zero value."
    }

Verify if the funding goal for the project has already been reached. If reached, respond with:

    {
        "success":false,
        "message": "Funding goal for project ID " + {projectId} + " has already been reached."
    }

Validate if the investment amount exceeds the remaining funding goal (funding_goal-current_funding)for the project. If it exceeds, respond with:

    {
        "success":false,
        "message": "Investment amount exceeds the remaining funding goal for project ID " +{ projectId }+ "."
    }

If all validations pass, the investment will be recorded in the "investments" table with a unique investment_id, along with the project_id, investor_id, investment amount, and timestamp. Additionally, the current funding for the project in the "projects" table will be updated by adding the invested amount to the existing currentFunding value. The total_invested_amount for the investor in the "investors" table will also be updated by adding the investment amount to the existing totalInvestedAmount.

Response for Successful Investment:

    {
        "investmentId": 1
        "projectId": 1
        "investorId": 1,
        "investorName": "John Doe",
         "invetorEmail": "john.doe@example.com"
        "amountInvested": 5000.0,
        "timestamp": "2023-07-22T14:49:53.8355342"
    }

This task involves handling input validation, updating the "investments," "projects," and "investors" tables in the database, and providing a successful investment response. It also demonstrates the importance of maintaining data consistency and updating relevant tables upon successful investment.

## Task 7: Illuminating the Path of Collaboration: Revealing Investor Contributions in Project
This task involves creating an endpoint to retrieve detailed project information along with the investors who have contributed to the project. The API endpoint, GET "/project/{project_id}/investments", will display a list of investors and their respective investment amounts for the specified project.

Get Project Investments (GET /project/{project_id}/investments): This endpoint allows users to view the project details along with the investors who have made contributions to the project specified by {project_id}. Upon successful validation of the project_id, the API will respond with the project's current funding, funding goal, a list of investors with their respective details, and the timestamp of the response.

If the project has investors, the API will return the following response:

    {     
        "projectId": 1,     
        "currentFunding": 5000.00,     
        "fundingGoal": 50000.00,     
        "investors": [         
            {             
                "investorId": 1,             
                "investorName": "John Doe",             
                "email": "john.doe@example.com",             
                "amount": 5000.00         
            }     
        ],     
        "timestamp": "2023-07-22T14:36:37.1496922" 
    }

If no investors have contributed to the project, the API will return the following response:

    {     
        "projectId": 1     
        "currentFunding": 0.00,     
        "fundingGoal": 50000.00,     
        "investors": [],     
        "timestamp": "2023-07-22T14:35:59.0591816" 
    }

This task involves implementing robust validation to ensure that the provided project_id exists in the "projects" table. Additionally, the API will display appropriate responses based on the presence or absence of investors for the specified project. This task will enable us to understand how to manage and display investment details for specific projects, enhancing the overall functionality of the Crowd Funding Platform.

## Task 8: Illuminating Investor's Path: Personalized Investment Dashboard	
This task involves creating a GET endpoint "/investor/dashboard"  that allows investors to access their personalized dashboard. Upon successful validation of the investorId, the endpoint retrieves and displays all investment details made by the particular investor.

Endpoint: GET /investor/dashboard?investorId={investorId}

Validation and Response: The system validates the provided investorId to ensure its existence in the "investors" table. If the investorId is valid, the response will include the investor's information, total invested amount, and a list of project investments made by the investor.

Output:

    {     
        "investorId": 1,     
        "investorName": "John Doe",     
        "email": "john.doe@example.com",     
        "totalInvestedAmount": 5000,     
        "projectInvestments": [         
            {             
                "projectId": 1,             
                "title": "My Healthcare Project",             
                "category": "Healthcare",             
                "fundingGoal": 50000.00,             
                "investedAmount": 5000.00         
            }     
        ] 
    }

This task enables investors to view their investment portfolio, including project details such as title, category, funding goal, and the amount invested in each project. This feature enhances the user experience and provides investors with valuable insights into their contributions to various projects.

## Task 9: Fostering Investor Voices: Crafting Feedback and Ratings for Project
This task  involves creating an endpoint "/investor/{project_id}/feedback" that allows investors to provide feedback and rate specific projects. The endpoint accepts input data, including the investorId, rating, and comment for the project. The system performs validation checks to ensure the project and investor exist, and that the rating and comment meet specific criteria.

Endpoint: POST /investor/{project_id}/feedback

Input:(for "project_id"=1)

    {     
        "investorId": 1,     
        "rating": 4,     
        "comment": "This project looks promising!" 
    }

Validation and Response: The system performs validation checks to ensure the project with the specified projectId exists and that the investorId is valid. It also validates the rating and comment fields for correctness. If any validation fails, the appropriate error response will be returned, indicating the reason for failure.

Validations:

"Project with ID " + {projectId} + " not found." "Investor with ID " +{ investorId} + " not found." "Invalid rating. Rating must be between 1 and 5." "Comment cannot be null or empty."

Upon successful validation, the system stores the feedback data in the "feedbacks" table, including the feedbackId, projectId, investorId, rating, comment, and timestamp. The response will contain the feedback details.

Output:

    {     
        "feedbackId": 1,     
        "projectId": 1,     
        "investorId": 1,     
        "rating": 4,     
        "comment": "This project looks promising!",     
        "timestamp": "2023-07-22T15:08:14.0887563" 
    }

This task allows investors to provide valuable feedback and rate projects, contributing to the overall reputation and credibility of the platform. The validation checks ensure the accuracy and integrity of the feedback data provided by investors.

DB Details : 