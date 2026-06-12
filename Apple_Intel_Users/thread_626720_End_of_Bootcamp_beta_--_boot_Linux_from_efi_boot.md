---
title: "End of Bootcamp beta -- boot Linux from efi boot?"
date: 2007-11-29
forum: Apple Intel Users
---

### Post by thouters on 2007-11-29
Hi,

I have a first-gen macbook, and have been running linux on it since I first bought it (a year ago, before that I used gentoo on an iBook for a year). 
I'm so in love with GNU/Linux/Ubuntu I can't realy remember when last time was I booted OSX.

These days the media trumpeted much about how the end of the Bootcamp beta phase would mean the end of booting mac's into anything other then OSX without upgrading tho the latest MacOS.

This has made me nervous, fearing that one day my macbook would refuse booting into GRUB through rEFIt/bootcamp.

So here comes my question; is it possible to boot into Ubuntu using rEFIt and GRUB with efi patches?
This way I wouldn't have to obtain/buy the new bootcamp/OSX.
I'm thinking of removing OSX from my laptop, but haven't yet because I'm not taking the risk of messing with my current setup.  I don't have the time to spend fixing things, if something goes wrong.

Another relevant question: do GNU tools (fdisk come to mind) support the efi partition system?

ps: sorry for the typo in the topic but I hit the enter key next to the right apple key (hitting enter in the subject form submit's the post???). Subject should be "End of Bootcamp beta -- booting Linux with grub-efi/rEFIt?"

---

### Post by cyberdork33 on 2007-11-29
> **thouters said:**
> I have a first-gen macbook, and have been running linux on it since I first bought it (a year ago, before that I used gentoo on an iBook for a year). 
I'm so in love with GNU/Linux/Ubuntu I can't realy remember when last time was I booted OSX.

These days the media trumpeted much about how the end of the Bootcamp beta phase would mean the end of booting mac's into anything other then OSX without upgrading tho the latest MacOS. You will not be able to use the boot camp utility anymore. That is all that is expiring. Boot Camp has nothing to do with the actual multi booting of your machine. That is all up to the firmware. You should have no trouble booting into linux even after the expiration of bootcamp. Also, the partitioning aspect of bootcamp is just a GUI. It is really using a commandline tool to resize your partition. [http://www.macgeekery.com/tips/cli/nondestructively_resizing_volumes](http://www.macgeekery.com/tips/cli/nondestructively_resizing_volumes)

> So here comes my question; is it possible to boot into Ubuntu using rEFIt and GRUB with efi patches?This is possible, but it is still buggy, and not recommended (you currently lose 3D capability).

> I'm thinking of removing OSX from my laptop, but haven't yet because I'm not taking the risk of messing with my current setup.  I don't have the time to spend fixing things, if something goes wrong.several people here do that already.

> Another relevant question: do GNU tools (fdisk come to mind) support the efi partition system? The partition system is called GPT (GUID Partition Table). fdisk does _**NOT**_ support GPT. parted and gparted do though.

---

### Post by volanin on 2007-11-29
> So here comes my question; is it possible to boot into Ubuntu using rEFIt and GRUB with efi patches?

Well... well...
I have a Macbook 3rd generation for about 3 months now.
I have never used BootCamp in my life, and always booted Ubuntu normally via rEFIt+GRUB, without any patches at all, and with full-3D on the Intel Card.

For me, it just works!
Is there so many differences between the 1st gen and 3rd gen that borks this?
:)

---

### Post by cyberdork33 on 2007-11-29
> **volanin said:**
> Well... well...
I have a Macbook 3rd generation for about 3 months now.
I have never used BootCamp in my life, and always booted Ubuntu normally via rEFIt+GRUB, without any patches at all, and with full-3D on the Intel Card.

For me, it just works!
Is there so many differences between the 1st gen and 3rd gen that borks this?
:)
No, sorry... he was referring to booting via EFI natively (i think). This is possible to do (via elilo or grub 2), and will likely be the way to do things in the future, but right now we are using Apple's built in BIOS emulation to boot Ubuntu in Legacy mode. This probably won't change until someone figures out how to initialize graphics properly, or Apple releases specs about the EFI system.

