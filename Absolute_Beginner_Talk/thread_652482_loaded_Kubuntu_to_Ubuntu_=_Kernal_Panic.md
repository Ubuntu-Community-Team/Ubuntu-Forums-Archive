---
title: "loaded Kubuntu to Ubuntu = Kernal Panic"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by nynoah on 2007-12-28
I installed Kubuntu and when rebooted, I got a Kernal Panic.  I went into the recovery mode and it said that my root system has some fatal errors and that I should run a fsck check.  Tried that and then it told me to do a e2fsck.  This gave me a whole bunch of options.  I just rebooted from there and came to you all.  

What is going on?

Noah

---

### Post by tinycamp on 2007-12-28
try booting with a livecd and check the partition table status with fdisk, BE CAREFUL

if you get to access your drive and you have info there, BACK UP RIGHT AWAY

what boot manager are u using, grub? try to reinstall grub

good luck

---

### Post by nynoah on 2007-12-28
Yes I have a live disk.  I don't care if I lose anything on the computer.  There is nothing on there to loose.  I already lost my other system and I am trying to rebuild this one.  I have set my home drive to a seperate partition and that was working fine.  I loaded Ubuntu studio back on.  No problem there, other than I had problems with my graphics drivers.  Did a work around to the Vesa driver and reinstalled my Nvidia driver after downloading something I was told to download from synaptic.  

Then I later loaded on Kubuntu and Wham..........kernal panic.......

So what should I do now.  I am not sure how to do all that from the live disk.  I do have some decent ubuntu knowledge.   I am writing from my laptop right now too.

so what should I do from the live disk?

N

---

### Post by nynoah on 2007-12-28
I typed:  *sudo fdisk -l*  and it all looks good to me so far

how do I reinstall grub?

---

### Post by nynoah on 2007-12-28
I think it has something to do with my usplash theme......how can I update that from the live cd?

---

### Post by tinycamp on 2007-12-29
if you can mount the system partition from the live cd, do this:

if the partition is mounted on /media/disk do:

```
chroot /media/disk
grub-install /dev/hda <---- or hdb, sda, this should be the bootable partition

```you can remove the splash config at /boot/grub/menu.lst, look for the boot command and configure from there..... i think...

good luck

---

