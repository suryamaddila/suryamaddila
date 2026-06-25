
name: Generate Snake Animation
 
on:
  # Run automatically every 12 hours
  schedule:
    - cron: "0 */12 * * *"
  # Allow manual triggering from the Actions tab
  workflow_dispatch:
  # Run on every push to the default branch
  push:
    branches:
      - main
 
jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5
 
    steps:
      - name: Generate snake SVGs
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark&color_snake=%2300D4AA&color_dots=%230D1117,%23FF6B6B,%2300D4AA,%2300D4AA,%2300D4AA
 
      - name: Push to output branch
        uses: crazy-max/ghaction-github-pages@v4
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
 
