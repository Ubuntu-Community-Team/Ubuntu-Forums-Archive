---
title: "How to recover GRUB menu"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by surmandal on 2007-08-16
Previously I have installed XP first then ubuntu 7.04. It was working ...but now XP got crashed so i have reinstall XP on c: without formatting. Now I don't see any GRUB menu to go to ubuntu. So How can i recover it. Please help.

---

### Post by heimo on 2007-08-16
> **surmandal said:**
> Previously I have installed XP first then ubuntu 7.04. It was working ...but now XP got crashed so i have reinstall XP on c: without formatting. Now I don't see any GRUB menu to go to ubuntu. So How can i recover it. Please help.

See if this helps:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by ronmarley1 on 2007-08-16
Another option is the Super GRUB Disk.  [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by tgalati4 on 2007-08-17
Boot with the supergrub disk.

Hit "c" for command line:

>find /boot/grub/menu.lst
Hey, found something familiar at (hd0,0)
>root (hd0,0)
>setup (hd0,0)
>reboot (or control-alt-del)

It's late, and this is from memory, so you may have to tweak these instructions.

---

### Post by alienexplorers on 2007-08-17
Boot your live cd and start it.  Wait for it to boot and go to TERMINAL.  Enter sudo grub.
enter:
>find /boot/grub/stage1
enter:
>root (hd#,#)  replace #,# with your drive and partition you boot ubuntu from
enter:
>root (hd#) replace # with your drive
quit grub editor
reboot

---

### Post by surmandal on 2007-08-20
Well...I got the error message. Error says /boot/grub/stage1      grub not found. :( any idea ??? When I type /boot/ ant hit the tab twice it doesn't shows anythings. I mean there is no grub at /boot/ .

---

### Post by surmandal on 2007-08-21
Any Luck???

---

### Post by wonko on 2007-08-23
Maybe you, like me, have a separate partition for grub? In that case you have to search for /grub/stage1 only. At least it works for me...

---

### Post by daka58 on 2008-01-25
I'm a newbie. I installed Ubuntu 7.10 Minimal CD on a window XP. It just booted straight into XP (no ESC option). I've been reading different ways of using GRUB to modify Master Boot Record or Windows Boot Loader. I guessed I'm a little confused :)

I got the following:
============================

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5        9725    78083932+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf49c60bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30394   244139773+   c  W95 FAT32 (LBA)
/dev/sdb2   *       30395       60519   241979062+  83  Linux
/dev/sdb3           60520       60801     2265165    5  Extended
/dev/sdb5           60520       60801     2265133+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 
======================

Does that mean 
I don't have a boot file and
I installed Ubuntu in the F: (500 GB external drive) instead on C: ?

What I ultimately want to do is installed LiveCD in F: and have a dual boot option

Please help.
Thanks.

---

