---
title: "Ubuntu 12.10 for Macbook pro late 2008"
date: 2012-11-23
forum: Apple Hardware Users
---

### Post by october490 on 2012-11-23
Hello people !

I have a Macbook pro late 2008, with 2.4 GHz Intel Core 2 Duo processor, 64 bit and 2 GB RAM.
It was very fast with the OS 10.5 but now with the OS 10.8.2 it's simply crawling !
I don't want to spend money in hardware upgrades, so I am thinking of installing Ubuntu.
I'd like your help re the following issues:

1. Which version of Ubuntu 12.10 shall I get : 32 bit or 64 bit ?

2. Shall I make a dual boot system with Mac OS and Ubuntu ? In this case, will I be able to use my files and media already stored in the Mac partition? 
And also, will Ubuntu work smoothly with the hardware in this Macbook (wifi, RAM size, dvd etc )

3. Or shall I use Ubuntu directly from the DVD without installing it in the hard drive and doing risky procedures like partitioning ? 

Thank you very much !

PS: I have also the option to re-install Mac OS 10.5, but I have work before with Ubuntu 8.10 in my old desktop and I like the idea of kicking out Apple from my laptop ! :P

---

### Post by howefield on 2012-11-23
Thread moved to the "*Apple Users*" forum.

---

### Post by zaebo on 2012-11-23
1)
Your decision.
I have also a core 2 duo, and as it is capable of 64bit, I decided to go for Ubuntu 64bit. 

2)
Since I have a MB late '09 I can't tell you if everything works. But you can find out by booting the live-cd and watch for yourself.
Under 10.04 and 12.04 different repositories, like mactel, helped me to solve different problems, e.g. with bad wlan connectivity.

The RAM size depends on what you are planning to do. 
You can try out first and then see if you need to upgrade. RAM doesn't cost much these days.

You can read your HFS+ partition from Ubuntu. Although you have to do something to read system folders, but that should be easily googl-able.

For 12.04, I recently set up my macbook new. I always like to keep a little mac partition. I never really used it, but for some reason I can't tell, I like to have it.
Ah. And I always install rEFIt when installing Ubuntu. For that you need Mac OS. But there are different ways of installing Ubuntu, and I think rEFIt isn't needed.

3)
If you are happy with Mac 10.5 or 10.6, than just run Ubuntu via VM. If you want to run it nativley, because you don't have much RAM and/or don't want to upgrade it, than install it natively.

Helpful links:
[https://help.ubuntu.com/community/MacBook]("https://help.ubuntu.com/community/MacBook")
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Quick_Steps]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Quick_Steps")

---

### Post by 2F4U on 2012-11-24
I have a MacBook early 2008 with similar specs than yours.

> 1. Which version of Ubuntu 12.10 shall I get : 32 bit or 64 bit ?

You can run both. 64 bit consumes a bit more RAM, but else both run very well.

> 2. Shall I make a dual boot system with Mac OS and Ubuntu ? In this  case, will I be able to use my files and media already stored in the Mac  partition? 
And also, will Ubuntu work smoothly with the hardware in this Macbook (wifi, RAM size, dvd etc )


This is totally up to you. Ubuntu 12.04 supports the MacBook and everything works out of the box. While you can access the Mac partition from Ubuntu, it is always recommended to make a backup of your data before attempting to install a new OS.

---

### Post by october490 on 2012-12-04
Thank you for your replies and help but I ...stuck on step 1  !!!!

I tried to download ubuntu 12.10 and the ubuntu site has only the ubuntu 12.10.386. iso.
When I burn it on a dvd my mac simply doesn't recognise it !
Is there an easy way to download ubuntu in a mac-friendly format ( ? dmg ? img I don't know...).
Because I tried to follow the instructions and convert the .iso to .img (I think...) and I simply wasn't able to handle the information - unfortunately I am not a pc/mac specialist !

---

### Post by trogdor1138 on 2012-12-05
If at all possible, I would highly recommend partitioning and dual-booting. While this may sound scary, it's really not that bad.

It's easiest to do this if you use Boot Camp. Although provided with the intent of running Windows, Boot Camp works equally well for running Linux. Boot Camp consists of three things:

- An OS X utility used to partition your drive
- Apple-provided drivers for Windows, also accessible through the above utility
- A BIOS emulation mode to support functions required by Windows and other BIOS-based OS's

In your case, you would:

- Boot Mountain Lion as normal, then go to Applications > Utilities > Boot Camp Assistant

- Walk through the guided process. The utility will repeatedly mention Windows, but that's fine and you can ignore it. You'll have options to download drivers and burn a CD; you don't want to do either of these

- Using Disk Utility, burn the appropriate ISO to a DVD. You want the special EFI-less version for Apple computers, available here: [http://releases.ubuntu.com/quantal/ubuntu-12.10-desktop-amd64+mac.iso](http://releases.ubuntu.com/quantal/ubuntu-12.10-desktop-amd64+mac.iso)

- Once you've burned the above image, put it in your drive, reboot your Mac, and hold the option key once you hear the chime

- Once the boot menu loads, select the "Windows" disc by clicking it. Your Mac will show "Windows" for any BIOS-based operating system, so this is normal

- Follow the regular Ubuntu install steps

For more information, this wiki page is written by the team responsible for supporting Intel Macs: [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

---

