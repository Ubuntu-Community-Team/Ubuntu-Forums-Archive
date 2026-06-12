---
title: "Problems with Asus N53SV after installing NVIDIA Driver"
date: 2011-07-28
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Migel Anjel on 2011-07-28
Hi everyone!
I'm quite new on using any Unix based OS so this might be a very dumb question, but please help me.

I just installed Ubuntu 11.04, and at first it worked fine. But, after installing the private driver for my graphic card (GeForce GT540M), the OS told me that i hardware wasn't good enough for running Unity, wich is wierd, because before installing the driver, Unity worked. Anyway, i managed to get that the driver wasn't active, so i run the command ```
sudo nvidia-xconfig
``` to activate it. After that i resarted the system and it never got to run Ubuntu again.
It gets frozen while doing the first steps of initializing.

Does anyone know how to fix this?

Thanks for your help!

PS. My compouter is an Asus N53SV.

---

### Post by AureiAnimus on 2011-07-30
Unfortunately, I don't know enough to tell you how to properly remove the nvidia drive (that should solve it), but I can tell you that once you managed to restore it, you will want to take a look at this thread: [http://ubuntuforums.org/showthread.php?t=1791081](http://ubuntuforums.org/showthread.php?t=1791081) Most of the problems you might have, including the Nvidia card have solutions there. In addition, learning how to back up your system should be worth it: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by Fishkins on 2011-07-31
I think I was having a similar problem with my UL50VT. If it's the same thing, there are two ways you might be able to fix things:

1) Open BIOS settings (press F2, F10, DEL, or possibly another key while booting) and change the SATA mode to compatibility. I'm not sure if this will work for you, but that's what I had to do to get Ubuntu to work with my nvidia card.

2) Boot in recovery mode, and choose graphics failsafe mode. This should allow you to run ubuntu temporarily. From there, you can delete xorg.conf (in /etc/X11). That's the file that's created by the nvidia-xconfig command, and for me it was causing Ubuntu to crash unless I changed the aforementioned BIOS setting.

Hopefully that helps.

---

### Post by cucisan on 2011-08-02
see my thread on how to get that stuff working. (postet above)

why would you want to use nvidia card all the time anyways? :)

---

### Post by tijs14tijs on 2011-08-05
Does it still boot? Mine didnt :P (if not: delete /etc/X11/Xorg.conf)

This is going to be hard for you if your not a guru, I have to go to the same process of installing the NVidia drivers. 
Detect your issues here: [Nvidia forums]("http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14")

Download Drivers: [Nvidia driver download page]("http://www.nvidia.com/Download/index.aspx?lang=en-us")

And, read the manual. Yes I know this manual suck XD:
[Manual]("http://us.download.nvidia.com/XFree86/Linux-x86_64/280.13/README/index.html")

Good luck :P

If you find the answer, mail me please
Tijsxdmaas at gmail dotcom

---

