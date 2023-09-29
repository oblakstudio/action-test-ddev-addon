# Test your custom DDEV addon

![GitHub release (with filter)](https://img.shields.io/github/v/release/oblakstudio/action-test-ddev-addon)
![project is maintained](https://img.shields.io/maintenance/yes/2024.svg)

This action tests your custom DDEV addon using Bash Automated Testing System. It provides a simple and reliable way to verify that your custom-made DDEV addon works. It provides options to test both the current version of the addon and the release version, so you can use it in scheduled workflows to test your addon against DDEV on a regular basis.

## Usage

See [action.yml](action.yml)

```yaml
- name: Test DDEV addon
  uses: oblakstudio/action-test-ddev-addon@v1
  with:
    # Allows ddev get to use a github token to prevent rate limiting by tests
    # In almost any forseeable case you can use ${{secrets.GITHUB_TOKEN}} here
    github_token: ${{ secrets.GITHUB_TOKEN }}
    # Debug the test suite by opening a tmate session
    debug_enabled: false
    # DDEV version to test against
    # Can be "edge", "HEAD" or "stable"
    # Defaults to "stable"
    ddev_version: stable
    # Test type to run.
    # We recommend tagging your bats tests with "local" and "release"
    # Local tests will get the version of the addon in the branch / commit you are testing
    # Release tests will get the version of the addon from the github using latest release
    # If you don't tag your tests, you can use an empty string
    test_type: local
```
### Basic:

```yaml
steps:
  - uses: action/checkout@v4
  - name: Test DDEV addon
    uses: oblakstudio/action-test-ddev-addon@v1
```

### With test tag

```yaml
steps:
  - uses: action/checkout@v4
  - name: Test DDEV addon
    uses: oblakstudio/action-test-ddev-addon@v1
    with:
      test_type: local
```





