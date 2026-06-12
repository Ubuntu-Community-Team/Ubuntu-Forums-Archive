---
title: "How extensive is windows emulation?"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by SSB on 2006-06-08
I mainly ask this for 2 or 3 programs, namely FL Studio and Gunz. Would I be able to run either of these on linux with VMWare or anything? I know virtually nothing about linux yet, and if I can I would like to get away from windows completely. I just need a few programs..

---

### Post by sYs^ on 2006-06-08
In vmware you can run any windows programs and if you have some luck you can run them in wine also.
There are some other emulators too, like Cedega for games (with directx support)  and CrossOver Office for softwares like Word, Excel and AutoCad. There are some Dos emulators too like DosBox and DosEmu.

---

### Post by philipgm on 2006-06-08
VMware will allow you to run Windows XP on your linux box, and then you can install your windows software there. There are limitations though, under VMware  Windows XP is limited to the device driver capabilities of your linux installation. So if 3D dri is required for an application and 3D acceleration doesn't work in linux then it won't work on the Windows XP install in VMware either. 

You could look at wine, [www.winehq.com](www.winehq.com). you might be able to find out if wine is known to run your application. Alternatively, [www.codeweavers.com](www.codeweavers.com) have a commercial version of wine. Wine is an API for windows programs so the binaries actually run directly on the machine avoiding performance issues that arise with emulations, such as the machine emulation which is VMware.

Phil

---

### Post by IYY on 2006-06-08
How extensive is it? Not very. Don't count on it, but do try it. It might work perfectly, it might be buggy, or it might not work at all, depending on your applications.

---

### Post by lapsey on 2006-06-08
VMWare is really very extensive for emulation. Everything but a PPC environment for OSX. It's great for most programs, including photoshop. 

On the other hand you mentioned FL studio. Now this is very processor intensive where effects and plugins are concerned. Even more so when running on an emulated virtual machine such as VMWare. It chokes on a 2Ghz Athlon with 4 sytrus layers, so unless you have a much faster machine, emulation is no good for FL.

Then there is Wine. Sadly at the moment it barely supports FL 3 (is suspect there are a ton of unorthodox hacks that went into Fruity at design level), so until they perfect the windows compatibility layer you (like me) will still have to boot into windows to run FL. Not that I'm complaining since it helps me concentrate on the task in hand.

Happy is the day that LMMS (a fruity clone for linux) is developed to a similar level.

---

