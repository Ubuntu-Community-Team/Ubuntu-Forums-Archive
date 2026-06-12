---
title: "Error 16"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by stephenson on 2006-03-29
Hello All, 
I have loaded ubuntu on my PC running XP pro.

unbuntu was loaded on a 80Gig slave drive,everything was install according to the install details but when the disc ejects and after configuring GRUB and the system shuts down to reboot, I get an "ERROR 16" message and the system doesn't boot. Any help will be greatly appreciated
Thanks

---

### Post by Iowan on 2006-03-29
[HERE]("http://www.uruk.org/orig-grub/errors.html") is a listing of GRUB errors and what they mean.  I realize it doesn't help get your system running, but: > 16 : "Device string unrecognizable"
This error is returned if a device string was expected, and the string encountered didn't fit the syntax/rules listed in the Filesystem Description.
 Or from [http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors]("http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors"):
> 16 : Inconsistent filesystem structure
This error is returned by the filesystem code to denote an internal error caused by the sanity checks of the filesystem structure on disk not matching what it expects. This is usually caused by a corrupt filesystem or bugs in the code handling it in GRUB. 
[Another]("http://ubuntuforums.org/showthread.php?t=99965&highlight=grub+error+16") thread that might help.

---

### Post by r4ik on 2006-03-29
To get your windows back,
Boot from cd choose R(recovery)
In step one the suggested default is oke.
Step two adminpasswrd if you got one type it and hit enter otherwhise just enter.

Command is  fixmbr aswer y(es) and hit enter again.

Abourt and reboot.

Good luck !

---

### Post by CameronCalver on 2006-05-17
Hey i have ubuntu and windows each on there own hd and sometimes it says error 16 and i cant get past grub how can i reinstall grub from install cd or live cd

---

