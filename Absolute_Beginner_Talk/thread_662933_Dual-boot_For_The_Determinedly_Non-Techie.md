---
title: "Dual-boot For The Determinedly Non-Techie"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by sloe gin on 2008-01-09
Hi - I am totally non-techie - have never typed a line of code. If I bought this laptop

[http://www.novatech.co.uk/novatech/specpage.html?NNB-580](http://www.novatech.co.uk/novatech/specpage.html?NNB-580)

with the Windows xp option

Would I be able to load Ubuntu as a dual boot?
And would the machine be friendly to it?

I've had a look at the stickies above and they're just opaque to me, nevertheless the ultimate aim is to ween myself off Windows and I see the dual boot as a safe half-way rusk. Have you good people got Ubuntu ready for fools like me or should I wait a bit?

---

### Post by Pevichaey5 on 2008-01-09
ubuntu is ready for anyone :D

when u boot from the live cd, it doesn't mess around with your files on your hard drive

when the install part is running, it will give you the option of shrinking your windows section  (which is the best option for you) and you move the slide bar to how ever much you want for linux

you can download a copy of ubuntu [here](http://www.ubuntu.com/getubuntu/download)

---

### Post by Hightide on 2008-01-09
Hi
If you are used to windows XP I would go for a dual boot. I have XP and Gutsy dual as my kids use XP alot.

Its quite simple to do. 

1. Download the Gparted live onto a cd  from here [http://download.tuxfamily.org/gpartedlive/](http://download.tuxfamily.org/gpartedlive/)

2. Boot from Live CD and follow instructions to partition your disk.

3. After, insert your Ubuntu CD, follow instructions and install on unallocated free space.

It will install the boot menu (GRUB) for you giving you the options to choose XP or Ubuntu

:)

---

### Post by sloe gin on 2008-01-09
Christ that was quick! Thanks folks. Guess the thing to do is get the lappy and then sook it and see.

---

### Post by eriqjaffe on 2008-01-09
Or, if you want to be really cautious about it, you can use [WUBI]("http://wubi-installer.org/"), which will let you dual-boot Ubuntu via a standard Windows installer.

---

### Post by sloe gin on 2008-01-09
Hmmmmm. That looks interesting. Thanks Eriq. Wonder if Bill Gates uses it?

But I'll buy the lappy first.

---

### Post by esteckis on 2008-01-09
Also, I am still using XP as my daily use while I get used to Ubuntu, I highly recommend startup manager so you can set the default load will be XP  but you can always pick Ubuntu whenever you startup your computer.

---

### Post by mister_pink on 2008-01-09
You could try out the live CD for a bit on your current computer if you want to see what you think. 

Also, I don't think anyone here has really had a proper look at the laptop you're planning on buying, including me. I don't really know much regarding laptop hardware support but basically ubuntu will work on at least 90% of systems without any trouble, and the other 10% will require some work to get absolutely everything working, and most common issues seem to be wireless and graphics chipsets. Check out the wiki and compare it to the system you're buying 
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) 
That won't list everything that works but its a starting point.

Edit: Just had a look, I don't think the graphics card is an issue, and since it doesn't list the wireless details you don't have much choice. On the off chance that you're unlucky it's normally pretty easy to fix with a bit of community support from here!

---

### Post by sloe gin on 2008-01-09
Thanxs guys. Looks like if the system turns out to be a plonker I can always turn to you for another way of looking at it.

---

### Post by twin_57103 on 2008-01-09
Here is a link that may be helpful in finding out the hardware compatibility: [https://wiki.ubuntu.com/]("https://wiki.ubuntu.com/")

After you get the laptop, run the live CD a couple times to be sure everything works right.  There are varying opinions on this issue, but I don't think you need anything but the Ubuntu disk itself for this installation.  It will help you partition your drive without extra software or options that could be confusing.  

The installation process is straightforward.  You will need to decide on partitioning - how to separate the physical drive into segments for Windows and Linux.  Many people also set up an additional "data partition" to act as a go-between for the two system.  This is optional but often convenient.

Post-installation, you will need to do a fair amount of configuration.  Synaptic is the "package manager" of Linux - the way you install software.  To configure options, open Synaptic, then select Settings...repositories.  I'd recommend checking main and universe, and possibly restricted drivers, depending on the video card.  You may wish to select multiverse at a later date, but start with those three.  Universe implies software that is free, but not in the Ubuntu core set.  Restricted drivers are not open-source (a core Ubuntu value), but except for open-software idealists, most people don't mind.  Software that is not in the repositories (that you have to download and install from sources other than Synaptic) is often difficult to install and may be less stable.

You don't need antivirus for Linux alone, but if you're dual-booting, it's a wise choice.  ClamAV is in the repositories and is the main antivirus choice for Linux.

If you use a 5-button mouse, you'll need to configure it.  You will need to do some additional configuration for multimedia, as well (this is not default because of the free & open source software ideals of Ubuntu).  There are a lot of great how-to's on [https://help.ubuntu.com/]("https://help.ubuntu.com/"), and, as you've discovered, by searching and/or posting on these forums.

A couple definitions that may come in handy: 
Live CD: the Ubuntu CD is bootable and will run the entire operating system directly from the CD.  This is a great way to try it out and to be sure it works well with the hardware.

GRUB/boot loader: GRUB is the bootloader, which helps the two operating systems work together.  You will get a screen when you boot that gives you a chance to select Windows of Linux.

Nautilus: the equivalent of Windows explorer

Terminal: somewhat similar to the command prompt in Windows, but more powerful - in Windows, the command prompt has fallen to the wayside; in Linux, it is integral and powerful.
There are a lot of great threads that will give other software parallels.

Above all, be patient.  Linux is a learning process if you've never used it before.

Oof...I'm long-winded.  I hope that helps and isn't boring!

---

### Post by Sef on 2008-01-09
Read [Psychocat's Installing]("http://www.psychocats.net/ubuntu/installing") or the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/") or both.

---

