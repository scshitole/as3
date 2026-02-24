# Application Services AS3 101

This repository is a compact, beginner-friendly set of examples for **F5 Application Services 3 (AS3)** declarations.

## What this repo contains

- `example-http.json`  
  A single-application AS3 declaration with one `Service_HTTP` virtual service and one backend pool.
- `example-http-multipleapps.json`  
  A multi-application declaration in the same tenant (`A1` and `A2`) to show how to model multiple apps in one payload.
- `how_to_post_using_curl`  
  Quick `curl` commands for posting, retrieving, and deleting declarations through the AS3 REST API.

## General structure to understand first

Both JSON examples follow the same AS3 hierarchy:

1. **Top-level AS3 control block** (`class: AS3`, `action: deploy`, `persist: true`)
2. **`declaration` object** with `class: ADC` and `schemaVersion`
3. **Tenant** (for example, `Sample_01`) with `class: Tenant`
4. **Application** objects (`class: Application`)
5. **Service + support objects** such as:
   - `Service_HTTP` (virtual address + virtual port)
   - `Pool` (members + monitor)

If you are new to BIG-IP/AS3, focus first on how a `Service_HTTP` references a `Pool` and how pool members map to backend endpoints.

## Important things to know while using these examples

- These files are intended as **learning templates**, not production-ready declarations.
- You can apply declarations to BIG-IP at:
  - `POST /mgmt/shared/appsvcs/declare`
- You can inspect declarations with:
  - `GET /mgmt/shared/appsvcs/declare`
- You can remove declarations with:
  - `DELETE /mgmt/shared/appsvcs/declare`

The `how_to_post_using_curl` file includes concrete command examples for each workflow.

## Good next topics to learn

- Add HTTPS (`Service_HTTPS`) and TLS certificates/profiles.
- Use advanced pool behavior (load-balancing modes, persistence, health monitors).
- Organize multi-tenant declarations and shared objects.
- Integrate declaration deployment into CI/CD pipelines.
- Validate declarations against AS3 schema documentation before deployment.
