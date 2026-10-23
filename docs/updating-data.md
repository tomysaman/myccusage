# Updating the data

The data comes from my private `ccusage` repo. `scripts/update-data.ps1` (or `scripts/update-data.sh`) downloads its merged data and writes `data.js` with per-day, per-model token and cost totals, with all machines summed together.

Nothing with a time of day is published. Billing blocks, session ids, project names, machine tags and raw ccusage output are left out.

## Run the script

You need the [GitHub CLI](https://cli.github.com/), logged in (`gh auth login`) with an account that can read `tomysaman/ccusage`.

Windows PowerShell:

```powershell
powershell -ExecutionPolicy Bypass -File .\scripts\update-data.ps1
```

macOS (needs `node`):

```sh
./scripts/update-data.sh
```

Both scripts write the same `data.js`.

Then commit and push `data.js`:

```sh
git add data.js && git commit -m "Data update" && git push
```

Options:

- `-Repo owner/name` (`--repo` in the .sh) reads from a different source repo.
- `-Source path/to/data.js` (`--source` in the .sh) reads a local copy instead of GitHub.

## View locally

Open `index.html` in a browser. It loads `data.js` from the same folder and makes no other requests.
