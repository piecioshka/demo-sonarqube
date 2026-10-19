# Contributing to demo-sonarqube

How to run the tests and the SonarQube analysis. For what the demo shows, see the [README](README.md).

## Getting started

Prerequisites: Node.js version from `.nvmrc` (`lts/krypton`).

```bash
git clone https://github.com/piecioshka/demo-sonarqube
cd demo-sonarqube
npm install
```

## Scripts

| Script                  | What it does                           |
| ----------------------- | -------------------------------------- |
| `npm test`              | Runs the Jest test suite               |
| `npm run test:coverage` | Runs Jest and writes a coverage report |

## Project structure

```
src/
  auth.js         - authentication module (SQL injection, command injection examples)
  calculator.js   - math utilities (eval usage, code smells examples)
tests/
  auth.test.js
  calculator.test.js
```

The code in `src/` contains intentional issues listed in the README. Keep them in place - they are what SonarQube is supposed to find.

## SonarQube analysis

- `sonar-project.properties` sets the project key (`demo-sonarqube`), sources (`src`) and tests (`tests`).
- `.github/workflows/sonarqube.yml` runs `SonarSource/sonarqube-scan-action` on every push to `main` and on pull requests.
- The workflow needs the `SONAR_TOKEN` secret and the `SONAR_HOST_URL` repository variable.
- The SonarQube host is self-hosted and not always reachable, so the scan step has `continue-on-error: true` and does not turn CI red.

The [video linked in the README](https://www.youtube.com/watch?v=y4L8_Ie8oj8) walks through setting up SonarQube for this project.

## Conventions

Commit messages are short and imperative; recent ones use Conventional Commits prefixes (`ci:`, `chore:`).
