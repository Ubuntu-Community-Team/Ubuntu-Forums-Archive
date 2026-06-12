---
title: "help with wine/winetools please..."
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by damon11 on 2007-06-09
I have no idea where to ask questions regarding wine and such, so I'll just ask here.
I have installed wine and winetools using guides from these forums, and they appeared to have installed correctly.
Now, whenever I try to install **anything** in winetools (for example, DCOM98 ), it tells me the installation has failed.
Contents of terminal provided, in case it helps:
```
justin@justin-desktop:~$ wt
detecting Wine version... done.
Drive C: is /home/justin/.wine/drive_c
Wine 0
wine is executed as wine
Parameters are --noexit
Browser is /usr/bin/firefox.
WINEVER is "0".
Calls to wine are executed as  "wine".
Config is /home/justin/.wine/winetools.log.
Choice is Base setup
Choice is DCOM98 with checked=F
dcom98.exe to check
software installation verified by /home/justin/.wine/winetools.log
1229056 bytes previously downloaded
WINEDEBUG="fixme-all" WINEDLLOVERRIDES="ole32=n" wine ./dcom98.exe
err:module:load_builtin_dll failed to load .so lib for builtin L"COMCTL32.dll": /usr/local/bin/../lib/wine/comctl32.dll.so: file too short
err:module:import_dll Loading library COMCTL32.dll (which is needed by L"F:\\sys\\dcom98.exe") failed (error c000007a).
err:module:LdrInitializeThunk Main exe initialization for L"F:\\sys\\dcom98.exe" failed, status c0000135
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
Failed: 1
check installation by return value...
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
err:module:load_builtin_dll failed to load .so lib for builtin L"comctl32.dll": /usr/local/bin/../lib/wine/comctl32.dll.so: file too short
err:module:import_dll Loading library comctl32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") failed (error c000007a).
err:module:import_dll Library shell32.dll (which is needed by L"c:\\windows\\system32\\wineboot.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"c:\\windows\\system32\\wineboot.exe" failed, status c0000135
Failed: 1


```

I've tried removing wine and winetools and reinstalling them, and rebooting my computer so far....
Any help with this will be greatly appreciated!

---

### Post by machoo02 on 2007-06-09
One place to go for questions regarding WINE is [this page]("http://www.winehq.org/site/getting_help").  However, be aware that using winetools is not recommended or supported by any of the WINE developers, so if you try to ask them a question or submit a bug report and mention that you've used it you will be asked to uninstall/reinstall WINE without winetools and try again before they will help you.

---

