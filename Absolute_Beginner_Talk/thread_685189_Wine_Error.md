---
title: "Wine Error"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Fizzzy on 2008-02-01
Whenever I try to load a application in wine using the terminal I always get one of these errors:

```
Warning: could not find DOS drive for current working directory '/home', starting in the Windows directory.
fixme:exec:SHELL_execute flags ignored: 0x00000500
Application could not be started, or no application associated with the specified file.
ShellExecuteEx failed: File not found
```
**or**
```
Warning: could not find DOS drive for current working directory '/home', starting in the Windows directory.
wine: could not load L"c:\\windows\\system32\\Application.exe": Module not found
```

I'm trying both of these commands:
```
wine application.exe
```
**and**
```
wine start application
```

Neither of those seemed to work, and i've tried with different applications, does anyone know what i'm doing wrong?

---

### Post by Nythain on 2008-02-01
run winecfg in the terminal first (i think thats the right command) basically wine isnt done settin itself up yet, and hasnt created the "windows file structure" yet, wich wine is looking for.

---

### Post by Fizzzy on 2008-02-01
> **Nythain said:**
> run winecfg in the terminal first (i think thats the right command) basically wine isnt done settin itself up yet, and hasnt created the "windows file structure" yet, wich wine is looking for.

I'm pretty sure i've set it up, i've gotten one program to install and work before.

---

