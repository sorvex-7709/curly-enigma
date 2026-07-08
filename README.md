# TagalogUI (Aliucord plugin)

Swaps a curated set of common Discord UI strings (buttons, menu labels, settings
sections) into Tagalog. See the doc comment at the top of `TagalogUI.kt` for
exactly what this does and doesn't cover — short version: it reaches Android
resource-sourced text (notification actions, some native dialogs/toasts), not
the bulk of Discord's React-Native-rendered chat/settings screens. Nothing in
your dictionary crashes anything — unmatched strings just stay in English.

This is real, uncompiled source built against Aliucord's actual current plugin
template (github.com/Aliucord/plugins-template) and documentation
(github.com/Aliucord/documentation/tree/main/plugin-dev). It has **not** been
compiled or tested on-device — building an Aliucord plugin needs the Android
Gradle toolchain, which isn't available in the environment this was written in.

## Building the .zip from your phone (no computer needed)

1. Create a new GitHub repo from this folder:
   - Easiest: create an empty repo on GitHub, then use GitHub's mobile web
     "Add file → Upload files" to upload everything in this zip, preserving
     the folder structure.
2. Go to the **Actions** tab of your repo.
3. Push a commit (the upload in step 1 counts) or run the "Build" workflow
   manually (Actions tab → "Build" → "Run workflow").
4. Open the finished workflow run → scroll to **Artifacts** → download
   `plugins`. Inside is `TagalogUI.zip`.
5. On your phone: move `TagalogUI.zip` into `/sdcard/Aliucord/plugins/`
   (or use Aliucord's in-app plugin installer to load the file), then
   restart Aliucord.

If the build fails, open the failed step in the Actions log — it'll usually
be a Gradle/Kotlin error pointing at the exact line. Common first-run fixes:
- Rename the placeholder package `com.github.yourusername.tagalogui` (in
  `plugins/build.gradle.kts` and the Kotlin file's folder path/package line)
  to something with your own name — they just need to match each other.

## Editing translations

Everything Tagalog-related lives in
`plugins/TagalogUI/src/main/assets/tagalog_strings.json` — plain
`"English": "Tagalog"` pairs, case-insensitive matching. Add a line, push,
re-download the artifact. No Kotlin required for this part.
