---
title: "Where does GRUB reside?"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Songwind on 2007-03-16
I am already looking ahead to the time when I will take windows off of my computer completely, and want to recover my windows drive space.

Currently I have a SATA hard drive (120Gb) split about evenly between Kubuntu and Windows XP Pro.  XP was on the system first, and is on SDA1.  Kubuntu is installed on SDA5 (long story, involving misunderstanding the partition resizing capabilities of GParted).  My swap is SDA3 or whatever, on the end of the drive.

My question is, where is GRUB located?  Is it on SDA5 with Linux?  Or is it at the front of SDA1 (the first partition on the drive)?  If it's on SDA5 I should be able to delete SDA1 and reformat it as ext3 with impunity, right?  And then move my home directories onto it or something.

If it's on SDA1, does anyone know of a how-to or tutorial for removing SDA1, recreating it at ext3, and getting GRUB back in action without having to reinstall Kubuntu?

Thanks,
Eric

---

### Post by jhenager on 2007-03-16
Should be on the boot sector of hard disk 0, unless I'm mistaken.

---

### Post by spd106 on 2007-03-16
Hi,

Chances are grub is in both places. By default grub installs into the Master Boot Record which is in the first few sectors of the hard drive. As this area is too small to be of much use so it also adds a second stage to the beginning of the linux partition that you want to boot. As long as the MBR is pointed to the right boot partition you will be ok to boot.

I suggest you have a read through this wiki page for some background and useful instructions [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto). I will also be useful to keep a live/desktop cd handy in case you need to reinstall grub. This process will not necessarily require that you reinstall the whole of Ubuntu, though you will probably need to use the grub-install program via a terminal.

---

