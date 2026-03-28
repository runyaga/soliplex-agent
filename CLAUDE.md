# soliplex-agent

Pure Dart agent orchestration monorepo for Soliplex AI runtime.

## Quick Reference

```bash
dart pub get                          # Install dependencies (workspace)
dart format .                         # Format code
dart analyze --fatal-infos            # Analyze (must be 0 issues)
dart test                             # Run tests
```

## Package Structure

```text
packages/
  soliplex_agent/          # Core: session, runtime, orchestration
  soliplex_client/         # Pure Dart: REST API, AG-UI, domain models
  soliplex_client_native/  # Platform HTTP adapters (Cupertino)
  soliplex_logging/        # Pure Dart: logging, DiskQueue, BackendLogSink
```

## Architecture

Three layers: Agent (orchestration) -> Client (API, models) -> Logging.
`soliplex_client_native` provides platform-specific HTTP adapters.

All packages are pure Dart except `soliplex_client_native` (Flutter).

## Development Rules

- KISS, YAGNI, SOLID — simple solutions over clever ones
- Match surrounding code style exactly
- Never use `// ignore:` directives — restructure code instead
- Keep `soliplex_agent`, `soliplex_client`, and `soliplex_logging` pure Dart
- Platform-specific code goes in `soliplex_client_native`

## Code Quality

After any code modification, run in order:

1. `dart format .` (must produce no changes)
2. `dart analyze --fatal-infos` (must be 0 issues)
3. `dart test` (must pass)

## Testing

- Use `mocktail` for mocking (not mockito)
- Mirror lib/ structure in test/
