# Sakai Automated QA

For now, I recommend using Electron, the built-in Chromium based browser.

## Installation

Clone this repository:

`git clone https://github.com/psev/sakai-cypress-test`

Move into the cloned repository:

`cd sakai-cypress-test`

Then, install dependencies:

`npm install`

## Running

To open Cypress:

`CYPRESS_BASE_URL='http://qa20-mysql.nightly.sakaiproject.org' npm run cypress:open`

You can specify the `admin` username and password with the
`CYPRESS_ADMIN_USERNAME` and `CYPRESS_ADMIN_PASSWORD` environment variables.

## Testing

### Basic Example

```gherkin
Feature: This is an example feature

  @site
  Scenario: This is an example scenario
    Given I am the instructor
    Then go to the site
    Then add the "announcements" tool
    # Add other steps here.
    Then logout
```

### Tags

#### General

- `@admin`
  - Login as _admin_.
- `@site`
  - Create a temporary site and its users.

#### Versions

- `@sakai-20`
  - Uses `https://qa20-mysql.nightly.sakaiproject.org`.

### Instructions

- __@site__ instructions:
  - `Given` I am the instructor
  - `Given` I am the student
  - `Then` go to the site
- `Given` I am "\<username\>"
- `Then` create user "\<username\>" "\<type:optional\>"
  - __type__ can be one of:
    - registered (_default_)
    - maintain
- `Then` create site "\<sitename\>"
- `Then` add user "\<username\>" to site "\<sitename\>" "\<type:optional\>"
  - __type__ can be one of:
    - access (_default_)
    - maintain
- `Then` add the "\<toolname\>" tool
- `Then` go to site "\<sitename\>"
- `Then` delete site "\<sitename\>"
- `Then` remove user "\<username\>"
- `Then` logout
