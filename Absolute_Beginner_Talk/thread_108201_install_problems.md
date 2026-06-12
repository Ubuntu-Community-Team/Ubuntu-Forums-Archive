---
title: "install problems"
date: 2005-12-25
forum: Absolute Beginner Talk
---

### Post by Snaaky on 2005-12-25
Ok, I've been trying too install ubuntu with a dual boot with windows. I've installed windows and am now trying too install ubuntu on a different hard drive. (My windows hd is a sata drive and I have a amd64) I work through the installation and partition the hd for the swap partition and a main partition. I then continue to install. It gets to a point where it installs grub and then wants to restart and boot from the hard drive. The first time I tried it it booted into windows, and the second time I just got an error and wanted me to insert a system disk. I've tried playing with the boot settings in bios but it doesn't seem 2 make any difference. Does anyone know what would cause this? Maybee I'm setting up the partitions wrong?

Thanks for any help.

---

### Post by odin on 2005-12-26
Not sure about this one but try mkaing the partition where you installed ubuntu active

---

### Post by bscbrit on 2005-12-26
I'm not sure what has happened here but I do have a few observations and then a few stark questions.

When you install Grub it defaults to starting Ubuntu in preference to any Windows installation that it can find.  So the fact that it tried to start Windows rather than Ubuntu is a bit disconcerting - it should have at least tried to start Ubuntu.

The request that the computer wants a system disk means that it hasn't found an operating system anywhere.  That doesn't sound too good....but the computer might just be confused.

Q1 - are you _sure_ that you installed ubuntu to your 2nd drive?

Q2 - have you removed the CD and tried to reboot again?  if so, what exactly did you see?

Q3 - do you want to try to install it again?

---

