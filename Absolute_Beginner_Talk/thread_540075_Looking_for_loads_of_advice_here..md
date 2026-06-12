---
title: "Looking for loads of advice here."
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by Lifes Victim on 2007-09-01
Here it goes:
I have an AMD Turion64 processor, so if I were to download Ubuntu 7.04, I would install Desktop > 64bit AMD computers, right?
I write that .iso image on to a blank CD. 
Am I able to dual boot both Ubuntu and XP with just one hard drive? If so, steps for doing this?
I tried out the Feisty Live CD and couldn't get the desktop enhancements to activate when I went to that option, do I need specific hardware to do this? Maybe I have the hardware, I just don't know how to do this. Would installing all the updates and packages help this?
Could anyone provide me with a tutorial on learning how to fully use a terminal?
Also, could you provide me with links to any sites that are essential for beginning Linux users?
I am an avid player of a game called Guild Wars; I have heard of something called "Wine," is this what I would need to install it onto Ubuntu and play it there? If not Wine, then what would do it?
Anything else I should need to know?

I'm devoting the next.. Say, 24+ hours straight to reading up on this version of Ubuntu and trying to find out as much as I need to know and hoping to fully install Ubuntu and all of the updates & packages I can. Would much appreciate if someone could answer a lot of these questions for me, looking way eager to doing this. So exciting for me. :-D

If you need to know anything about my hardware specs or anything just let me know and I'll tell you.

---

### Post by aitorcalero on 2007-09-01
> **Lifes Victim said:**
> Here it goes:
I have an AMD Turion64 processor, so if I were to download Ubuntu 7.04, I would install Desktop > 64bit AMD computers, right?
Yes right

> I write that .iso image on to a blank CD. 
Exactly

> Am I able to dual boot both Ubuntu and XP with just one hard drive? If so, steps for doing this?
Ubuntu installation takes care of this autmatically. No need to worry, it will install an OS boot loader called GRUB

> I tried out the Feisty Live CD and couldn't get the desktop enhancements to activate when I went to that option, do I need specific hardware to do this? Maybe I have the hardware, I just don't know how to do this. Would installing all the updates and packages help this?

I think that hardware acceleration (which is needed to desktop enhancements) is not configured with live cd, but when you install ubuntu on hard disk it detects your video card and it will work, but to make sure maybe you could look for your video card ubuntu compatibility

> Could anyone provide me with a tutorial on learning how to fully use a terminal?
Look for "basic commands linux" in google, wikipedia, etc...

> Also, could you provide me with links to any sites that are essential for beginning Linux users?
You are now in the best site ;), but again search for it in google

> I am an avid player of a game called Guild Wars; I have heard of something called "Wine," is this what I would need to install it onto Ubuntu and play it there? If not Wine, then what would do it?
Anything else I should need to know?
You could check in WINE's site if this game is supported, if it is not, you can check out CEDEGA (but it is commercial software by subscription) or just boot Windows to play this game, maybe the best option if you have this game already installed.

> If you need to know anything about my hardware specs or anything just let me know and I'll tell you.
You may also check for yourself about your hardware compatibility in google or just searching this forum.):P

---

### Post by sumguy231 on 2007-09-01
> I have an AMD Turion64 processor, so if I were to download Ubuntu 7.04, I would install Desktop > 64bit AMD computers, right?
You can install the 64-bit version if you want, but I hear it's a pain to get 32-bit only proprietary software (like Flash) to work right. I wouldn't know from personal experience though. If that doesn't sound fun to you you can always use the 32-bit version.(64-bit peeps, correct me if I'm wrong. I can't afford such things as 64-bit processors!)
> I write that .iso image on to a blank CD. 
Right. Make sure you actually use the function of your CD burning application which specifically mentions writing the ISO to a disk, as opposed to just putting the .iso file on a data cd and burning it. The former will work, the latter will do nothing.
> Am I able to dual boot both Ubuntu and XP with just one hard drive? If so, steps for doing this?
Yep. That's the most common way to do things. Here's a generic guide, though there's probably a better one that someone else will mention:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
> I tried out the Feisty Live CD and couldn't get the desktop enhancements to activate when I went to that option, do I need specific hardware to do this? Maybe I have the hardware, I just don't know how to do this. Would installing all the updates and packages help this?
All you need is: a.) a decent video card and b.) the right video drivers. The video drivers you need probably don't come with Ubuntu, but will be easy to install once you've installed Ubuntu. This depends on what card you have.

