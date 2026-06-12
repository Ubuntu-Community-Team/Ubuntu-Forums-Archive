---
title: "serious wine error--help"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by KarmaKing on 2006-07-17
> karmaubuntu:~$ winecfg
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") not found
err:module:import_dll Library shlwapi.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Library shell32.dll (which is needed by L"c:\\windows\\system32\\comdlg32.dll") not found
err:module:import_dll Loading library shlwapi.dll (which is needed by L"c:\\windows\\system32\\comdlg32.dll") failed (error c000007b).
err:module:import_dll Library comdlg32.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") not found
err:module:import_dll Loading library shell32.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") failed (error c000007b).
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") not found
err:module:import_dll Loading library shlwapi.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") failed (error c000007b).
err:module:LdrInitializeThunk Main exe initialization for L"c:\\windows\\system32\\winecfg.exe" failed, status c0000135
karma@karmaubuntu:~$



I was following a how-to on the WINEHQ page, trying to [install Native MSXML 3]("http://wiki.winehq.org/NativeMSXML3")  and I got the message above in the terminal.  Now wine won't work at all.  THe cfg won't come up either.  I tried to a complete reinstall, but nothing, just the same error.

any ideas on how I can get back

---

### Post by KarmaKing on 2006-07-17
ok, got a fresh install, but I could use some help installing the Native MSXML from this wine pages
[http://wiki.winehq.org/NativeMSXML3]("http://wiki.winehq.org/NativeMSXML3")
[http://wiki.winehq.org/NativeDcom](http://wiki.winehq.org/NativeDcom)
[http://wiki.winehq.org/NativeMsi]("http://wiki.winehq.org/NativeMsi")

there is a point on the 2 page there wher it asks for one to install with this command, but I can't figure it out.  Where do i do that command?  I tried in terminal, but nothing.

---

