# myctl-templates

Service templates for [myctl](https://github.com/oladayo21/myctl) server management CLI.

## Available Templates

| Template | Description | Port |
|----------|-------------|------|
| postgres | PostgreSQL 16 database | 5432 |
| redis | Redis 7 cache | 6379 |
| whoami | HTTP request/response testing | 80 |

## Usage

```bash
# List available templates
myctl template list

# Show template details
myctl template show postgres

# Deploy a service
myctl deploy --template=postgres --name=mydb --server=prod
```

## Template Structure

Each template contains:

```
<template>/
  template.yaml   # Service metadata, port, env vars
  compose.yaml    # Docker Compose configuration
```

### template.yaml

```yaml
name: postgres
description: PostgreSQL 16 database
port: 5432
env:
  - name: POSTGRES_USER
    default: postgres
  - name: POSTGRES_PASSWORD
    generate: true
    required: true
  - name: POSTGRES_DB
    default: postgres
```

### compose.yaml

Standard Docker Compose file with health checks.

## Adding Templates

1. Create directory: `<name>/`
2. Add `template.yaml` with metadata
3. Add `compose.yaml` with Docker config
4. Submit PR

## License

MIT
