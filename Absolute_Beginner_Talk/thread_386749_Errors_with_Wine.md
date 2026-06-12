---
title: "Errors with Wine"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by Stormweaver on 2007-03-17
Ok here is the log from my attempt at this:

stormweaver@Hurricane:~/Desktop/wowcopy$ wine installer.exe
wine: creating configuration directory '/home/stormweaver/.wine'...
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\rundll32.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"c:\\windows\\system32\\rundll32.exe" failed, status c0000135
wine: wineprefixcreate failed while creating '/home/stormweaver/.wine'.
stormweaver@Hurricane:~/Desktop/wowcopy$ wineprefixcreate
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.6: wrong ELF class: ELFCLASS64
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system32\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"c:\\windows\\system32\\rundll32.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"c:\\windows\\system32\\rundll32.exe" failed, status c0000135
stormweaver@Hurricane:~/Desktop/wowcopy$ 


So I am guessing I am missing things to make this run, that the [http://wiki.winehq.org/UbuntuAMD64](http://wiki.winehq.org/UbuntuAMD64) neglects to tell you.  I can't make Wine run as a result, my attempt to get aid from #winehq on IRC was much much less then useful.  Can someone help me figure out what I've done wrong and if its correctable?


Stormweaver

---

### Post by zvacet on 2007-03-17
Put your exe in .wine>C drive>program files.(you will find .wine in your home hidden folders)
```
winefile
```
C>program files>your exe>double click

---

### Post by Stormweaver on 2007-03-18
Ok, I am really new to Ubuntu - Could you explain that a bit more clearly???


Stormweaver

---

### Post by zvacet on 2007-03-19
Programs<places>personal folder>click on it>view>hidden files>.wine
Now you know where .wine is,so copy exe in .wine>c drive>program files
In terminal(programs>acessories>terminal)type
```
winefile
```
click on C and find program files.this is the place where your exe is.Double click on it and that´s it.

---

