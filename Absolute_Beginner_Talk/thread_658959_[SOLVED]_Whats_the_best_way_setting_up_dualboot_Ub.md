---
title: "[SOLVED] Whats the best way setting up dualboot Ubuntu/XP"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by orky87 on 2008-01-05
Hello to you all,
Guys tell me
What's the Best/Easiest way of  setting up my dual boot,
I have my UbuntuStudio 7.10 & WinXP SP2,
what should I do first, should I create partitions or should I install one of the OS's so on.
I have no data that's important so deleting my hard drive is no problem.
I want to have most of my 230gb hard drive formatted to FAT32 at 150gb as Shared Folder 
Thanks...

---

### Post by Crumpets and Jam on 2008-01-05
> **orky87 said:**
> Hello to you all,
Guys tell me
What's the Best/Easiest way of  setting up my dual boot,
I have my UbuntuStudio 7.10 & WinXP SP2,
what should I do first, should I create partitions or should I install one of the OS's so on.
I have no data that's important so deleting my hard drive is no problem.
I want to have most of my 230gb hard drive formatted to FAT32 at 150gb as Shared Folder 
Thanks...

Install which ever operating system you like first. Then follow one of [these guides]("http://apcmag.com/node/5162/") depending on which operating system is on your hard drive.

---

### Post by ubutufan on 2008-01-05
You need not waist FAT32 space. It is not safe for your files

GUTSY supports NTFS read/write. That will get you going for safe storing your files with ubuntu+windows

---

### Post by bumanie on 2008-01-05
Generally, it is an accepted practice to install windows first, that way you don't have the hassle of reinstalling grub. If ubuntu is installed first, windows will overwrite the mbr and grub won't work (although it can be reinstalled). Whereas if ubuntu is installed after windows, grub should be setup straight away. You can install either way but windows installed first is generally a little easier. Also windows is happier if it is the first OS on the first hdd.
As far as partioning goes, you could allocate 'x' amount to xp at install and then allocate what you need for ubuntu with the partition editor during the ubuntu install.
My understanding of modern ubuntu is that you don't necessarily need a FAT32 for a shared /home, as ntfs can be accessed from ubuntu and there is an open source program (can't remember the name) that can be installed in windows that allows access to the ubuntu file system. Also, as you are using 7.10, I believe the ntfs-3g program is installed natively and you should be able to read and write to windows from within ubuntu.
Another thing to consider is using something like vmware or virtual box to run one OS in a virtual environment - whether you have enough resources to do this adequately depends on your system.
I would carefully check all these things to see which one suits your needs best, before committing to anything.

---

### Post by hyper_ch on 2008-01-05
Have a read here, that explains most of it:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

And first install windows, then Ubuntu

---

### Post by Torqumada286 on 2008-01-05
If you have more than one HD, you could install Ubuntu on one and Windows on the other, like I have.

Torqumada

---

### Post by ubutufan on 2008-01-05
I agree that you should install XP first and Ubuntu second.
I do not agree that you should use GRUB as your bootloader. Both the windows bootloader and or GRUB work fine.
If you decide to use GRUB then everything posted here is fine. If not and you want to use the windows bootloader then follow the instuctions of this excellent post
[http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/)

In raelity it is up to you to decide. Last comment is that GRUB is much more easily configured. Nothing wrong with windows bootloader but more time consuming.

---

### Post by orky87 on 2008-01-06
Guys thanks a lot great info you all doing a great job  keep up the good work.
Cheers...

---

