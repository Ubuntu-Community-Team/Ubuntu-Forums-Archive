---
title: "philips wacs7000 to ubuntu"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by in2media on 2007-08-09
hi, i have a philips wacs7000 wireless music system and want to connect to my ubuntu stsem. although this is quite easy on windows via the software they include does anyone know how to do this on ubuntu

---

### Post by splintercellguy on 2007-08-09
How exactly do you mean "connect" to it? I'm not wholly familiar with your product but I believe it is one of those wireless music streamers?

---

### Post by in2media on 2007-08-09
yea its a wireless music system and has wifi. but on windoze you use a cd supplied which has wadm or this prog
[http://www.lucia-mathias.com/wacs/](http://www.lucia-mathias.com/wacs/)
i have my wacs connected to my belkin router via ethernet cable

---

### Post by splintercellguy on 2007-08-09
Hmm, you could try Wine compatibility layer for that app, worth a shot. How exactly is the device hooked up to your PC?

EDIT: It seems a PC would communicate with such a device via UPnP. Most likely you might be able to get the application running under Wine.

---

### Post by in2media on 2007-08-09
its not directly connected to pc, its connected to my router and i use the software to edit my songs or play them on pc etc.
this way windows has no problem identifying the wireless music system.

---

### Post by splintercellguy on 2007-08-09
Ah, then just run the program you have under Wine. Follow these instructions to obtain latest wine: [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb) then do wine "path to EXE file" to get it working.

---

### Post by in2media on 2007-08-09
ok mate thanks il give it a go

---

### Post by in2media on 2007-08-09
rite installed wine and ran the windows cd software i got from philips. when i open wine and add the application and click ok, then try to run it in wine i get the following error
john@john-laptop:~$ wine wadm
wine: could not load L"c:\\windows\\system32\\wadm.exe": Module not found
john@john-laptop:~$

---

### Post by in2media on 2007-08-09
ok im trying to get wine working but not having any luck
john@john-laptop:~$ ls -la ~/.wine/dosdevices/
total 8
drwxr-xr-x 2 john john 4096 2007-08-09 17:58 .
drwxr-xr-x 4 john john 4096 2007-08-09 20:26 ..
lrwxrwxrwx 1 john john   10 2007-08-09 17:51 c: -> ../drive_c
lrwxrwxrwx 1 john john    9 2007-08-09 17:52 d:: -> /dev/scd0
lrwxrwxrwx 1 john john    1 2007-08-09 17:51 z: -> /
john@john-laptop:~$ wine "c:\program files\wadm\wadm.exe
> wine "c:\program files\wadm\wadm.exe
wine: cannot find 'c:\program files\wadm\wadm.exe
wine c:program'
john@john-laptop:~$ wine "c:\program files\wadm\wadm.exe
wine "c:\program files\WADM\WADM.exe
wine: cannot find 'c:\program files\wadm\wadm.exe
wine c:program'
john@john-laptop:~$ wine "c:\program files\wadm\wadm.exe
wine "c:\program files\Philips\WADM\WADM.exe
wine: cannot find 'c:\program files\wadm\wadm.exe
wine c:program'
john@john-laptop:~$ wine "c:\program files\wadm\wadm.exe
wine "c:\program files\Philips\WADM\WADM.exe
wine: cannot find 'c:\program files\wadm\wadm.exe
wine c:program'
john@john-laptop:~$ wine foo.exe
wine: could not load L"c:\\windows\\system32\\foo.exe": Module not found
john@john-laptop:~$ wine c:\\myapps\\foo.exe
wine: cannot find 'c:\myapps\foo.exe'
john@john-laptop:~$

---

### Post by zanac on 2008-03-28
The solution is get these dll from a Windows XP with installed a new copy of Windows Media Player:
wmasf.dll
WMVCore.DLL

WADM.exe with these dlls run fine with wine ;)

---

