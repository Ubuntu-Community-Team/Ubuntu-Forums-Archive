---
title: "Grub error message: Error 17 : Cannot mount selected partition"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by Topes_the_one on 2007-10-02
I am sorry for bringing this topic up again.  I have followed the other threads and am still lacking the insight to make the changes to get grub to boot without the "error 17" message.

I have a three drive system.  Two sata drives and one ide drive.  The ide drive is partitioned with NTSF and FAT32.  The first sata drive is WinXP and the second sata is Ubuntu 7.04 Feisty Fawn.

I can boot from Super Grub to Ubuntu. I have tried to repair grub using Super Grub and then boot without Super Grub, alas with the same message. Here is the out put from my menu.lst with my edits:
  title   windows xp
  root   (hd1,0)
  map  (hd0) (hd1)
  map  (hd1) (hd0)
  map  (hd0) (hd2)
  map  (hd2) (hd0)
  map  (hd1) (hd2)
  map  (hd2) (hd1)
  chainloader (hd1,0)+1

With this setup, I get the same error message booting Ubuntu but I can boot into windows.

I will stay at this until I find a way without using Super Grub to boot into Ubuntu.

Any help will be much appreciated.

---

### Post by djchandler on 2007-10-02
Seems as though GRUB has been clobbered on SATA(0) [XP] drive.

One other thing to check is your BIOS. Is it possible to change the boot Hard Disk? Maybe GRUB is on SATA(1). If you change your BIOS for the boot drive to match your [Ubuntu] drive, that could do the trick. Not elegant perhaps, but a workaround.

DJ

---

### Post by multifaceted on 2007-10-02
From what I understand, GRUB is owned by whichever file system location was used to install it. If you changed the location of the file system the boot loader goes to, it will give Error 17.

Recently happened to me, I got frustrated and just reinstalled.... was a cleaner install and went rather quick.... about an hour for set up and UI configuration. Kind of glad I had to, lol!

Mine however, was a result of partition editing... deleted something I knew I shouldn't have....

You live and you learn!

:popcorn:

---

