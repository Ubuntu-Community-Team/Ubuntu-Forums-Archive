---
title: "running local boot scripts c.etc.rc.last&quot;"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by colin2006 on 2008-03-30
I have at last installed Ubuntu to my machine BUT when i try to boot Ubuntu freezes at "running local boot scripts c.etc.rc.last". My machine is a tablet with a Transmeta Crusoe 5800 800MHz CPU 512 mem and a 80gig hard drive

I have pressed enter nothing happens except an empty line. I have tried recovery boot which after running does not produce any error messages, and stops at a terminal command line. What do I do know I do want to give up now. As new to ubuntu I do not know sudo or grub commands. Please help

---

### Post by smurphy_it on 2008-03-30
boot into recovery mode and take at your log files.

in a terminal type cd /var/log

Once there you can do a ls to see a directory listing.

Ones of interest off hand would be dmesg and messages.

You can type nano dmesg or vi dmesg (may need to use sudo instead).
thus, sudo nano dmesg or sudo vi dmesg

That might help in figuring out your problem.

Although, you may have problems with ACPI and have to try booting with noacpi appended to your startup line.

---

