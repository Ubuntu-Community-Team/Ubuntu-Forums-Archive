---
title: "progr instalation using wine"
date: 2005-10-09
forum: Absolute Beginner Talk
---

### Post by bmarilena on 2005-10-09
I tried this:
[I]wine /media/cdrom/setup.exe
[/I]

and the answer is:
[I]Converted windows dir to new entry HKCU\Environment "windir" = L"c:\\windows"
err:thunk:_loadthunk (commctrl.dll, Cctl1632_ThunkData16, comctl32.dll): Unable to load 'commctrl.dll', error 2
err:module:LdrInitializeThunk "comctl32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"D:\\setup.exe" failed, status c0000142
[/I]


What should I do next?

Probably I didn't configure wine correctly, but I can't locate the error.

HELP please!!!!!


Marilena

---

### Post by Abild on 2005-10-09
It seems like you'll have to copy a native commctrl.dll file into the system directory of your virtual windows installation. (probably ~/.wine/c_drive/windows/system)
You can get the dll file from here: [http://www.dll-files.com/dllindex/dll-files.shtml?commctrl](http://www.dll-files.com/dllindex/dll-files.shtml?commctrl)

Which program are you trying to install?

---

### Post by bmarilena on 2005-10-09
[QUOTE=Abild]It seems like you'll have to copy a native commctrl.dll file into the system directory of your virtual windows installation. (probably ~/.wine/c_drive/windows/system)
You can get the dll file from here: [http://www.dll-files.com/dllindex/dll-files.shtml?commctrl](http://www.dll-files.com/dllindex/dll-files.shtml?commctrl)

Which program are you trying to install?[/QUOTE]

Thanks. I'll try this.

I'm trying to install a law database handeler called Lege4.

---

### Post by bmarilena on 2005-10-09
[QUOTE=Abild]It seems like you'll have to copy a native commctrl.dll file into the system directory of your virtual windows installation. (probably ~/.wine/c_drive/windows/system)
You can get the dll file from here: [http://www.dll-files.com/dllindex/dll-files.shtml?commctrl](http://www.dll-files.com/dllindex/dll-files.shtml?commctrl)

Which program are you trying to install?[/QUOTE]

THANKS... IT WORKS... YUPIIIIIIIIIIIIIIIII!

---

