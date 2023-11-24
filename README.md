# Project Overview

The task is to build a currency exchange rate API that will save a set of currency rate amounts with the EUR base currency into a MySQL Database and includes redis cache not to trigger third party api nor the database all the time a request is triggered. The following requirements must be met:

## Requirements

- Build a Symfony 5 project with the following dependencies:

  - Doctrine (with migrations)
  - Redis
  - GuzzleHTTP (for making HTTP requests)

- Create a console command that will fetch the currency exchange rates for a given set of currencies from the Open Exchange Rates API.

  - There are other alternatives, similar to Open Exchange Rates that can be used such as:
    - Frankfurter: Frankfurter provides exchange rates for 179 currencies and precious metals. They offer a free plan that allows up to 1,000 requests per month. You can find more details at: <https://www.frankfurter.app/> - <https://api.frankfurter.app/latest?from=USD>
    - ExchangeRate-API: ExchangeRate-API provides real-time and historical exchange rates for currencies. It offers a free plan that includes 1,500 requests per month. You can access the API at: <https://www.exchangerate-api.com>
    - CurrencyFreaks: CurrencyFreaks offers exchange rate data for more than 150 currencies. They have a free plan that allows up to 1,000 requests per month. You can find more information at: <https://currencyfreaks.com/>
  - The command should have the following signature:

  ```
  `php bin/console app:currency:rates [base_currency] [target_currency_1] [target_currency_2] ... [target_currency_n]`
  ```

  The command should make an HTTP request to the API to fetch the exchange rates for the given currencies, save the rates into a MySQL Database with the EUR base currency and store the rates in Redis. This must be set as a cron job to be triggered daily at 1am.

- Create an endpoint that will return the exchange rates for a given set of currencies. The endpoint should have the following signature:

  ```
  `GET /api/exchange-rates?base_currency=[base_currency]&target_currencies=[target_currency_1,target_currency_2,...,target_currency_n]`
  ```

  The endpoint should first check Redis for the requested rates. If the rates are not in Redis, it should fetch them from the MySQL Database, store them in Redis and return the rates. If the rates are in Redis, it should return the rates directly from Redis.

- Write unit tests to verify the functionality of the console command and the endpoint.
- Use doctrine migrations to manage database schema changes.
- Push your changes to a GitHub account by creating a timeline of git commits.

## Evaluation Criteria

- Code quality and organization
- Correct use of Symfony components and best practices
- Correct implementation of the API requirements
- Unit tests that verify the functionality of the console command and the endpoint
- Effective use of git and GitHub

## Submission

Please create a public GitHub repository and send the link to your repository once you have completed the project to <development@united-remote.com>.
