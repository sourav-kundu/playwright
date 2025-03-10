---
id: test-cli
title: "Command line"
---

<!-- TOC -->

## Examples

Here are the most common options available in the command line.

- Run all the tests
  ```bash
  npx playwright test
  ```

- Run a single test file
  ```bash
  npx playwright test tests/todo-page.spec.ts
  ```

- Run a set of test files
  ```bash
  npx playwright test tests/todo-page/ tests/landing-page/
  ```

- Run files that have `my-spec` or `my-spec-2` in the file name
  ```bash
  npx playwright test my-spec my-spec-2
  ```

- Run the test with the title
  ```bash
  npx playwright test -g "add a todo item"
  ```

- Run tests in headed browsers
  ```bash
  npx playwright test --headed
  ```

- Run tests in a particular browser (config-less mode)
  ```bash
  npx playwright test --browser=webkit
  ```

- Run tests in all browsers (config-less mode)
  ```bash
  npx playwright test --browser=all
  ```

- Disable [parallelization](./test-parallel.md)
  ```bash
  npx playwright test --workers=1
  ```

- Choose a [reporter](./test-reporters.md)
  ```bash
  npx playwright test --reporter=dot
  ```

- Run in debug mode with [Playwright Inspector](./inspector.md)
  ```bash
  # Linux/macOS
  PWDEBUG=1 npx playwright test

  # Windows with cmd.exe
  set PWDEBUG=1
  npx playwright test

  # Windows with PowerShell
  $env:PWDEBUG=1
  npx playwright test
  ```

- Ask for help
  ```bash
  npx playwright test --help
  ```

## Reference

Complete set of Playwright Test options is available in the [configuration file](./test-advanced.md). Following options can be passed to a command line and take a priority over the configuration file:

- `--headed`: Run tests in headed browsers. Useful for debugging.

- `--browser`: Run test in a specific browser. Available options are  `"chromium"`, `"firefox"`, `"webkit"` or `"all"` to run tests in all three browsers at the same time.

- `-c <file>` or `--config <file>`: Configuration file. If not passed, defaults to `playwright.config.ts` or `playwright.config.js` in the current directory.

- `-c <dir>` or `--config <dir>`: Directory with the tests to run without configuration file.

- `--forbid-only`: Whether to disallow `test.only`. Useful on CI.

- `-g <grep>` or `--grep <grep>`: Only run tests matching this regular expression. For example, this will run `'should add to cart'` when passed `-g="add to cart"`.

- `--grep-invert <grep>`: Only run tests **not** matching this regular expression. The opposite of `--grep`.

- `--global-timeout <number>`: Total timeout for the whole test run in milliseconds. By default, there is no global timeout.

- `--list`: List all the tests, but do not run them.

- `--max-failures <N>` or `-x`: Stop after the first `N` test failures. Passing `-x` stops after the first failure.

- `--output <dir>`: Directory for artifacts produced by tests, defaults to `test-results`.

- `--project <name>`: Only run tests from one of the specified [projects](./test-advanced.md#projects). Defaults to running all projects defined in the configuration file.

- `--quiet`: Whether to suppress stdout and stderr from the tests.

- `--repeat-each <N>`: Run each test `N` times, defaults to one.

- `--reporter <reporter>`: Choose a reporter: minimalist `dot`, concise `line` or detailed `list`. See [reporters](./test-reporters.md) for more information.

- `--retries <number>`: The maximum number of [retries](./test-retries.md) for flaky tests, defaults to zero (no retries).

- `--shard <shard>`: [Shard](./test-parallel.md#shard-tests-between-multiple-machines) tests and execute only selected shard, specified in the form `current/all`, 1-based, for example `3/5`.

- `--timeout <number>`: Maximum timeout in milliseconds for each test, defaults to 30 seconds.

- `--update-snapshots` or `-u`: Whether to update [snapshots](./test-snapshots.md) with actual results instead of comparing them. Use this when snapshot expectations have changed.

- `--workers <number>` or `-j <number>`: The maximum number of concurrent worker processes that run in [parallel](./test-parallel.md).
