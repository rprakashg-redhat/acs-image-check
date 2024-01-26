# acs-image-check
Check images for build time policy violations, and report them.

# Usage
```yaml
- uses: rprakashg-redhat/acs-image-check@main
  with:
    # Central endpoint
    central: ""

    # ROX Api token
    api-token: ""

    # Container Image to check for build time policy violations
    image: ""

    # output format valid values (table|csv|json|sarif)
    output: ""

    # directory to create output from image check should be created
    output-path: ""
```

## Example 
```yaml
name: example
on:
  workflow_dispatch:
jobs:
  analyze:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: rprakashg-redhat/setup-roxctl@main
      - name: run image check
        uses: ./
        with:
          image: "ghcr.io/rprakashg-redhat/eventscheduler@sha256:ba9347ae0d0857ea9b11d1e7bb63e86c960cb9d670cf48330b4e22fd9fd1e4df"
          api-token: ${{ secrets.ROX_API_TOKEN }}
          central: ${{ secrets.ROX_CENTRAL }}
          output: table
          output-path: ${{ runner.temp }}
```

