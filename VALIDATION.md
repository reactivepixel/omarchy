# Transcode batch verification

Final verification on October 18, 2026, at commit `8ad30b69dde5c5453b62def9ae5345c8a3c0aad7`:

- All 25 focused batch/menu-helper/migration assertions passed, plus existing menu and QML text-format checks.
- Bash/Python syntax, `git diff --check`, structural i18n tests, and `python3 scripts/i18n-sync.py extract-scan --check` passed.
- `I18N_STRUCTURAL=1 OMARCHY_PATH="$PWD" PATH="$PWD/bin:$PATH" ./test/all`: CLI passed; **5 of 454 shell test files failed**, and 10 files contained skipped checks. This is not a fully passing aggregate suite.
- The five remaining failures are `background-instant-reload-test.sh` (initial wallpaper), `background-intro-clone-test.sh` (wallpaper after cover release), `default-apps-test.sh` (Chrome default), `elsewhen-migration-test.sh` (legacy cache), and `screenshot-sanity-test.sh` (missing `omasnap`). All five also failed in a pristine worktree at base `dd07b6269f0dd2a059b8ed5b4124f5adde74d389` under the same environment during the prior baseline comparison. Root causes other than the missing dependency have not been established. The earlier startup-cursor failure did not recur in this final run.
- Graphical acceptance suite not run: repository guidance requires a disposable VM. Live manual verification was performed separately on the installed system as described above.

Only the menu crops are published. They show an isolated compatible port of the feature on installed Omarchy 4.0.4-1; source tests target the submitted checkout. A real Files context-menu test converted two generated HEIC images to 2160×1440 JPEGs from one JPG/medium selection. No user photos were used.
