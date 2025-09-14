# Microsoft Store URL Installer

A small Windows utility to **download and install Microsoft Store apps from a URL**, without opening the Store app UI.

> **Status:** Binary-only release for now (source to be added when available).  
> **File:** `MicrosoftStoreInstaller.exe` (0.03 MB)  
> **SHA256:** `2b26c60577820bcdf7ac8aaa925974613fa0659bcfb17dbbb081101657265b80`

---

## ✨ Features
- Paste an **apps.microsoft.com** (or Store) URL and install directly.
- Download the underlying **.msixbundle/.appx/.appxbundle** and dependencies.
- Optional **silent** install for scripting scenarios (if supported by the package).
- Clear logging to help diagnose failures.

> This tool is intended for legitimate installs of **free** or already **licensed** apps. It does **not** bypass licensing, DRM, or payment.

---

## ✅ Requirements
- Windows 10 or 11
- Internet connectivity
- Permission to install Store apps on the machine (and admin if required by the package)

---

## 📦 Download
Get the latest binary from **Releases** and verify the checksum:

```powershell
# Verify SHA-256
Get-FileHash .\MicrosoftStoreInstaller.exe -Algorithm SHA256
```

Expected:
```
SHA256: 2b26c60577820bcdf7ac8aaa925974613fa0659bcfb17dbbb081101657265b80
```

---

## 🚀 Usage

> **Note:** If you have a different CLI interface, update this section accordingly.

**Basic:**
```bat
MicrosoftStoreInstaller.exe <Store URL>
```

**Options (example syntax):**
```
--output <dir>      # where to save the downloaded package(s)
--silent            # attempt silent install if the app supports it
--force             # overwrite existing downloads
--skip-install      # only download, do not install
--log <file>        # write detailed logs to a file
```

**Examples:**
```bat
MicrosoftStoreInstaller.exe https://apps.microsoft.com/detail/9WZDNCRFHVJL
MicrosoftStoreInstaller.exe https://apps.microsoft.com/detail/9NBLGGH4NNS1 --silent --output C:\Temp\store-cache
```

---

## 🔐 Security & Privacy
- Always verify the checksum above. Windows SmartScreen may warn for unsigned binaries.
- Logs may include package identifiers but no credentials.
- The tool does **not** attempt to bypass Microsoft licensing or region restrictions.

---

## ⚠️ Limitations
- Paid apps or apps requiring sign-in may still open the Store app or fail.
- Some packages do not support silent install.
- Corporate devices with policy restrictions may block sideloading or offline installation.

---

## 🛠 Troubleshooting
- Run from an **elevated** terminal if permission errors occur.
- Clear previous partial downloads in your output directory and retry.
- Check Windows **App Installer** is present (`winget install Microsoft.AppInstaller`).
- See the log file (if provided via `--log`) for detailed errors.

---

## 📄 License
For now, **all rights reserved** (binary-only). If/when the source code is restored, licensing may change to MIT.

See `EULA.txt` for end-user terms.

---

## 🗺️ Roadmap
- Open-source the PowerShell implementation (if recovered).
- Add CI to attach checksummed binaries to Releases.
- Richer progress and error codes.

---

## 🙌 Author
Tiago Roque — [GitHub](https://github.com/tiagoroque3) · [LinkedIn](https://www.linkedin.com/)

