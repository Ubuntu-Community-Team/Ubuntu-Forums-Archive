---
title: "Linux n00b needs help setting up an Ubuntu partition on a MacBook."
date: 2008-12-03
forum: Apple Hardware Users
---

### Post by Quantum Anomaly on 2008-12-03
Hi all. I am new to Ubuntu, but it seems I must install an Ubuntu partition on my MacBook to run Blender because of a three-way EPIC FAIL between Blender, Leopard, and the Intel GMA graphics chips of the earlier plastic MacBooks. 

I know this is like a twenty-something step process and I'm afraid I'm going to break my computer while setting this up.

Can those who have ventured in this territory please illuminate the path for me?

First of all I'm not sure how to find the proper download page for my particular MacBook as I understand each model is different. 
Here are the specs:
[SIZE="1"]Black MacBook 2.4GHz Intel Core2Duo (mid 2008)
4GB RAM
250GB hard drive
Intel GMA X3100 graphics chipset (the cause of my woes)
OS X 10.5.5 build 9F33[/SIZE]

Forgive me if this kind of post is redundant but I am feeling lost.
Thanks
QA

---

### Post by Kobalt on 2008-12-03
Hello,

For your MacBook, you can download the 64bit edition of the Ubuntu Desktop CD.
One way to handle the partitioning and cohabitation of the two OSes on a Mac is to use BootCamp. You'll create a partition wichi you'll use for Ubuntu, and at startup you'll press the Alt button in order to select which OS you want to boot.

This is IMHO the simplest way.

---

### Post by MaddMatt on 2008-12-03
> **Kobalt said:**
> Hello,

For your MacBook, you can download the 64bit edition of the Ubuntu Desktop CD.


That is not necessarily true- I run 32 bit just fine. I don't think there is any additional reason why you should choose 64 bit over 32 bit just because you are installing on a MacBook. [This article]("http://ubuntu-tutorials.com/2007/11/26/32bit-vs-64bit-ubuntu-that-is-the-question/") has some of the differences that you should consider between the two: the reason I haven't yet is because of the greater program base for 32, but the main reason to switch to 64 bit is to increase the user base, and facilitate the change... I plan on switching to 64 bit on my non-mac tower soon, but I just wanted to make it clear that 64 bit is NOT a prerequisite. 

Either way, installing on a macbook is not difficult. 
If you got it in 2008, then it's likely 4,1 - "Penryn" architecture. There is a whole wiki that has instructions to get your new install tip-top, so I recommend you look at the Penryn wiki here: 
[https://wiki.ubuntu.com/MacBookPro/Penryn]("https://wiki.ubuntu.com/MacBookPro/Penryn")

Essentially just partition using Bootcamp, and install normally. 

Some people (myself included) find that bootcamp doesn't detect linux 100% until you use Refit, an alternate Mac bootloader. You can find that here: [http://refit.sourceforge.net/]("http://refit.sourceforge.net/")

It also gives you nice icons, and has a configuration file that allows you to default to Linux (legacyfirst option) rather than OS X. 

If you have issues, don't hesitate to ask. 
Welcome to the club, and have fun!

M

PS- if you are a linux 'n00b' as you say, you are probably going to want to install the medibuntu suite - it enables you to play DVDs and other things on your kicking laptop - [http://www.medibuntu.org]("http://www.medibuntu.org")

---

### Post by skullmunky on 2008-12-03
The one thing to pay attention to when you install, which I missed the first four times I tried it, is the part of the Ubuntu instal :)lation where you choose where to install Grub, the boot menu.  Just pay attention to the option for choosing the partition for Grub.  It has to be the same one as your Linux partition, but the default is to put it on the first partition, which won't work.

---

### Post by cyberdork33 on 2008-12-03
See the "Before You Post" link in my signature to determine how to properly identify your Mac and how to find documentation for your particular version.

---

### Post by Quantum Anomaly on 2008-12-04
Thanks for the helpful replies!

I am just looking at this page:
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
and it lists 24 different steps to setting up Ubuntu on a MacBook. It's a bit daunting. 

I have 58GB of drive space left. I'll probably want 10GB for the Blender (and GIMP?) files I'll be making in Ubuntu. How much would I need to run the Ubuntu OS itself? My friend mentioned I would want to designate 8GB (double my RAM) for a swap disk for writing temporary files...is this necessary? Would I need more than my 4GB of RAM? Because I don't want to use up more drive space if I don't need to, but I will if it will greatly improve Blender's performance.

If it ends up not working out, how difficult is it to uninstall Ubuntu, erase the partition, and get everything back into one partition for OS X to utilize 100%?

---

### Post by Quantum Anomaly on 2008-12-04
OK, more questions still:

How is rEFIt different from BootCamp? 

Where does Grub come into play?

What's the difference between Gutsy and just regular Ubuntu?

---

### Post by cyberdork33 on 2008-12-04
> **Quantum Anomaly said:**
> Thanks for the helpful replies!

I am just looking at this page:
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
and it lists 24 different steps to setting up Ubuntu on a MacBook. It's a bit daunting.
Well, first, that may or may not be the document you want to follow depending on which Macbook version you are working with... Second, The "installation" is taken care of in part one of that page. The other items are various configuration changes and hardware fixes that you really only need to consult if you have a problem with any of those items. 

> **Quantum Anomaly said:**
> I have 58GB of drive space left. I'll probably want 10GB for the Blender (and GIMP?) files I'll be making in Ubuntu. How much would I need to run the Ubuntu OS itself? My friend mentioned I would want to designate 8GB (double my RAM) for a swap disk for writing temporary files...is this necessary? Would I need more than my 4GB of RAM? Because I don't want to use up more drive space if I don't need to, but I will if it will greatly improve Blender's performance.
You do not need 8GB of swap, that is a bit excessive. The rule of thumb was 2x RAM but that is really not neccessary anymore. Here is my quick install method that will handle creating your swap partition for you. To start off, I would use Bootcamp to create a 30GB partition for Ubuntu. This will give plenty of space for your working files, the OS, software, and an appropriate swap partition.
[http://ubuntuforums.org/showpost.php?p=6211925&postcount=2](http://ubuntuforums.org/showpost.php?p=6211925&postcount=2)

> **Quantum Anomaly said:**
> If it ends up not working out, how difficult is it to uninstall Ubuntu, erase the partition, and get everything back into one partition for OS X to utilize 100%? It can be a bit awkward, but, basically, you should be able to boot the Ubuntu LiveCD, run gparted and delete the Ubuntu and Swap partitions. Then you can boot into OSX and use DiskUtility to resize your OSX partition to use the free space.

> **Quantum Anomaly said:**
> How is rEFIt different from BootCamp? 
rEFIt is just a pretty interface for the EFI bootloader in your Mac. It also has some nifty tools that can be useful for installation. It is not necessary to use rEFIt once you have everything installed the way you want.

> **Quantum Anomaly said:**
> Where does Grub come into play?
Grub is the Linux bootloader. It loads the kernel into memory. Windows also has a bootloader though you usually never see it. OSX can be booted directly by the EFI firmware. You will install grub as part of your Ubuntu installation. See the post I linked to above.

> **Quantum Anomaly said:**
> What's the difference between Gutsy and just regular Ubuntu?
Gutsy (actually the full name is Gutsy Gibbon) IS "regular" Ubuntu. It is just a specific release. The newest release (and the one you should use) is version 8.10 (AKA Intrepid Ibex).

---

