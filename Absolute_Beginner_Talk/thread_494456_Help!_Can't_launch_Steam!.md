---
title: "Help! Can't launch Steam!"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by chris062689 on 2007-07-06
The last thing I remember doing is making Steam go to offline mode. I can't boot up into Steam anymore, it juts gives me the following error.  I've tried reinstalling (I think it might be something I can fix in the registry.)

[email]chris@ubuntu:~/.wine[/email]/drive_c/Program Files/Steam$ wine Steam.exe
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:process:IsWow64Process (0xffffffff 0x3e7e44) stub!
fixme:reg:RegOpenUserClassesRoot (0x1fc, 0x0, 0x2000000, 0x33b3c4) semi-stub
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {8856f961-340a-11d0-a96b-00c04fd705a2} 0x33b398
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {8856f961-340a-11d0-a96b-00c04fd705a2} 0x33b344
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {8856f961-340a-11d0-a96b-00c04fd705a2} 0x33acb8
Shutting down. . .

It was working before....

---

### Post by shearn89 on 2007-07-07
its saying something about access rights, so maybe try "sudo wine steam.exe"?

---

### Post by chris062689 on 2007-07-07
Tried it.

---

### Post by chuckyp on 2007-07-07
Try launching steam from inside of its own folder.  i.e. 'cd ~/.wine/drive_c/Program Files/Steam/Steam.exe'  then wine Steam.exe

---

### Post by chris062689 on 2007-07-07
Tried it :(
Same error.

---

