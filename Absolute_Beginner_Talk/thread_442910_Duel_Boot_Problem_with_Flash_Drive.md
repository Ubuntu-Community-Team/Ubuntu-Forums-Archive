---
title: "Duel Boot Problem with Flash Drive"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by Cuz314 on 2007-05-14
I'm a total newbie to Linux and installed Ubuntu 5.10 to a 4 gig flash drive. Everything seemed to be going fine until the end when it recognized my Windows XP operating system and asked if I wanted a duel boot. I said yes and now if the flash drive is not plugged in I can't boot up and when it is in I can't boot into Ubuntu. I use this computer for work so i need to be able to boot with having to depend on the flash drive and secondly, I would still like to be able to use Ubuntu on the flash drive. If I boot using the Live CD I can see the flash drive and root on the desktop. Any help would be appriciated. Thanks

---

### Post by geekphreak on 2007-05-14
It sounds like you might have installed grub onto the flash drive. Here's what I would do:
 - boot off of XP CD, go to recovery console and restore XP loader
 - get 7.04 and install that
 - pay attention about the grub location next time around

---

### Post by Cuz314 on 2007-05-14
Thanks, I was the Repair Console earlier today and don't recall seeing anything about an XP Loader. Is that a seperate command or is it the same as FixMBR or bootcfg?

---

### Post by confused57 on 2007-05-14
> **Cuz314 said:**
> Thanks, I was the Repair Console earlier today and don't recall seeing anything about an XP Loader. Is that a seperate command or is it the same as FixMBR or bootcfg?
Looks like you installed grub to your internal hd mbr, here's how to restore your Window's mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
if you have a Window's install cd, boot with it in your cd drive, press "r", & you need to enter the FIXMBR command.

To get your flash drive working, you'll need to install grub to the flash drive mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Then boot first to your flash drive & hopefully you'll get a grub boot menu, highlight your Ubuntu entry, press "e", change root from (hdx,y) to (hd0,y), then press "b" to boot...this is temporary, but if it works you can make it permanent.

Added:  Here's a recent thread with someone who was trying to get their external hd booting Ubuntu:
[http://ubuntuforums.org/showthread.php?t=439411](http://ubuntuforums.org/showthread.php?t=439411)

---

