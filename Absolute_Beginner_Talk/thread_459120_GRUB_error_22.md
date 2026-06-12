---
title: "GRUB error 22"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by chria on 2007-05-30
Hi all

I am completelly new to ubuntu. I have installed it but I have problems whith GRUB. First of all I will explain who my HDDs are organized.

1. HDD extrernal USB
2. 1 SATA in channel 0. The partitions are: 1st Vista (NTFS), 2nd Boot(Ext3), 3rd root(Ext3), 4th Swap(Swap).
3. 1 SATA HDD (2 NTFS partitions)

When I try to boot, i get a GRUB error message 22. I enter in ubuntu or vista if only I press F12 key (while in POST), see the devices that I can boot and select the HDD that I have installed my operating systems.


I suppose I have to change something in GRUB files. Any idea?


Thank you in advance

---

### Post by plcdfa on 2007-05-30
It's not completely clear for me. So you have installed grub, ubuntu, and xp to you second hard drive. then why not set it the default (and only) boot device in your computer's setup?

---

### Post by Borzo on 2007-05-30
are you sure it's error 22?

---

### Post by psusi on 2007-05-30
I have no idea why you are getting a grub error because it sounds like your bios is just trying to boot from the wrong disk.  If telling it to use the correct disk works, then go into the bios setup and tell it to boot from that disk all the time.

---

### Post by rsambuca on 2007-05-30
Error 22 occurs when grub is looking for a drive that isn't there.  This usually happens because the order of the drives in grub is different than that of your bios.

Check the order that grub thinks the drives should be in a terminal:```
/boot/grub/device.map
```.

Check the boot order of your drives in the BIOS and make sure it matches.

---

