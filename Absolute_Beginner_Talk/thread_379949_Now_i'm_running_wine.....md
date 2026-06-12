---
title: "Now i'm running wine...."
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by adza on 2007-03-09
Now that i'm running wine, can windows malware etc that may infect wine environments then run on my linux box? Or does everything still need the superuser password to run... doesn't windows allow superuser rights to the user by default? 
**Edit** i'm actually having an issue now, i've installed wine and then installed Medieval total war II (yay! - bye bye windows haha), however this needs directx 9.0 to run and when i try to launch medieval, it craps out... no good. Terminal error is 

adza@adza:~$ fixme:win:EnumDisplayDevicesW ((null),0,0x34f770,0x00000000), stub!fixme:system:SystemParametersInfoW Unimplemented action: 8202 (SPI_GETFONTSMOOTHINGTYPE)
err:module:import_dll Library D3DX9_30.DLL (which is needed by L"C:\\Program Files\\SEGA\\Medieval II Total War\\medieval2.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\SEGA\\Medieval II Total War\\medieval2.exe" failed, status c0000135

so as shown above, this is looking for the directx dll file however it won't let me run the directx installer? also craps out...

adza@adza:~$ wine /media/cdrom0/directx9/DXSETUP.exe
fixme:mscoree:GetCORVersion (0x61fb3384, 600, 0x61fb3370): semi-stub!
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x61fb327c
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x61fb2a98
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x61fb2a98
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x61fb2a98
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x61fb2a98
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x61fb2a98
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x61fb2a98
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x61fb2a98
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x61fb2a98
fixme:mscoree:LoadLibraryShim (0xa129a8 L"fusion.dll", (nil), (nil), 0x61fb2a7c): semi-stub

is there a linux directx program i need to run or similar?

sorry for the massive post!

---

### Post by Patrick K on 2007-03-09
There was a long thread on this a couple weeks ago. A fellow purposely ran some viruses under wine. IIRC, one did minor damage to Linux and only a couple others ran at all. Try a search on wine and virus. It may turn up.

---

### Post by steven8 on 2007-03-09
I had heard that Linux wasn't hurt, but the one virus stuck wine in a loop.  He removed and re-installed wine, no damage done.

---

### Post by adza on 2007-03-09
that thread will make for some interesting reading then.. off to search :) hopefully someone can help me out with my edit :P

---

### Post by steven8 on 2007-03-09
You do not need to install directx.  Wine supplies the apis that handle that.

---

### Post by adza on 2007-03-09
so what could be the problem with the game not running? if it's missing a dll how do i get it to recognise that file through wine?

---

### Post by steven8 on 2007-03-09
go to winehq and see if that program runs in wine.  Wine can't run verything just yet.

---

### Post by adza on 2007-03-09
Alas,

     No joy :( will have to wait for that one to come out it seems...

---

### Post by steven8 on 2007-03-09
> **adza said:**
> Alas,

     No joy :( will have to wait for that one to come out it seems...

I was afraid of that. :(

---

### Post by adza on 2007-03-09
it is of little bother, i am dual booting at the moment anyway.... i was merely overjoyed at the prospect of burning my windows license, as this is the last piece of software that i use on windows... haha i will watch winehq (maybe a litte RTFM would've helped before this post hehe) with great interest now...

---

