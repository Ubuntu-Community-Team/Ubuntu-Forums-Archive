---
title: "iMac G4 Hangs on 7.10 Live CD boot"
date: 2007-11-07
forum: Apple PPC Users
---

### Post by evdjj3j on 2007-11-07
When I try to boot the 7.10 live cd the cd starts to boot, says creating ramdisk, shows some text on the screen then hangs with a frozen cursor in the upper left corner.  The Ubuntu splash screen never shows.

---

### Post by kugn on 2007-11-08
at the boot prompt you need to type live-nosplash-powerpc. the splash screen is the problem. see [http://ubuntuforums.org/showthread.php?t=579487](http://ubuntuforums.org/showthread.php?t=579487) for further details.

---

### Post by evdjj3j on 2007-11-08
I tried live-nosplash-powerpc, and it gets me further than before, but I then get dumped into busy box.  Once in busy box I type modprobe ide-core, press enter type exit, enter, and get the following error message.

BusyBox _ _ _ Built-in shell (Ash)

(initramfs) modprobe ide_core
(initramfs) exit

cp: unable to open 'root/var/log/' : No such file or directory
mount: Mounting /root/dev/.static/dev failed : No such file or directory
mount: Mounting /sys on/root/sys failed : No such file or directory
mount: Mounting /proc on/root/proc failed : No such file or directory
Target filesystem doesn't have /sbin/init

Back to BusyBox

I have tried modprobe ide-core and modprobe ide_core, still nothing.

Its seems as thought the cdrom is getting lost and it cannot continue to boot.

---

### Post by pxwpxw on 2007-11-08
Try also 
 modprobe ide_disk

---

### Post by stmiller on 2007-11-09
See [this thread]("http://ubuntuforums.org/showthread.php?t=581280") for a fix. I know it sucks that the Gutsy PowerPC isos were finalized with this problem remaining. The bug report remains unassigned to anyone. :(

---

### Post by Ububurns on 2007-11-12
I have run into the exactly the same problem. What a pain!  I have been hanging out for Gutsy!

Unfortunately I am unable to contribute further.  I have been trying for about an hour, with numerous combinations of "solutions" in other threads.

stmiller, the thread you refer to only seems to apply to people who have upgraded their systems - not just using a live / installer cd.

Surely SOMEONE has the live CD working!

---

### Post by Ububurns on 2007-11-14
ONE WORKING SOLUTION:

- Install Gutsy using alternative (text-based) CD
- After install, first reboot will drop to Busybox, where "modprobe ide_core" -> "exit" will boot the system.

From here on, the method for fixing the system can be taken from the link stmiller posted.  Good luck!

---

