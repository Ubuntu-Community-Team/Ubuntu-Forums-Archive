---
title: "Tversity and WINE"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by phoenix23 on 2007-05-20
I'm running a live edition of Feisty, trying to sync with my Xbox 360.

I installed WINE, hoping to get the Windows version of Tversity to work, but it freezes when you start the server and asks you to reboot.

Since rebooting a live disc causes one to lose all data,can anyone confirm Tversity works with WINE?

---

### Post by Terl on 2007-05-21
Seems like it... Check WineHQ.  It is always best to go to WineHQ for current info regarding applications and whether they work/don't work.   They also give nice how-to's and other tips.  Here's the link for you:  [tversity ate WineHQ]("http://appdb.winehq.org/appview.php?iVersionId=7864")

---

### Post by jdogzilla on 2007-08-11
Hello, I have Ubuntu 7.04 and Wine 0.9.41-0.  I'm trying to run tversity under this version of wine and am getting the following error:

wine .wine/drive_c/Program\ Files/TVersity/Media\ Server/MediaServer.exe -start
fixme:actctx:FindActCtxSectionStringW 00000000 (null) 2 L"msvcr80.dll" 0x347b2c
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
Starting TVersity Media Server...
fixme:actctx:FindActCtxSectionStringW 00000000 (null) 2 L"msvcr80.dll" 0x347b2c
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:msvcrt:_set_error_mode dummy implementation (old mode: 0, new mode: 2)

Anybody have any clue as to what I can do to fix this? 

Thanks

---

### Post by jdogzilla on 2007-08-19
Hello, in Wine 0.9.41-0. I'm unable to register the msvcr80.dll using regsrv command.  Anybody been successful with that.  I get an error message every time I try to do so.

---

