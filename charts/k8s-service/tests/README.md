# Chart Validation Tests

This directory contains test value files for validating chart behavior.

## Test Files

### Negative Tests (Should Fail)

- `duplicate-mountpath.yaml` - Tests that duplicate `mountPath` values are detected and rejected
- `duplicate-hostpath.yaml` - Tests that duplicate host `path` values are detected and rejected

### Positive Tests (Should Pass)

- `valid-hostpaths.yaml` - Tests that valid unique hostPaths configuration works correctly

## Running Tests Locally

### Test that duplicates are rejected:
```bash
# Should fail with error about duplicate mountPath
helm template test charts/k8s-service -f charts/k8s-service/tests/duplicate-mountpath.yaml

# Should fail with error about duplicate host path
helm template test charts/k8s-service -f charts/k8s-service/tests/duplicate-hostpath.yaml
```

### Test that valid config works:
```bash
# Should succeed
helm template test charts/k8s-service -f charts/k8s-service/tests/valid-hostpaths.yaml
```

## CI/CD Integration

These tests are automatically run in GitHub Actions workflows to ensure validation logic works correctly.
