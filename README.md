# SOLUM DeviceAPI Documentation

This repository contains the official documentation for the SOLUM DeviceAPI library, which provides system-level control capabilities for Android-based signage devices.

---

## API Documentation

View full API documentation:
https://github.com/solum-signage-system/device_api_documents/blob/main/API_Doc.md

---

## Overview

The DeviceAPI library provides access to the following system-level capabilities:

- Device management
- Display control
- Power management
- Input handling
- System configuration

---

## Compatibility

- Works only on SOLUM platform
- Requires system-level privileges
- Some APIs may vary depending on platform/firmware

---

## Getting Started

### 1. Add GitHub Package Repository

```kotlin
maven {
    name = "GitHubPackages"
    url = uri("https://maven.pkg.github.com/solum-signage-system/cms-system-controller")
    credentials {
        username = "YOUR_GITHUB_USERNAME"
        password = "YOUR_PERSONAL_ACCESS_TOKEN"
    }
}
```

---

### 2. Add Dependency

```kotlin
implementation("com.solum.display:system-manager:{version}")
```

```xml
<dependency>
  <groupId>com.solum.display</groupId>
  <artifactId>system-manager</artifactId>
  <version>{version}</version>
</dependency>
```

---

### 3. Grant Permissions

To use DeviceAPI, one of the following is required:

- Install via CMS Play Wizard
- Request permission via API:

```kotlin
Package.requestGrantSystemAccess(...)
```

---

### 4. Verify Grant Status

```kotlin
val pkg = context.packageName
val granted = Package.checkGrantSystemAccess(context, pkg)
if (!granted) {
    Package.requestGrantSystemAccess(context, pkg)
}
```

---

### 5. Verify Installed Version

```bash
adb shell dumpsys package com.solum.display.system | grep versionName
```

![version](images/version.png)

---

## FAQ

### Where can I check the latest version?

https://github.com/solum-signage-system/cms-system-controller/packages/2142218

---

### Can this be used on general Android devices?

No. It works only on the SOLUM platform.

---

### Does it behave the same on all devices?

No. Full support is available from 2025 production models.

---

### Is the permission persistent?

The permission remains until the device is factory reset.

---

### What should I do if permission fails?

Reinstall the application using CMS Play Wizard and verify again.
