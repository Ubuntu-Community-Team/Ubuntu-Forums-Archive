---
title: "Flash player on PPC: QEMU? MOL? GNASH?"
date: 2007-03-25
forum: Apple PPC Users
---

### Post by jae1227 on 2007-03-25
I have been trying to get flash player on my 800mhz G3 iBook. First I tried Gnash but have had very little success with it. Next I tried QEMU. I was able to run a DSL live disk but was stunned when it said I had a PII 24mhz processor. I know my ppc processor must emulate the x86 processor but did not know that it would be THAT resource intensive. Now I am unsuccessfully trying to get Mac on Linux to work to works so I can boot into Tiger to run Flash Player. Is there something else that I could do. I thought there might be some way to emulate the X86 processor just for Flash Player because there is a Flash Player for Linux. Hope someone can help.


This is my 24mhz PII in QEMU
[[IMG]http://img99.imageshack.us/img99/866/screenshotkd9.th.png[/IMG]](http://img99.imageshack.us/my.php?image=screenshotkd9.png)

---

### Post by 3rdalbum on 2007-03-26
What success have you not had? I must say I was pretty impressed with Gnash's compatibility on my G3, even if it was incredibly slow :-)

Qemu and Bochs always report very low-end processors, so the guest operating system does not try to use processor commands that the emulators don't support. Don't worry about the reported processor speed; it would report exactly the same speed even if you had a quad G5 (but of course, run faster!)

Theoretically, you can use "User-mode emulation" on Qemu to emulate just an x86 program and its libraries inside your PowerPC Linux distribution. In practice though, I've not heard from anyone who has done it. There is a howto for x86-on-x86 user-mode emulation on the Qemu website - if you can get it going on PowerPC, please post a HOWTO here! I'm looking for the secret of it so I can include easy support in my Copland distribution (which has been sadly neglected for the past couple of weeks because I'm so busy!)

---

### Post by spikee on 2007-03-26
Please check out Swfdec. [http://swfdec.freedesktop.org/wiki/](http://swfdec.freedesktop.org/wiki/) It's "supposedly" better than Gnash.

---

### Post by stmiller on 2007-03-27
You can play flash video on PPC Linux with the most current VLC (ver. 0.8.6 and higher).

Just use this bookmark page: 

[http://1024k.de/bookmarklets/video-bookmarklets.html](http://1024k.de/bookmarklets/video-bookmarklets.html)

To download the .flv file from youtube, etc., then open that .flv file in vlc.

The current VLC will also play and h.264 and other misc. formats. It's pretty good!

---

### Post by fkdev on 2007-03-29
For those of you suffering from gnash being slow and resource hogging, I would recommend recompiling gnash. The version in the repositories is compiled to use OpenGL as it's rendering backend, which for computers with no direct rendering or otherwise poor OpenGL should not use. Recompile gnash with the AGG or Cairo backend and gnash should work MUCH better.

---

