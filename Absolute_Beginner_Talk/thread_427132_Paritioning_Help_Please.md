---
title: "Paritioning Help Please"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Vish555 on 2007-04-29
Hi everyone, need a bit of help with partitioning. I 've read that ubuntu cna be installed onto a logical drive but i've been told that it must be put on primary.

This is my current disk management layout: [http://img152.imageshack.us/img152/8533/diskmanagementtz5.png](http://img152.imageshack.us/img152/8533/diskmanagementtz5.png)

Can someone guide me as to where i should install ubuntu. Thx.

Any suggestions would be great. Thx in advance.

Vish

---

### Post by mikeyphi on 2007-04-29
Looked at your setup....when you install Ubuntu it will ask if you are happy to use all your 'free space' ...accept the option and let the installer do the rest!!!  You will have a dual boot grub allowing you to choose your OS at bootup.....enjoy!!!

---

### Post by zvacet on 2007-04-29
Install it on the free space.When you come to the partition stage do like this:
1.root =10GB                         mountpoint  /
2. home =rest exept              mountpoint  /home
3.swap =1GB

---

### Post by Vish555 on 2007-04-29
> **mikeyphi said:**
> Looked at your setup....when you install Ubuntu it will ask if you are happy to use all your 'free space' ...accept the option and let the installer do the rest!!!  You will have a dual boot grub allowing you to choose your OS at bootup.....enjoy!!!


What about the bootloader? Won't there be a conflict because both os's will be installed on the same extended partition but just in logical drives?

---

### Post by riminicat on 2007-04-29
Microsoft does conflict with the bootloader, I made a rescue cd before I installed, and then put grub on the same partition as I put Ubuntu, just in case Microsoft screwed it up.  Microsoft messed up the boot loader and then i put the rescue cd in and got into either os that way

---

### Post by mikeyphi on 2007-04-29
> **Vish555 said:**
> What about the bootloader? Won't there be a conflict because both os's will be installed on the same extended partition but just in logical drives?

No!! The bootloader will be GRUB - this will give you a text screen after power on allowing you to choose which OS to boot. It won't cause any other changes to your present system.
Have a look at what the installer offers - if you don't like it you can abort without any problems.

---

### Post by Vish555 on 2007-04-29
if grub is installed, what happens to the mbr? And if grub doesn't work, how will i get the mbr back? Thx for the quick reply. :)

---

### Post by mikeyphi on 2007-04-29
> **Vish555 said:**
> if grub is installed, what happens to the mbr? And if grub doesn't work, how will i get the mbr back? Thx for the quick reply. :)

The mbr is overwritten by GRUB.
If you decide to uninstall Ubuntu just use your previous windoze system disk and boot into recovery mode.....type fixmbr

---

