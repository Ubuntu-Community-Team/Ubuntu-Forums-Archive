---
title: "grub problem"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by webofunni on 2007-02-28
I am using ubuntu 6.06 dapper drake with windows xp in a duel boot system. The main problem i faced with ubuntu is related to booting. When ever there is some changes related to partition and hardisk my grub get corrupted. If i changes my file system in windows from fat32 to ntfs i will stuck with grub error 15 when i restart the s/m. Also if i split any partition or merge any of them i will get error. I the final option that will apply is to reinstall ubuntu to recover my grub. But i got many options like super grub cd, installing grub from live cd etc..
But these options will not make the grub to identify those changes that i make with harddisk.

My recent problem related to grub is that. I had a usb drive (kingston data traveler 512 MB) When ever i start my system with this usb drive connected i will get a blank screen with a blinking cursor at the top instead of grub menu. So i had to remove the usb drive and to restart for getting the grub menu. 

I tried to install grub from live cd with usb connected with the hope that grub installation will adjust itself to boot with usb connected but it disappointed me

also i used grub fix in super grub cd but that also doesn't work

I need a solution for installing grub so that new installation will scan my system and will configure itself with new changes that i made. I will explain more -- Like when we install ubuntu the ubuntu installer will scan all the drives and other operating systems and will configure grub according to that---Is there any method other that installing ubuntu again that will install grub like the ubuntu installer does

--thanks in advance:)

---

### Post by Herman on 2007-02-28
> I need a solution for installing grub so that new installation will scan my system and will configure itself with new changes that i made. I will explain more -- Like when we install ubuntu the ubuntu installer will scan all the drives and other operating systems and will configure grub according to that---Is there any method other that installing ubuntu again that will install grub like the ubuntu installer doesIf you have the 'Alternate' Ubuntu installation CD, you can                                                               [Re-install GRUB (with Alternate CD Rescue mode)]("http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub")
> The main problem i faced with ubuntu is related to booting. When ever there is some changes related to partition and hardisk my grub get corrupted.I suspect that may be due to the filesystems' UUID numbers being changed. Have you tried running 'sudo update-grub? That would be quicker, see if that helps you, ```
sudo update-grub
```I'll try that out for myself later today. If that doesn't yet have the fuctionality to re-detect UUID numbers you may have to edit your /boot/grub/menu.lst manually.

Probably your /etc/fstab file will need to be updated each time too,                      [About Edgy Eft's new /etc/fstab files with UUID filesystem ID added]("http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with")

It would be nice if there was a program called 'update-fstab' too, when I learn how to code I will write a program for that , he-he :)

Anyway, I hope that helps.
Regards, Herman :)

EDIT: Oh, yeah, one more thing, [Partitioning Tools ( And which ones not to use )]("http://www.brunolinux.com/04-The_File_System/Partitioning_Tools.html")

---

