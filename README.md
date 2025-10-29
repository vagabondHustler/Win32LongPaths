# Win32LongPaths

Two `.reg` files to enable or disable Win32 long paths by toggling `HKLM\SYSTEM\CurrentControlSet\Control\FileSystem\LongPathsEnabled`. Removes the legacy 260-character `MAX_PATH` limit on Windows 10 1607+ and Windows 11 for applications that are long-path aware.

## What it does
- `EnableLongPaths.reg` sets `LongPathsEnabled=1` (DWORD).
- `DisableLongPaths.reg` sets `LongPathsEnabled=0` (DWORD).

## Why
Prevents failures when paths exceed 260 characters.

## File contents

### EnableLongPaths.reg
```reg
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\FileSystem]
"LongPathsEnabled"=dword:00000001
````

### DisableLongPaths.reg

```reg
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\FileSystem]
"LongPathsEnabled"=dword:00000000
```

## Usage

1. Double-click the desired `.reg` file and accept the prompt.
2. Reboot to ensure all processes pick up the change.

Verify:

```bat
reg query HKLM\SYSTEM\CurrentControlSet\Control\FileSystem /v LongPathsEnabled
```

* 
## Official docs

* Maximum Path Length Limitation: [Maximum file path limitation](https://learn.microsoft.com/windows/win32/fileio/maximum-file-path-limitation)
* Naming Files, Paths, and Namespaces: [Naming a file](https://learn.microsoft.com/windows/win32/fileio/naming-a-file)
* Enable Win32 long paths (policy): [Enable win32 long paths](https://learn.microsoft.com/windows/security/identity-protection/application-control/security-policy-settings/enable-win32-long-paths)

## VirusTotal

[EnableLongPaths.reg](https://www.virustotal.com/gui/file/e51cca47153a1fa828c13a6e998bd1456b3c575181522b5cca8a2042655f38a3)

[DisableLongPaths.reg](https://www.virustotal.com/gui/file/96208dc528e411158ddb1b6ac3d09566e3556f68fb3a9ae6bf8c3f2a7bed7df7)




