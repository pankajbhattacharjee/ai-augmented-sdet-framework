# ✈️ AI-Augmented SDET Framework – Airline Automation Testing

An AI-assisted end-to-end test automation framework for airline Passenger Service Systems (PSS), built using **Python, Selenium WebDriver, Pytest, Flask, and GitHub Actions**.

The project simulates real-world airline booking workflows and combines traditional test automation with AI-assisted test generation, failure analysis, and automated test coverage-gap detection.

It is designed to demonstrate modern Software Development Engineer in Test (SDET) practices, intelligent test automation, and continuous integration.

---

## 🚀 Project Overview

Airline Passenger Service Systems (PSS) handle critical operations such as flight reservations, passenger information, ticket booking, and check-in.

Testing these systems manually can be time-consuming and error-prone.

This project addresses that challenge by providing an automated testing framework that:

* Automates end-to-end airline booking workflows.
* Uses Selenium WebDriver with Python for browser automation.
* Implements the Page Object Model (POM) design pattern.
* Uses Pytest for structured test execution.
* Generates executable test scenarios from natural-language requirements using AI-assisted logic.
* Analyzes test failures and identifies potential coverage gaps.
* Integrates automated testing into GitHub Actions CI/CD pipelines.

### Key Highlights

| Metric                | Result             |
| --------------------- | ------------------ |
| Total Automated Tests | 64                 |
| Passing Tests         | 64                 |
| Failed Tests          | 0                  |
| Test Execution Time   | 99.7 seconds       |
| Browser               | Chrome 156         |
| Execution Mode        | Headless           |
| Test Framework        | Pytest             |
| Automation Tool       | Selenium WebDriver |

**Test results:** 64/64 tests passed in the verified execution.

---

## 🛠️ Technology Stack

| Technology              | Purpose                                   |
| ----------------------- | ----------------------------------------- |
| Python                  | Core programming language                 |
| Selenium WebDriver      | Browser automation                        |
| Pytest                  | Test execution and assertions             |
| Flask                   | Self-contained demo airline application   |
| HTML / CSS / JavaScript | Demo application interface                |
| AI / LLM                | Test generation and failure analysis      |
| AST Parsing             | Validation-rule and coverage-gap analysis |
| Git & GitHub            | Version control                           |
| GitHub Actions          | CI/CD automation                          |
| HTML Reports            | Test execution reporting                  |

---

## 🏗️ Project Architecture

```text
ai-augmented-sdet-framework/
│
├── app/
│   └── server.py
│
├── pages/
│   ├── base_page.py
│   ├── login_page.py
│   ├── search_page.py
│   ├── results_page.py
│   ├── passenger_page.py
│   └── confirmation_page.py
│
├── tests/
│   ├── test_login.py
│   ├── test_flight_search.py
│   ├── test_passenger_details.py
│   ├── test_booking.py
│   └── generated/
│
├── ai/
│   ├── generate_tests.py
│   ├── analyze_failures.py
│   └── prompts/
│
├── reports/
│   ├── report.html
│   ├── ai_analysis.md
│   └── ai_analysis_example_failure.md
│
├── conftest.py
├── pytest.ini
├── Makefile
├── requirements.txt
└── README.md
```

*Note: The directory structure above represents the main logical components. Actual filenames and subdirectories should match the repository.*

---

## ✨ Key Features

### 1. End-to-End Airline Booking Automation

Automates a complete airline booking journey using Selenium.

The demo application supports:

* Airline homepage navigation.
* Flight search.
* Flight selection.
* Passenger information entry.
* Booking confirmation.
* User login.

The application is self-contained and deterministic, allowing tests to run without depending on external airline websites.

### 2. Selenium Automation with Page Object Model

Implements the Page Object Model (POM) to separate application page interactions from test logic.

Key implementation practices:

* Reusable page objects.
* Centralized element locators.
* Explicit waits.
* Reusable browser interaction methods.
* Maintainable test components.
* No hardcoded `time.sleep()` synchronization.

### 3. AI-Assisted Test Case Generation

The `ai/generate_tests.py` module converts natural-language requirements into executable test scenarios.

Example requirement:

```text
A passenger should not be able to
search for a flight without selecting
a destination.
```

Expected generated scenario:

```text
Test Scenario:
Verify destination validation.

Steps:
1. Open the airline application.
2. Enter the departure city.
3. Leave the destination empty.
4. Submit the flight search form.

Expected Result:
The application should display
a destination validation message.
```

The generator also provides an optional LLM integration path.

### 4. AI-Powered Failure Analysis

The `ai/analyze_failures.py` module analyzes test failures and produces structured reports.

Capabilities include:

* Failure categorization.
* Root cause investigation.
* Timing-related failure analysis.
* Validation regression detection.
* Behavioural regression identification.
* Automated coverage-gap detection.

The analysis uses AST parsing to inspect application validation rules and compare them with test assertions.

