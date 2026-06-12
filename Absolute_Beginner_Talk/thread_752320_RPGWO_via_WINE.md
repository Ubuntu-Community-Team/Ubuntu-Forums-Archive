---
title: "RPGWO via WINE?"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by HelloKitty on 2008-04-11
Before anyone tells me to search, I have.  There's one thread, but it's quite old (300 pages back) and I assume that a new thread is better than a necro bump.  That thread is [here]("http://ubuntuforums.org/showthread.php?t=504488").

Essentially I'm trying to get RPGWO, a small indie game, working in Ubuntu.  I download the main files from the official site (found [here]("http://www.rpgwo.com/downloads.html")).

I extract it and I get an exe, a cab, and a .lst.

If I "wine setup.exe" while in that folder, the setup file boots up.  It then says it's loading "STDOLE32.dll"" (2 of 2), then it closes and it's gone.

Note, for a brief second I can see "1 of 2" but it's only there for a fraction of a second.  

After it crashes, in the console I get this.

```

fixme:ole:DllRegisterServer stub
err:module:import_dll Library MSVBVM60.DLL (which is needed by L"C:\\windows\\Setup1.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\Setup1.exe" failed, status c0000135

```

I'm stuck.  Crossover has the same problem, but I don't know where to check errors in Crossover, so it just exits mysteriously.

---

### Post by Kevin Fischer on 2008-04-13
RPGWO isn't in Wine's [AppDB]("http://appdb.winehq.org/"), so if you feel like getting in your good deed for the day, you should add it.

Try installing the VB runtime:
```
test -f vbrun60.exe || wget http://download.microsoft.com/download/vb60pro/install/6/win98me/en-us/vbrun60.exe
wine vbrun60.exe
```

See if the MSVBVM60.DLL error goes away after that.

---

