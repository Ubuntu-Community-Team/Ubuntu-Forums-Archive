---
title: "Please please please HELP!"
date: 2005-12-03
forum: Absolute Beginner Talk
---

### Post by peter-the-pirate on 2005-12-03
Hi

To anyone who can help me here's the following:

My computer crashed and my OS (yes, it's XP....) won't boot up again, not even to dos. I don not have the orriginal XP CD, only the "Rescue disk" that came with my 6 (!) weeks old PC.
The problem is, I have about 50 gig of data (itunes et al) that I simply dont want to lose. So here is what I did, I downloaded Ubuntu Live CD and ran it in an attempt to do the following:

1. Copy my data to another (backup) drive
2. Use the rescue disk to format my first drive and reset it to "factory settings" (clean install of XP and other crap)

The problem is, ubuntu wont recognize my two HD's or I dont know how to find them in this OS! PLEASE! if anyone can tell me how to find them I'd appreciate it!
Other than installing ubuntu over my current f*&^ed up XP version (i dont know if that is possible) I dont want to make mr. gates happy by dishing out 200 bucks for a copy that I allready have somewhere on my computer!

Thank You!!!

---

### Post by trevorv on 2005-12-03
I think your best bet at rescuing data is to use Knoppix rather than Ubuntu, as it automatically puts your existing (Windows) partition onto the desktop, ready for access and rescue. As far as I can remember, the Ubuntu live CD does not, but it's been a while since I've run it on a PC with Windows.

---

### Post by Terry of Astoria on 2005-12-03
If the live CD has the same tools as the installer, it probably has a "disks" tool under the "system" "administration" menu.
From there I have been able to easily mount drives and partitions.

---

### Post by atoponce on 2005-12-03
[quote=peter-the-pirate]The problem is, ubuntu wont recognize my two HD's or I dont know how to find them in this OS! PLEASE! if anyone can tell me how to find them I'd appreciate it![/quote] 
So Windows XP won't boot period, and Ubuntu can't find your two hard drives?  Have the drives failed, or are they connected properly?  Are the drives SATA or IDE?  To locate the drives if they are IDE, pull up a terminal using the Ubuntu Live CD and type:

```
sudo fdisk -l /dev/hda
``` 
If SATA:

```
sudo fdisk -l /dev/sda
``` 
Once the drive is found, mount it using (if hda1 is your Windows drive):

```
sudo mkdir /windows
sudo mount /dev/hda1 /windows
``` 
From there, you should be able to rescue your Windows install using either the Ubuntu Live CD or the Windows resue disks that you have.

---

### Post by peter-the-pirate on 2005-12-03
[QUOTE=atoponce]So Windows XP won't boot period, and Ubuntu can't find your two hard drives?  Have the drives failed, or are they connected properly?  Are the drives SATA or IDE?  To locate the drives if they are IDE, pull up a terminal using the Ubuntu Live CD and type:

```
sudo fdisk -l /dev/hda
``` 
If SATA:

```
sudo fdisk -l /dev/sda
``` 
Once the drive is found, mount it using (if hda1 is your Windows drive):

```
sudo mkdir /windows
sudo mount /dev/hda1 /windows
``` 
From there, you should be able to rescue your Windows install using either the Ubuntu Live CD or the Windows resue disks that you have.[/QUOTE]

Thanks! Both drives are perfectly fine (up to the point where my windows crashed (lsass exe failure)
But I cant find the terminal. Does Ubuntu live have one? if so where? thanks again!

---

### Post by atoponce on 2005-12-03
[quote=peter-the-pirate]Thanks! Both drives are perfectly fine (up to the point where my windows crashed (lsass exe failure)
But I cant find the terminal. Does Ubuntu live have one? if so where? thanks again![/quote]

From the Gnome menu at the top-left:  Applications -> Accessories -> Terminal.

---

### Post by peter-the-pirate on 2005-12-03
ok i found a terminal!
This is what I got:

ubuntu@c-71-193-196-113:~$ sudo fdisk -l /dev/hda
 -note from user: so my IDE did not get recognized?
ubuntu@c-71-193-196-113:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 156.3 GB, 156394468864 bytes
255 heads, 63 sectors/track, 19013 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19013   152721891    7  HPFS/NTFS
ubuntu@c-71-193-196-113:~$ sudo mkdir /windows
ubuntu@c-71-193-196-113:~$ sudo mkdir /dev/hda1 /windows
mkdir: cannot create directory `/windows': File exists
ubuntu@c-71-193-196-113:~$
ubuntu@c-71-193-196-113:~$

---

### Post by peter-the-pirate on 2005-12-03
[QUOTE=peter-the-pirate]ok i found a terminal!
This is what I got:

ubuntu@c-71-193-196-113:~$ sudo fdisk -l /dev/hda
 -note from user: so my IDE did not get recognized?
ubuntu@c-71-193-196-113:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 156.3 GB, 156394468864 bytes
255 heads, 63 sectors/track, 19013 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19013   152721891    7  HPFS/NTFS
ubuntu@c-71-193-196-113:~$ sudo mkdir /windows
ubuntu@c-71-193-196-113:~$ sudo mkdir /dev/hda1 /windows
mkdir: cannot create directory `/windows': File exists
ubuntu@c-71-193-196-113:~$
ubuntu@c-71-193-196-113:~$[/QUOTE]
 
Also, i can see my two disks in the disks manager (system > administration > disks, but cannot open them

---

### Post by aysiu on 2005-12-03
[QUOTE=trevorv]I think your best bet at rescuing data is to use Knoppix rather than Ubuntu, as it automatically puts your existing (Windows) partition onto the desktop, ready for access and rescue. As far as I can remember, the Ubuntu live CD does not, but it's been a while since I've run it on a PC with Windows.[/QUOTE] This is sound advice. Please take it.

---

### Post by atoponce on 2005-12-03
[quote=peter-the-pirate]Also, i can see my two disks in the disks manager (system > administration > disks, but cannot open them[/quote]

Okay, so you have an SATA drive, rather than an IDE drive.  So, I noticed that you tried mounting an IDE drive to /windows.  Rather, you need to mount the SATA.  In your case, you should mount it as follows:

```
sudo mount /dev/sda1 /windows
```

---

