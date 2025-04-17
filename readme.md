# Assignment 10 – FastAPI QA Testing & Bug Fixes

## 🔧 Setup Instructions

1. **Clone the repository**
   ```bash
   git clone https://github.com/srushti0510/Assignment10.git
   cd Assignment10
   ```

2. **Create a virtual environment**
   ```bash
   python3 -m venv venv
   source venv/bin/activate
   ```

3. **Install required packages**
   ```bash
   pip install -r requirements.txt
   ```

4. **Start services using Docker Compose**
   ```bash
   docker compose up --build
   ```

5. **Run tests with coverage**
   ```bash
   docker compose exec fastapi pytest --cov=app --cov-report=term-missing
   ```

## Closed Issues (Bug Fixes)

Here are the 6 issues I identified, fixed, tested, and merged:

1. **Bug #1:** [Swagger example mismatch](https://github.com/srushti0510/Assignment10/issues/1)  
   *Fixed mismatches in login and registration example schemas.*

2. **Bug #2:** [Missing `nickname` field and weak password regex](https://github.com/srushti0510/Assignment10/issues/2)  
   *Added `nickname` and improved password validation logic.*

3. **Bug #3:** [Missing test fixture for invalid email](https://github.com/srushti0510/Assignment10/issues/3)  
   *Added `invalid_email_user_data` fixture for test coverage.*

4. **Bug #4:** [Duplicate `role` values in UserListResponse](https://github.com/srushti0510/Assignment10/issues/4)  
   *Removed duplicates and corrected sample user role values.*

5. **Bug #5:** [Missing fields in test fixtures vs schema](https://github.com/srushti0510/Assignment10/issues/5)  
   *Ensured test fixture data includes `nickname`, `first_name`, `last_name`, etc.*

6. **Bug #6:** [Email service tests and SMTP mocking](https://github.com/srushti0510/Assignment10/issues/6)  
   *Wrote tests for `send_user_email`, mocked SMTP errors, validated HTML content, and handled template rendering errors.*

## Docker Image

You can find the deployed Docker image here:  
 **[DockerHub - srushti5/assignment10](https://hub.docker.com/r/srushti5/wis_club_api)**

To pull the image:
```bash
docker pull srushti5/assignment10
```

## Test Coverage Report

To check test coverage, run:

```bash
docker compose exec fastapi pytest --cov=app --cov-report=term-missing
```
As of the final commit, test coverage is: 88%


## Reflection

Working on this QA-focused FastAPI assignment gave me a deeper understanding of backend validation, test-driven development, and collaborative workflows. I gained hands-on experience in identifying real-world bugs such as mismatched Swagger examples, missing schema fields, weak validation regexes, and test fixture inconsistencies. Implementing a secure password policy and improving schema-to-fixture consistency taught me the importance of maintaining a tightly aligned contract between the API layer and test layer.

One of the main challenges I faced was dealing with the email service and SMTP mocking. I encountered errors when rendering templates and testing mail delivery without a real SMTP server. To resolve this, I created DummySMTPClient and used monkeypatching and exception assertions to simulate and validate edge cases. Another challenge was increasing the test coverage to 88% — I had to systematically identify missing branches and untested conditions and write focused test cases to handle them. Debugging these with async functions and fixtures was a learning curve, but it deepened my understanding of asynchronous testing in Python.

Overall, this assignment not only strengthened my FastAPI and Pytest skills but also reinforced the importance of code coverage, documentation, and GitHub collaboration. I now feel more confident in contributing to production-quality backend systems with robust test suites and CI/CD pipelines.