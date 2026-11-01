---
name: python-coding
description: Use whenever writing or editing Python code (scripts, modules, tests, notebooks-to-script conversions), before producing any Python.
---

# Python coding

Modern Python 3.11+: type-safe, async where I/O-bound, production-ready.

## Core workflow

1. **Analyze codebase**: review structure, dependencies, type coverage, tests. Match existing style and project config first.
2. **Design interfaces**: define protocols, dataclasses, type aliases.
3. **Implement**: Pythonic code with full type hints and error handling.
4. **Test**: pytest suite with fixtures; aim for >90% coverage on packages and modules.
5. **Validate**: run the project's tests and linters (`mypy --strict`, `black`, `ruff`) if configured.
   - mypy fails: fix the type errors and re-run.
   - Tests fail: debug, fix, and iterate until green.
   - ruff/black reports issues: apply auto-fixes, then re-validate.

Scale to the task. For a one-off script, skip the full test suite and strict typing ceremony, but still run it to confirm it works.

Ask before installing any new dependency or tool (including mypy, black, ruff, httpx, Poetry).

## References

Load only when the topic applies:

| Topic | Reference | Load When |
|-------|-----------|-----------|
| Examples | `references/examples.md` | Need a pattern for config reading, dataclasses, async, pytest, or mypy config |
| Type System | `references/type-system.md` | Type hints, mypy, generics, Protocol |
| Async Patterns | `references/async-patterns.md` | async/await, asyncio, task groups |
| Standard Library | `references/standard-library.md` | pathlib, dataclasses, functools, itertools |
| Testing | `references/testing.md` | pytest, fixtures, mocking, parametrize |

## Constraints

### MUST DO
- Type hints for all function signatures and class attributes
- PEP 8 compliance with black formatting
- Docstrings (Google style) on public APIs
- `X | None` instead of `Optional[X]`
- Async/await for I/O-bound operations
- Dataclasses over manual `__init__`
- Context managers for resource handling
- Parameterized queries for any SQL
- Catch specific exception types
- Read secrets and config from environment variables
- Keep functions under 70 lines

### MUST NOT DO
- Use mutable default arguments
- Mix sync and async code improperly
- Ignore mypy errors in strict mode

## Output

When implementing a feature, provide:
1. Module file with complete type hints
2. Test file with pytest fixtures
3. Confirmation that the checks you ran passed (mypy, tests, linter), or what failed
4. Brief explanation of the Pythonic patterns used
