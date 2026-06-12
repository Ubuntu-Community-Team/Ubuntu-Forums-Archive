---
title: "Restoring GRUB"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by deatheater on 2008-04-17
Hi initially i had XP on my machine,then i installed ubuntu 7.10 on that machine.it worked smooth.for some region i need to install a fresh copy of XP and i did it.but now the boot control process is in XP's hand.
so can anyone pls guide me how to restore GRUB so that i can have a option menu for selecting OS.that ubuntu is still installed on my system just i want GRUB on my mbr.

pls help me out.
Thanks in advance

---

### Post by bumanie on 2008-04-17
Can you please post the output of > sudo fdisk -l

---

### Post by philinux on 2008-04-17
Windows has taken back control of your mbr, master boot record. This is normal but not nice.

You need to restore grub using the live cd.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by northern lights on 2008-04-17
When you (re)install Windows,it overwrites your entire Master Boot Record and GRUB is gone. There are several ways to recover / set it up again. All documented [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

---

### Post by Biggy on 2008-04-17
download [Super Grub Disk]("http://supergrub.forjamari.linex.org/")

---

