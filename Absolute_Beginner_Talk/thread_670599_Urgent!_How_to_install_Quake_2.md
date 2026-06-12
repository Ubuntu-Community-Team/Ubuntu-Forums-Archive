---
title: "Urgent! How to install Quake 2"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2008-01-17
Hi guys, here I am converting a Windows user to Ubuntu ;)

Everything is going fine of course, but the only thing I definitely need to do in order to complete my friend requirements is install the legendary Quake 2 natively.

I knew about some script that installs the latest version.. But I can't find it. Could you please give me a hand if you know how to install it?


Thank you guys!

---

### Post by Kosimo on 2008-01-17
We have the original CD by the way

Would be nice if is possible to listen the soundtrack as well.

---

### Post by RomeReactor on 2008-01-17
Hi. You can install the **quake2** and **quake2-data** packages from the repositories:
```
sudo aptitude install quake2 quake2-data
```
Then use quake2-data to install the data files from the CD.

---

### Post by Kosimo on 2008-01-17
> **RomeReactor said:**
> Hi. You can install the **quake2** and **quake2-data** packages from the repositories:
```
sudo aptitude install quake2 quake2-data
```
Then use quake2-data to install the data files from the CD.

Everything is installed.... But I can't find out how to use quake2-data to install the game from CD

---

### Post by Kosimo on 2008-01-17
Any other idea please? 

:KS

---

### Post by Kosimo on 2008-01-17
This is what I get after quake2 in terminal

> -laptop:~$ quake2
***** WARNING *****

   The networking part of Quake II (especially the server part) contains
   several unfixed security issues. Therefore, Quake II should not be
   used over untrusted networks (like the internet). The version
   included in Debian is intended only for local play.   

   See for an possibly non-exhaustive list of issues:
   [http://archives.neohapsis.com/archives/bugtraq/2004-10/0299.html](http://archives.neohapsis.com/archives/bugtraq/2004-10/0299.html)
   [http://www.r1ch.net/stuff/r1q2/](http://www.r1ch.net/stuff/r1q2/)
   [http://bugs.debian.org/280573](http://bugs.debian.org/280573)

*******************

Do you understand the security implications of continuing?
y
QuakeIIForge 0.3
using /home/cosimo/.quake2/baseq2/ for writing
couldn't exec default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
loading oss sound output driver, ok
oss: buffer size is 16384, 8192 samples
sound sampling rate: 11025
------------------------------------
------- Loading ref_softx.so -------
LoadLibrary("ref_softx.so")
No joysticks found
SNDDMA_Shutdown
recursive shutdown
Error: Couldn't load pics/colormap.pcx


---

### Post by RomeReactor on 2008-01-17
> **Kosimo said:**
> Everything is installed.... But I can't find out how to use quake2-data to install the game from CD

It seems that [the package doesn't have the pertinent documentation]("https://bugs.launchpad.net/ubuntu/+source/quake2-data/+bug/34410"); to use the package open a terminal and run:
```
sudo dpkg-reconfigure quake2-data
```
Also take a look at [this thread]("http://ubuntuforums.org/showthread.php?p=3525346")--especially the posts of **reset3x**.

---

### Post by Kosimo on 2008-01-18
> **RomeReactor said:**
> It seems that [the package doesn't have the pertinent documentation]("https://bugs.launchpad.net/ubuntu/+source/quake2-data/+bug/34410"); to use the package open a terminal and run:
```
sudo dpkg-reconfigure quake2-data
```
Also take a look at [this thread]("http://ubuntuforums.org/showthread.php?p=3525346")--especially the posts of **reset3x**.


Done ;)

Thank you!

---

### Post by bengoza on 2008-06-11
I don't see a quake2 package in Hardy. I see quake2-data, and quake3-data, but no quake2. Did they remove it since Gutsy?

---

### Post by Rhubarb on 2008-06-11
Good point, I can't find quake2 / quake3 in the Ubuntu repositories either.

I do know that you can get quake3 running easily with ioquake3:
[http://www.ioquake3.org/](http://www.ioquake3.org/)

I haven't done too much research on quake2, but I do know for a fact that quake2 runs beautifully in wine.

---

### Post by bengoza on 2008-06-12
I can't get it (Quake 2) to install in wine. Maybe I'm not doing it right (almost certainly). I put the CD in, and I right click on Setup.exe and choose open with Wine. I'm able to click on Install, but then I get a black screen and the installer hangs. Any suggestions?

---

### Post by derekgroves on 2008-06-12
I get the exact same blank screen in WINE myself....although I'm trying to install the Quake 2 demo first to make sure my older laptop is going to handle it fine.

I'm able to extract the install files, but when I run setup.exe I get the splash screen, click install, then black with only a cursor.

Any ideas?

Hardware is Dell Inspiron 700m, Intel integrated video, running Hardy Heron and .18 kernel.  Thanks.

---

