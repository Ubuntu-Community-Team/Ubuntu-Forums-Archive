---
title: "How can I tell if I completely erased Windows?"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by boriquajake on 2007-11-23
The answer is probably obvious but I really don't know if I completely erased XP from my laptop. How can one tell?

---

### Post by banewman on 2007-11-23
If you installed ubuntu after windows then at boot you will get a menu to choose which OS you want to run.
If you don't get that then put the live cd from ubuntu in and reboot. When it's running go to the menu and find "gparted". It is a partitioning program that will let you see the different partitions on your drive. If you didn't remove windows it will show up there. :)

---

### Post by overdrank on 2007-11-23
> **boriquajake said:**
> The answer is probably obvious but I really don't know if I completely erased XP from my laptop. How can one tell?

HI you can use this command in the terminal ```
sudo fdisk -l
``` and the output you can view and see if there is any ntfs file system. 
example

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3890    31246393+  83  Linux
/dev/sda2            3891       38889   281129467+   5  Extended
[COLOR="Red"]/dev/sda5            3891       16638   102398278+   b  W95 FAT32[/COLOR]
/dev/sda6           16639       16893     2048256   82  Linux swap / Solaris

No ntfs because I have no windows partitions. The fat file is just data.

---

### Post by mahiyar on 2007-11-23
It all depends on what you did to erase windows. There are a few pointers Ubuntu 7.1 has native ntfs drivers, open nautilus and look in each and every drive (like any other window drive) for the tell tale window files. Also you can do a quick >>sudo fdisl -lu if you see any NTFS partiton window is probably still there.

---

### Post by kellemes on 2007-11-23
> **boriquajake said:**
> The answer is probably obvious but I really don't know if I completely erased XP from my laptop. How can one tell?

Use Gparted or some other partition-editor to see if all NTFS-partitions (ergo Windows) are wiped. Assuming you're not using NTFS for some other reason except a Windows-install.

---

### Post by boriquajake on 2007-11-23
Thanks everyone. I checked and it is indeed all gone.

Any suggestions on where to download a copy of XP that I can use with the key that I have from the sticker on my machine?

---

### Post by LaRoza on 2007-11-23
> **boriquajake said:**
> 
Any suggestions on where to download a copy of XP that I can use with the key that I have from the sticker on my machine?

Please don't give an illegal responses here people.

---

### Post by boriquajake on 2007-11-23
> **LaRoza said:**
> Please don't give an illegal responses here people.

Oops, my bad. I didn't realize what I was asking was illegal. I only wanted a copy of windows to replace the one I lost. I would then activate it using the key on my computer. I thought it was legal. Sorry.

---

### Post by LaRoza on 2007-11-23
> **boriquajake said:**
> Oops, my bad. I didn't realize what I was asking was illegal. I only wanted a copy of windows to replace the one I lost. I would then activate it using the key on my computer. I thought it was legal. Sorry.

It would be (I think) but downloading it wouldn't be in all cases I believe. I realize you didn't ask for an illegal copy and intended to follow the EULA, but any torrents or links would point to illegal software.

---

### Post by MrFSL on 2007-11-23
> **boriquajake said:**
> Thanks everyone. I checked and it is indeed all gone.

Any suggestions on where to download a copy of XP that I can use with the key that I have from the sticker on my machine?

Windows XP has additional authentication other then entering the product code (key). You will either have to buy a new copy of Windows or go to the computer's manufacturer and request an installation CD.

---

### Post by kellemes on 2007-11-23
> **boriquajake said:**
> Oops, my bad. I didn't realize what I was asking was illegal. I only wanted a copy of windows to replace the one I lost. I would then activate it using the key on my computer. I thought it was legal. Sorry.

No problem..
It is rather confusing indeed, you have your key, you paid for it, so you think you own XP, not the case.. MS always finds new ways to your wallet.

---

### Post by aysiu on 2007-11-23
> **boriquajake said:**
> 
Any suggestions on where to download a copy of XP that I can use with the key that I have from the sticker on my machine? I'm sorry, but these forums do not support illegal activity.

---

