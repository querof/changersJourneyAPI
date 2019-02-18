# changersJourneyAPI

Hi Changers!

First thanks in advance for the opportunity.

Here you can find:

- Index.html: File thats show API documentation.
- journey.yml: File that contains source in Open Api 3.0.0. Compatible with _Apiary._ by the way.

## End points

| Name   | Method      | URL                   | Protected  |        Params        |
| ---    | ---         | ---                   | ---        | ---                  |
| List   | `GET`       | `/journey/mobility`   | ✓          | expect  user email and token in the header|
| Add   | `POST`       | `/journey`            | ✓          | expect  user email and token in the header also journey fields|



## Auth:

All the end points use token implementation for auth. The end point make the assumption that an different component return the token.

## Tools:

The doc and source yaml file was build with Swagger(Open Api 3.0.0).

## Pseudo code:

### JourneyController.php

Controller of basic CRUD actions.
#### AddAction:

Action that allow to add a new Journey linked to an User.

##### Logic:

- Validate Token. If the token is invalid return exception.
- Apply validation to values. If the data is invalid return exception.
- create Journey object and add values to properties.
- save object.
- Return success message.

### JourneyReportController.php

Controller of complex/report actions.

#### mobilitySummaryAction:

Action that allow to return mobility summary group by journeyType property.

##### Logic:

- Validate Token. If the token is invalid return exception.
- make summarizing operation (using sql or ORM tool).
- Return server json response.


## Global or common errors:

It is recommended to use a listener class to catch the exceptions of the API; to control it and show appropriate messages to the client.
