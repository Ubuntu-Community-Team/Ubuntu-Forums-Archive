---
title: "Double Linux with rEFIt"
date: 2008-09-29
forum: Apple Hardware Users
---

### Post by Kooothor on 2008-09-29
Hi macusers,

I have a nice dualboot Arch/Mac with rEFIt and I want to install Ubuntu also.

The problem is with the GRUB. I want to have two separate grub and the choice with rEFIt.

so I tried (alternate CD) the normal install with grub installed on my ubuntu partition (sda5)
But couldn't boot in neither of my linux OSs

My HD looks like this :

#1 /dev/sda1 EFI (mac bootloader) 200 Mo
#2 /dev/sda2 Léopard (mac apps) 150 Go
#3 /dev/sda3 Archlinux WITH GRUB boot loader 50 Go
#4 /dev/sda4 FAT32 Data exchange 283 Go
#5 /dev/sda5 I WANT TO PUT UBUNUTU HERE 18 Go
#6 /dev/sda6 swap for both distros 1 Go 
#7 /dev/sda7 I tried to install /boot here, but it didn't work either.

Anyone can help me out with this problem ?
thx :D


~ktr


PS : I guess the next post will come from Cyberdork33 :mrgreen:

---

### Post by kosumi68 on 2008-09-29
> 
#5 /dev/sda5 I WANT TO PUT UBUNUTU HERE 18 Go


sda5 is outside the four basic partitions, which might be a problem for the current grub. Quite generally, I am having problems with grub on partitions, I have settled with using the master boot record. Once installed there, booting into several distros using the /grub/menu.lst is of course not a problem.

---

### Post by cyberdork33 on 2008-09-29
> **Kooothor said:**
> #1 /dev/sda1 EFI (mac bootloader) 200 Mo
#2 /dev/sda2 Léopard (mac apps) 150 Go
#3 /dev/sda3 Archlinux WITH GRUB boot loader 50 Go
#4 /dev/sda4 FAT32 Data exchange 283 Go
#5 /dev/sda5 I WANT TO PUT UBUNUTU HERE 18 Go
#6 /dev/sda6 swap for both distros 1 Go 
#7 /dev/sda7 I tried to install /boot here, but it didn't work either.

Anyone can help me out with this problem ?
thx :DIt sounds like you have most of the info right. Let's go through this.

#1 Just terminology... The EFI partition is not where the bootloader is (it is in firmware). It is only a partition that is part of the EFI spec. There is actually nothing in there (unless you are performing a firmare update).

#2 looks good

#3 looks good if there is no separate boot partition for this install. Grub should be installed to this partition (which it sounds like you did).

#4 we'll get back to this one

#5 Unfortunately, since this is not one of the first four partitions, it will not be available to grub to boot. grub uses the MBR table, and it is limited to four partitions on a mac. (this is also the reason why having /boot on #7 will not work either.)

#6 is fine!

Here is my suggested change:

1 EFI
2 OSX
3 Arch
4 Ubuntu
5 FAT32 Storage
6 Swap

If you really need to have a /boot partition, you can make the boot partition #4, and the root partition can go anywhere. So something like:

1 EFI
2 OSX
3 Arch
4 /boot (for Ubuntu)
5 FAT32 storage
6 Ubuntu root
7 swap

> **Kooothor said:**
> PS : I guess the next post will come from Cyberdork33 :mrgreen:... didn't make it... almost though

---

### Post by volanin on 2008-09-29
> **cyberdork33 said:**
> Here is my suggested change:

1 EFI
2 OSX
3 Arch
4 Ubuntu
5 FAT32 Storage
6 Swap

This is a nice suggestion, but also remember that you can safely put OSX
beyond the 4th partition with no problems. This would free up one extra
MBR partition for you to experiment with.