> Also, could you provide me with links to any sites that are essential for beginning Linux users?
I am an avid player of a game called Guild Wars; I have heard of something called "Wine," is this what I would need to install it onto Ubuntu and play it there? If not Wine, then what would do it?
Anything else I should need to know?
Wine will run some Windows applications, but not all. There's a list of apps and how compatible they are here:
[http://appdb.winehq.org/](http://appdb.winehq.org/)

You could also look at Cedega, which is like Wine but focused more on gaming.


> I'm devoting the next.. Say, 24+ hours straight to reading up on this version of Ubuntu and trying to find out as much as I need to know and hoping to fully install Ubuntu and all of the updates & packages I can. Would much appreciate if someone could answer a lot of these questions for me, looking way eager to doing this. So exciting for me. :-D
Learning is good. :)

> If you need to know anything about my hardware specs or anything just let me know and I'll tell you.

---

### Post by dsauxier on 2007-09-01
32 vs 64-bit install.  Short answer-go with the 32-bit install unless you're an advanced user.  It will run fine, and you'll get over the nagging thought that you're wasting some of the horsepower (I've got a Turion 64 also, and I've gone back and forth between 32 and 64 bit a few times).

Yes, you write that .iso image (whichever you choose) on to a blank CD.

You can dual boot with just one hard drive, but you'll need to partition the disk.  Be sure to back up anything you care about because a mistake will wipe out your data.  Do you know if your partitions are FAT32 or NTFS?  My Acer Aspire 5003wlci laptop was set up with 3 FAT32 partitions - a small recovery partition, the windows partition and a data parition.  I just took the easy route, and split up the data partition for linux use (using a Knoppix CD)

The desktop enhancements may require a graphics card with 3D acceleration.  You may have one, but need proprietary drivers installed.
Can you post your laptop make/model?
Also, try checking the LaptopTestingTeam : [https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam)
If you're lucky yours (or similar model) will be on the list.
If it's not on the list, I strongly encourage you to document your results and put it on the list.

Installing all the updates and packages are not likely to help that specific situation.

What else you should know : 
You may need to connect the hardwired ethernet to download drivers for your wireless.
The sheer magnitude of choice is one of the greatest assets linux has to offer.  If you don't like a program (nautilus for example), find something else (I prefer emelfm)

I'll leave these for someone else:
Could anyone provide me with a tutorial on learning how to fully use a terminal?
Also, could you provide me with links to any sites that are essential for beginning Linux users?
I am an avid player of a game called Guild Wars; I have heard of something called "Wine," is this what I would need to install it onto Ubuntu and play it there? If not Wine, then what would do it?

---

### Post by Lifes Victim on 2007-09-01
Okay, I'm trying to take all this in and remember it. I'm going to do the beginning steps first. So right now I'm going to install it with the dual boot. Then I'll come back on once I get it loaded to answer questions and tell if you it worked. Thank you so much. :-D

---

### Post by mlentink on 2007-09-01
> **Lifes Victim said:**
> 
Could anyone provide me with a tutorial on learning how to fully use a terminal?

[www.linuxcommand.org](www.linuxcommand.org)

---

### Post by Lifes Victim on 2007-09-01
> **dsauxier said:**
> 
Can you post your laptop make/model?


It's an HP Pavilion dv8000, and it is on the list. So what would I need to install to enable these features?

---

### Post by dsauxier on 2007-09-01
According to the documentation I just looked at, that model has ATI's Radeon Xpress 200M graphics card... While I'm not familiar with that particular card, I know that the ATI cards do require the proprietary drivers to get full performance capabilities.

AFTER making a backup of your /etc/X11/xorg.conf file, you can try the instructions here [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) ... it may or may not work (your model is not listed as working).  If your video is toasted by this, then simply replace the modified xorg.conf with the backed up one.

---

### Post by DeepNoob on 2007-11-08
"It's an HP Pavilion dv8000..."

So is mine, and I was pleased to see that 7.10 supported my hardware out of the box.  I don't use wireless, so can't speak about that.  After you burn the ISO, boot from it and take a look around.  You should get a feeling about how compatible the hardware is.

If you have free space on your HD, or can make some in Windows, the install process will probably be less confusing if you create two empty, non-formated partitions: one for the OS and one for swap, about 1GB.  During installation choose "manual", not "guided" when laying out the partitions, and assign the large partition to "/" and the 1GB partition to "swap."

The dual boot mechanism (grub) will be installed transparently.

Should be pretty painless for you.  Good luck.

---

### Post by Robocoastie on 2007-11-08
Do yourself a favor and order from Amazon (or nearby bookstore) the latest edition of "Linux Cookbook" published by O'Reilly. 90% or more of any question you have as you learn Linux you can find in that book. The Ubuntu Wiki is also your best friend. The latest 7.10 x64 handles codecs, flash, and even wine marvelously now so don't be afraid to go for 64 bit.

Don't worry about Windows gaming for now, you have enough to learn about native Linux apps and methods first. So just boot to WinXP when you want to game. You could even run 32 bit Ubuntu in a Virtual machine if you have enough RAM, there's a version available freely using VMWare's appliance, or VirtualBox. In fact I recommend just running it in a VM until you get the hang of it and feel that you can start using it exclusively.

---