You can continue to use rEFIt and Grub to dual boot just like you likely have been.

---

### Post by thouters on 2007-11-29
> **cyberdork33 said:**
> You will not be able to use the boot camp utility anymore. That is all that is expiring. Boot Camp has nothing to do with the actual multi booting of your machine. That is all up to the firmware. You should have no trouble booting into linux even after the expiration of bootcamp. Also, the partitioning aspect of bootcamp is just a GUI. It is really using a commandline tool to resize your partition. [http://www.macgeekery.com/tips/cli/nondestructively_resizing_volumes](http://www.macgeekery.com/tips/cli/nondestructively_resizing_volumes)

This is possible, but it is still buggy, and not recommended (you currently lose 3D capability).

several people here do that already.

 The partition system is called GPT (GUID Partition Table). fdisk does _**NOT**_ support GPT. parted and gparted do though.

Thank you!

---

### Post by tehkain on 2007-11-29
I installed normally as if using a normal legacy bios system and the latest firmware allows the system to use a normal MBR setup.

Note that I wiped my drive(including the efi partition) clean, no OSX to be found.

---

### Post by nielsb on 2007-11-30
For the OP; as so many others have stated on this thread - BootCamp is not necessary when booting into Ubuntu on a Mac based system. The only reason for BootCamp (for Ubuntu) was to shrink volumes in order to create partition(s) for Ubuntu. For Windows you also used BootCamp to obtain drivers for the Mac specific stuff (such as iSight etc).

I've been running Ubuntu for a while on my 1:st gen MB and I have never touched BootCamp. If you are dual-booting with OSX (or rather you have OSX on your box), you do need rEfit though.

Now:
> **tehkain said:**
> I installed normally as if using a normal legacy bios system and the latest firmware allows the system to use a normal MBR setup.

Note that I wiped my drive(including the efi partition) clean, no OSX to be found.
The above is absolutely possible (as the poster says), but just be ware that if you wipe OSX totally, you are out of luck when Apple releases firmware upgrades.

Niels

---

### Post by thouters on 2007-11-30
Wouldn't it be possible to keep osx on a firewire disk, and boot from it for (firmware)upgrades?

---

### Post by nielsb on 2007-11-30
> **thouters said:**
> Wouldn't it be possible to keep osx on a firewire disk, and boot from it for (firmware)upgrades?
I assume - basically I have no clue - that you in that case still would need an EFI partition on the Mac. But as  said, I am not sure, so if someone knows - please fell free to pipe in.

Niels

---

### Post by cyberdork33 on 2007-11-30
> **thouters said:**
> Wouldn't it be possible to keep osx on a firewire disk, and boot from it for (firmware)upgrades?
yep. There are several doing that as well. You just need to make sure you have an EFI partition on the disk. I think that OSX will create one if it is not there when you start out from a clean disk.

---

### Post by Grey Box on 2007-11-30
You don't even need bootcamp to resize your partitions. Gparted will resize the HFS partition even when the OS X install disk refuses (without destroying your data, of course).

---

### Post by maluka on 2007-12-01
what is the best way for me to completely wipe the disk free of any trace of osx on my mbp? will wiping it and reformatting the disk to a linux compatible file system essentially turn my machine into a standard pc?

---

### Post by cyberdork33 on 2007-12-01
> **maluka said:**
> what is the best way for me to completely wipe the disk free of any trace of osx on my mbp? will wiping it and reformatting the disk to a linux compatible file system essentially turn my machine into a standard pc?
not quite, but if you are asking if you can just run Ubuntu by itself, yes.

---

### Post by phenexfire on 2008-05-02
I just read all the goodies on this posting and I hope someone might tell me what I should try doing to install ubuntu on this thing.

I have an intel mac mini with 100 gig hdd and 1 gig of ram.
I want to install ubuntu server and have the latest lts version downloaded. I don't care about graphics I want to use this as a mini server.

based off what I have read here I am getting that I should be able to wipe the HDD clean and install the server edition on here and it will boot?

I tried an older ubuntu server version and I could not get it to work no matter what I did, even with refit. so I miay have messed up. Can someone maybe give me a step by step of what they did to get server edition installed?

thanks

---

