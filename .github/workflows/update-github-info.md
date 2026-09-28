---
name: update-github-info
description: Update GitHub information from official sources.
on:
  schedule:
    - cron: "0 0 * * *"
  workflow_dispatch:
permissions:
  contents: read
  pull-requests: write
tools:
  edit:
    - site/content/github-info.md
  web-fetch:
    - https://github.blog/latest/
    - https://github.blog/changelog/
network:
  allowed:
    - github.blog
    - github.com
safe-outputs:
  create-pull-request:
    title: "Update GitHub information"
    draft: false
---

Read `notes/mona-notes.md`. Fetch and review:

- https://github.blog/latest/
- https://github.blog/changelog/

Update `site/content/github-info.md` with relevant, accurate information. Use the safe `create-pull-request` output to open a pull request for Mona to review. Do not write directly to the default branch.
