---
title: "Dual boot,does change the BIO?"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by David4 on 2007-04-13
Hi, am considering installing Ubuntu on a slave second HD, with Win on C drive,I think I understand the mechanics of setting it up,but will like to know more about where the "dual boot" resides, if at a later date I remove the second drive with Ubuntu, and return to a single C drive with Windows, will the "dual boot"remain or will just return to the "normal" windows boot?
thanks 
David

---

### Post by arochester on 2007-04-13
The bootloader is installed on the MBR (Master Boot Record) of the primary disk. If, at a later date, you remove the second drive you will need to "repair"/"fix"/"restore" the MBR. It is very easy to do and can be done by various means.

---

### Post by Seisen on 2007-04-13
This link should help you out and answer all of your questions.

[http://ubuntuforums.org/showthread.php?t=179902]("http://ubuntuforums.org/showthread.php?t=179902")

---

### Post by u04f061 on 2007-04-13
if u delete ubuntu drive then as for as i think your windows will remain unaffected but it would fail to boot because it won't find NT-Loader to boot the system. when you install a Linux system all of your OSs are booted by Grub boot loader or Lilo . on Ubuntu it is Grub. If some how you maintain Grub and its menu.lst file which tells it which OS to boot ,then it will be fine. But doing this is impossible because Grub as well as it menu.lst file are saved in Linux root directory. so doing so will erase Grub.

There is another solution to this problem. after u delete Linux(uninstall) as well as Grub ,u can recover Windows without any Loss of data except the one in your Linux Drive by inserting Win CD and choosing repair option instead of fresh install.
I hope i am right  but i am not sure

---

### Post by David4 on 2007-04-13
Thank you for your help.
arochester, you mention restoring the   MBR (Master Boot Record),found this link [http://www.tippscout.de/repair-and-restore-master-boot-record-mbr_tipp_3114.html](http://www.tippscout.de/repair-and-restore-master-boot-record-mbr_tipp_3114.html)
looks it may be more involved than it looks like, but is away to go.
thank you
David

---

