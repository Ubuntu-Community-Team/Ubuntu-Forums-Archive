---
title: "Can't boot XP from CD"
date: 2009-07-07
forum: Apple Hardware Users
---

### Post by stuartcnz on 2009-07-07
I have an early 2007 intel macbook with MAC OSX Tiger. I have successfully installed ubuntu 8.10.

I now have a need to run XP windows to be able to use Rhino CAD.

I bought leopard to use boot camp, managed to install XP, then replaced leopard with my existing Tiger set up, which works better for me. Then I reinstalled Ubuntu 8.10, which also works well for me. (I use a G3 modem to connect to the internet, which seems to be picky about my operating systems)

Once Ubuntu was back on my computer I lost the ability to boot into XP. I have resynced in rEFIt, but booting XP just hangs. When I try using the option key on start up I can start XP but it goes through GRUB and I have to select windows before ubuntu starts. When I do this, it tells me that hal.dll is missing or corrupt.

According to another post on this forum there used to be a way to fix this, but it no longer seems to work, needing a new reinstall of XP. So, using GParted I have reformatted the windows partition to FAT32, but now every time I try to boot from the XP CD, Ubuntu starts instead. 

How can I boot from the XP CD to reinstall and will it work if I do?

---

### Post by tiagobt on 2009-07-07
Could you post your current partition table?

---

### Post by stuartcnz on 2009-07-07
How do I do that?

I know that it is something like 1:EFI 200MB
                                 2:MacOS tiger 85GB
                                 3:FAT32 10.5GB
                                 4:Ubuntu 12.5GB
                                 5:linux swap 500ish MB

---

### Post by tiagobt on 2009-07-07
Ubuntu seems to change the MBR, causing Windows to stop booting. What you could do is backup the MBR before installing Ubuntu, and then restore it later on.

Before that, however, you have to reinstall Windows XP, making it work again. You should be able to boot the CD by holding the "option" key as the computer starts up (rEFIt usually reads the CD as well, showing an extra boot option). Then you should be able to install Windows XP normally.

When Windows XP starts working again, do the following:

[LIST=1]
[*]Before installing Ubuntu, boot the live CD and make a backup of the MBR:
```
sudo dd if=/dev/sda of=/tmp/sda.mbr bs=512 count=1
```

[*]The backup will be placed in the **/tmp** folder. I recommend you copy this file to a safe place, like an external drive.

[*]Install Ubuntu normally, placing GRUB on the Linux root partition. This can be done by using the advanced installer options. In your case, you should place GRUB in **/dev/sda4** (or **hd0,3** in GRUB notation).

[*]When the installation is done, restore the backup:
```
sudo dd if=/tmp/sda.mbr of=/dev/sda
```
[/LIST]

If that doesn't work, there's something else you could try. But I'm not sure how reliable this information is. Some users report that Windows XP "likes" to be the last partition in the MBR (/dev/sda4). If this is really the case, your partition table should be something like follows:

[LIST]
[*]**(hd0,0) /dev/sda1** - EFI
[*]**(hd0,1) /dev/sda2** - Mac OS X
[*]**(hd0,2) /dev/sda3** - Ubuntu <-- GRUB should go here
[*]**(hd0,3) /dev/sda4** - Windows XP
[*]**(hd0,4) /dev/sda5** - Swap
[/LIST]

I hope that helps,
Tiago

---

### Post by stuartcnz on 2009-07-08
So, does that mean I will have to reinstall Ubuntu as well? Even though it is working fine at the moment.

---

