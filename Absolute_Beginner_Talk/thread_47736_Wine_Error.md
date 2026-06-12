---
title: "Wine Error"
date: 2005-07-09
forum: Absolute Beginner Talk
---

### Post by jkarnacki on 2005-07-09
I finally got Wine installed and working.  I let it automatically create a config file using winesetup.  I've tried to open a few win32 executable files but nothing happens.  I then do the command line approach to see if it will return an errors.  I recieve:

jeff@Ubuntu:~/Desktop$ wine SteamInstall.exe
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: cannot open shared object file: No such file or directory
err:module:import_dll Loading library gdi32.dll (which is needed by L"C:\\Windows\\System\\user32.dll") failed (error c000007a).
err:module:import_dll Library USER32.dll (which is needed by L"Z:\\home\\jeff\\Desktop\\SteamInstall.exe") not found
err:module:load_builtin_dll failed to load .so lib for builtin L"GDI32.dll": libstdc++.so.6: cannot open shared object file: No such file or directory
err:module:import_dll Loading library GDI32.dll (which is needed by L"Z:\\home\\jeff\\Desktop\\SteamInstall.exe") failed (error c000007a).
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\jeff\\Desktop\\SteamInstall.exe" failed, status c0000135
jeff@Ubuntu:~/Desktop$

I've tried this with a few other apps and I get the same thing.


Thanks

---Jeff---

---