### 5. Automated Coverage-Gap Detection

The framework identifies validation rules that are not covered by automated test assertions.

Verified analysis:

* 23 application validation rules identified.
* 19 validation rules asserted.
* 4 defensive branches identified as unreachable through the UI.

Rather than incorrectly treating unreachable branches as successfully tested, the framework reports them separately.

### 6. Automated Failure Evidence Collection

When a test fails, the framework captures:

* Browser screenshot.
* Rendered DOM.
* Current page URL.

This helps developers and QA engineers investigate failures without manually reproducing every issue.

### 7. CI/CD Integration

GitHub Actions automates the testing workflow.

The pipeline includes:

1. Smoke testing.
2. Regression testing.
3. AI failure analysis.
4. Test report generation.
5. Artifact collection.
6. Generated scenario consistency checks.

The pipeline also detects changes that cause generated test scenarios to drift from their original requirements.

---

## 🧪 Test Coverage

The framework contains 64 automated tests:

* 49 hand-written tests.
* 15 generated tests.

Tests are organized using `tcNN` markers mapped to the following test categories.

| Test Case | Testing Area             |
| --------- | ------------------------ |
| TC01      | Application Navigation   |
| TC02      | Flight Search            |
| TC03      | Flight Selection         |
| TC04      | Passenger Information    |
| TC05      | Form Validation          |
| TC06      | Booking Workflow         |
| TC07      | Booking Confirmation     |
| TC08      | Login and Authentication |

The framework covers positive scenarios, negative scenarios, validation checks, and regression scenarios.

---

## ⚙️ Installation and Setup

### Prerequisites

Make sure you have:

* Python 3.10 or later.
* Google Chrome.
* Git.
* pip package manager.

### 1. Clone the Repository

```bash
git clone https://github.com/pankajbhattacharjee/ai-augmented-sdet-framework.git
```

### 2. Navigate to the Project

```bash
cd ai-augmented-sdet-framework
```

### 3. Create a Virtual Environment

Windows:

```powershell
python -m venv venv
```

Activate it:

```powershell
.\venv\Scripts\Activate.ps1
```

### 4. Install Dependencies

```bash
pip install -r requirements.txt
```

### 5. Run Automated Tests

```bash
pytest -v
```

For detailed output:

```bash
pytest -v -s
```

The framework automatically starts the demo application and manages the Chrome browser through its test fixtures.

### 6. Run Against a Different Application

The framework supports configuring a different application URL through its `--base-url` option.

```bash
pytest --base-url=http://localhost:5000 -v
```

---

## 📊 Test Reports

The framework generates test execution reports and AI analysis outputs.

| Report                           | Description                   |
| -------------------------------- | ----------------------------- |
| `report.html`                    | HTML test execution report    |
| `ai_analysis.md`                 | AI-assisted test analysis     |
| `ai_analysis_example_failure.md` | Example failure investigation |

The failure analysis example includes three deliberately broken tests demonstrating:

* Locator and timing-related failures.
* Validation regression.
* Behavioural regression.

---

## 🔍 Engineering Challenges & Solutions

During development, several issues were identified and resolved.

**1. Zero-Size Validation Elements**

Some empty HTML error `<span>` elements had zero dimensions, making visibility-based Selenium waits unreliable.

Solution: Improved element detection and synchronization strategies.

**2. Stale Pre-Submit DOM Reads**

Reading page content immediately after submitting a form could capture the previous DOM state.

Solution: Improved synchronization to wait for the expected post-submit state.

**3. Premature Navigation Completion**

The form submission method returned before the application redirect completed.

Solution: Added appropriate navigation synchronization.

These improvements helped eliminate flaky test behaviour and improve framework reliability.

---

## 🎯 Learning Outcomes

This project demonstrates practical experience with:

* Selenium WebDriver automation.
* Python-based test framework development.
* Pytest fixtures, markers, and assertions.
* Page Object Model architecture.
* Explicit waits and synchronization.
* Functional and regression testing.
* AI-assisted test generation.
* Automated failure analysis.
* AST-based validation coverage analysis.
* GitHub Actions CI/CD.
* Test reporting and debugging.

---

## 🔮 Future Improvements

Potential enhancements include:

* Multi-passenger booking scenarios.
* Round-trip flight booking automation.
* API testing integration.
* Cross-browser testing.
* Real LLM API integration for intelligent test generation.
* Advanced test analytics and dashboards.
* Parallel test execution.

---

## 👨‍💻 Author

**Pankaj Bhattacharjee**

B.Tech Computer Science & Engineering Student

* GitHub: https://github.com/pankajbhattacharjee
* LinkedIn: https://www.linkedin.com/in/pankaj-bhattacharjee-475b86325/

---

## ⭐ Support

If you find this project useful, consider giving the repository a star!

---

**Built to explore intelligent test automation and modern SDET engineering practices.**
