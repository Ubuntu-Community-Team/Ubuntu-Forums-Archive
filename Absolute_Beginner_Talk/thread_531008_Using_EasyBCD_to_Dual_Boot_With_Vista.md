---
title: "Using EasyBCD to Dual Boot With Vista"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by dannymichel on 2007-08-21
What I did was install Vista FIRST then installed Ubuntu which installed GRUB over my Vista MBR. I then installed EasyBCD which is a program that manages the MBR and allows you to edit it via Windows. For some reason I can't get GRUB working properly via EasyBCD Add/Remove Entries>Linux/BSD>add Ubuntu GRUB. It adds itself fine in EasyBCD, but when I try and boot into Ubuntu it gives me some sort of error message.

---

### Post by mikeyphi on 2007-08-21
> **dannymichel said:**
> What I did was install Vista FIRST then installed Ubuntu which installed GRUB over my Vista MBR. I then installed EasyBCD which is a program that manages the MBR and allows you to edit it via Windows. For some reason I can't get GRUB working properly via EasyBCD Add/Remove Entries>Linux/BSD>add Ubuntu GRUB. It adds itself fine in EasyBCD, but when I try and boot into Ubuntu it gives me some sort of error message.

What is it you are trying to do with EasyBCD?

The MBR is the first sector on the Disk; the space is too small for any significant info so it is used to point to the address to load the OS. If you only have windows the it points to the Windows Boot file. After you installed Ubuntu the MBR points to Grub which gives the option to continue loading either OS.
So, what exactly do you need to edit?

---

### Post by bme on 2007-08-21
since you were able to get into vista from grub before you installed easybcd then your ubuntu/gub was working before this errors came up. you did not state your reason for installing easybcd which is just another bootloader which works from windows. I suggest you use the ubuntu live cd to reinstall grub and ditch easybcd......

---

### Post by mikeyphi on 2007-08-21
> **dannymichel said:**
> What I did was install Vista FIRST then installed Ubuntu which installed GRUB over my Vista MBR. I then installed EasyBCD which is a program that manages the MBR and allows you to edit it via Windows. For some reason I can't get GRUB working properly via EasyBCD Add/Remove Entries>Linux/BSD>add Ubuntu GRUB. It adds itself fine in EasyBCD, but when I try and boot into Ubuntu it gives me some sort of error message.

This guide might help:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Boot_Ubuntu_from_the_Windows_Bootloader](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Boot_Ubuntu_from_the_Windows_Bootloader)

---

### Post by Steve1961 on 2007-08-21
Grub needs to be installed to your root partition for easyBCD to work.

---

### Post by dannymichel on 2007-08-21
> **Steve1961 said:**
> Grub needs to be installed to your root partition for easyBCD to work.
How is this done?

---

### Post by Steve1961 on 2007-08-21
> **dannymichel said:**
> How is this done?

Boot from the live cd and identify your root partition:

sudo fdisk -l

This will list the partitions on your system - /dev/hda1, hda2, etc.  Grub uses a different notation so that /dev/hda1 would be (hd0,1), hda2 would be (hdo,1) and so forth.  Assuming you have Ubuntu installed to /dev/hda2:

sudo grub
root (hd0,1)
setup (hdo,1)
quit

---

