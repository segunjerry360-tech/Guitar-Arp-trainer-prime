# Arpeggio Trainer — GitHub Actions Android build

This repository packages the supplied standalone `index.html` as an Android app using Capacitor and builds a debug APK with GitHub Actions.

## Files
- `index.html` — the app supplied for packaging.
- `resources/icon.png` — launcher-icon source image.
- `.github/workflows/build.yml` — GitHub Actions build workflow.
- `capacitor.config.json` — Android app ID and display name.

## Build the APK
1. Create a new GitHub repository.
2. Upload the **contents** of this folder to the repository root (not the enclosing folder itself).
3. Open the repository's **Actions** tab.
4. Select **Build Arpeggio Trainer APK** and choose **Run workflow**. A push to `main` or `master` also starts a build.
5. When the workflow finishes, open the run and download the `Arpeggio-Trainer-debug-apk` artifact.
6. Extract the downloaded ZIP; install `app-debug.apk` on your Android phone.

The workflow generates the Android project during the build, so the `android/` directory does not need to be committed.

## App identity
- Display name: Arpeggio Trainer
- Android application ID: `com.triiiga.arpeggiotrainer`

Changing the application ID after installing an APK makes Android treat it as a different app. Keep it stable for future updates.

## Important playback note
The HTML contains its own lock-screen and keep-playing logic. Packaging it in a WebView does not guarantee unrestricted background audio on every Android version or phone. Test playback with the screen off on the target device; a native foreground-audio service may be needed if Android suspends the WebView.