But it might mean reinstalling OSX though.
:(

---

### Post by cyberdork33 on 2008-09-29
> **volanin said:**
> This is a nice suggestion, but also remember that you can safely put OSX
beyond the 4th partition with no problems. This would free up one extra
MBR partition for you to experiment with.

But it might mean reinstalling OSX though.
:(
yep

You can apparently map the 4 MBR partitions to any partition in the GPT, but this is a little advanced...

[http://ubuntuforums.org/showthread.php?p=4896559#post4896559](http://ubuntuforums.org/showthread.php?p=4896559#post4896559)

---

### Post by Kooothor on 2008-09-30
Ok thx for your replies all, 

That's what I thought, I remember having read somewhere that you have to be in the first four partitions....

I think I'll swap my fat32 and a linux. Thx :D

---

### Post by jenitta on 2008-09-30
I think it is a great site to know about the Double Linux with refit I want to install ubuntu but I was facing problem so I tried the normal installation with grub installed on my ubuntu partition I was able to installed thanks for the information

______________________________________

[Houston Best Florist](http://www.florist-flowers-roses-delivery.com/texas/houston_tx.html) [loans with no credit check](http://www.cheaponline-loans.co.uk/help/no-credit-check-loans.php) [pisos vilafranca](http://www.vilafrancadelpenedes.com/-1/posts/1_Habitatge/0/) [download iPhone ringtones](http://www.myringtoneshub.com/specials/buy-cell-phone-ringtones.htm)

---

### Post by Kooothor on 2008-10-01
Ok, I've done some moves into my HD :

/dev/sda1 EFI
/dev/sda2 Apple Leopard partition
/dev/sda3 openSUSE
/dev/sda4 Arch + grub with dual boot Arch/openSUSE
/dev/sda5 swap
/dev/sda6 FAT32 BUT I can't manage to get rid of the marker "microsoft reserved" and so this partition isn't usable.... :(

I tried with gparted live CD, but there is still the tag "mrsftrvd" or something like this...

I think I can manage to get rid of it with the Arch partitionner...

[BTW openSUSE rocks concerning hardware detection !](http://ubuntuforums.org/showthread.php?p=5886304#post5886304)
Can you believe the backlight of the screen was actually tunable out of the box with F1 and F2 ??? !! oO
A load of things are detected nicely, you should give it a try !

---

### Post by volanin on 2008-10-01
> **Kooothor said:**
> /dev/sda6 FAT32 BUT I can't manage to get rid of the marker "microsoft reserved" and so this partition isn't usable.... :(

I tried with gparted live CD, but there is still the tag "mrsftrvd" or something like this...

Just right-click the partition in gparted and choose "Manage Flags"
Unset mrsfrvd and you should be ready to go!
:)

---

### Post by Kooothor on 2008-10-01
> **volanin said:**
> Just right-click the partition in gparted and choose "Manage Flags"
Unset mrsfrvd and you should be ready to go!
:)

Yeah I tried that, didn't work.

---

### Post by cyberdork33 on 2008-10-01
> **Kooothor said:**
> Yeah I tried that, didn't work.
This might be relevent:
[http://www.macosxhints.com/article.php?story=20080130022147512](http://www.macosxhints.com/article.php?story=20080130022147512)

---

### Post by Kooothor on 2008-10-01
> **cyberdork33 said:**
> This might be relevent:
[http://www.macosxhints.com/article.php?story=20080130022147512](http://www.macosxhints.com/article.php?story=20080130022147512)

Yeah, I bumped into this post already, but it isn't clean.
It's just a workaround, and I can't "select the partition", it doesn't exist for Disk Utility.

I once manage to have a fully useful FAT32 partition, but now.... :(
Damned you M$ !!! :(
I'll try with cfdisk of the Arch install CD, I think it was with that utility that I managed to have a working partition.

---

### Post by cyberdork33 on 2008-10-01
> **Kooothor said:**
> I'll try with cfdisk of the Arch install CD, I think it was with that utility that I managed to have a working partition.
fdisk (which cfdisk is based on) does not edit the gpt. parted in the only GNU tool that does (that I am aware of) which is what gparted is based on. You could try deleting the partition with gparted and recreating it in diskutility...

---

### Post by Kooothor on 2008-10-01
> **cyberdork33 said:**
> try deleting the partition with gparted and recreating it in diskutility...


Yeah, I'll try that.

---

### Post by johndavid_9696 on 2008-10-11
Most have problems with the grub on partitions. Using master boot record is the solution. I think EFI, OSX, Arch, Boot, FAT32 storage, Swap, Ubuntu root. Double linux with rEFlt is safe mode.


============================================================

john


[Downtown Florist](http://www.florist-flowers-roses-delivery.com/california/los_angeles_ca.html)

---

