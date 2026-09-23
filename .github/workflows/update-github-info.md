---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:

permissions:
  contents: read
  pull-requests: read

tools:
  edit:
  web-fetch:
  github:
    toolsets:
      - repos

network:
  allowed:
    - github.blog
    - github.com

safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    draft: false
    max: 1
---

# Update GitHub Info

Keep Mona's GitHub Info website current with concise, practical updates from official GitHub sources.

## Instructions

1. Read `notes/mona-notes.md` and follow its editorial guidance.
2. Use the GitHub repository API tools to read repository guidance or reference files. Do not use terminal, CLI, or sandboxed commands for repository guidance or reference-file access.
3. Web fetch `https://github.blog/latest/` and `https://github.blog/changelog/`.
4. Select useful, recent items that help developers learn GitHub faster. Prefer a small number of meaningful updates over exhaustive coverage.
5. Update `site/content/github-info.md` with short summaries, links to the official sources, and clear source labels for every GitHub Blog or GitHub Changelog item.
6. Preserve the existing Markdown structure and do not modify unrelated files.
7. Review the resulting diff for accuracy, concise writing, valid links, and accidental unrelated changes.
8. Open a pull request with the proposed `site/content/github-info.md` changes for Mona to review. Explain which sources were checked and summarize the updates in the pull request description.

Do not write directly to `main`, merge the pull request, or publish changes outside the pull request.