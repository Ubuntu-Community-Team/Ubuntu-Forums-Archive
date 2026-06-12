---
title: "Completely clueless with this odd install..."
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by Imsati on 2007-10-16
A few weeks ago, I obtained a new MoBo (ECS 945GZT-M) and Ubuntu stopped working. Upon trying to reinstall it, the X-server wouldn't start from the Live CD. The only thing different from my old board was the PCI-E slot. My old board was x16 and this one is at x4. Well, I experimented with some other MoBo's (both with full x16 speeds) and the Live CD booted right up. On a whim, I tried the ECS board again and the Live CD worked. Unfortunately in the process, I fried my spare HDD I decided to keep the ECS since I really didn't need all the features the other boards offered, and since Ubuntu was now apparently working, it would be fine. ...

Fast forward to this morning. My new HDD arrived and I installed it right away and booted up the 7.04 i386 Live CD. It loaded up find and installed to the HDD perfectly. Zero issues whatsoever. Upon completion, I rebooted and loaded up Ubuntu. It would load normally until the very end, at which point the status bar would freeze for about 20 seconds and then move to a terminal-like display with the following:

*Mounting local filesystems
*Activating Swapfile swap
*Configuring network interfaces
*Loadind ACPI modules
*Starting ACPI services
*Starting system log daemon
*Doing Wacom setup
*Starting kernel log
*Starting system message bus dbus
*Starting hardware abstraction layer hald

After the last line, the system would hang for 2-3 minutes, then more code would pop up too fast to copy. After, the background to the Splash screen appears, but it's about 20 seconds before the Login appears.

After I'm logged in, the system itself is incredibly slow. I'm not able to enable the Nvidia driver, the system does not detect any updates, and when I use Terminal or Update Manager, it tells me that the repositories don't exist. Synaptic shows nothing detected as upgrades either. Loading up Feisty 64-bit, it also installs perfectly (although at a lower resolution) but once everything is loaded and restarted, the same as the i386--no upgrades, Nvidia, etc.

I went into BIOS and looked at the PCI Settings. My options are to either use on-board VGA adapter (which works perfectly, actually, but why have a video card if you can't use it?), PCI x16(which does not run at x16), or PCI x4.

I'm completely stumped now. I still have the other MoBo's ready to be shipped out. As I mentioned above, I'd prefer to keep the ECS, but will use the Abit IL9 Pro (which has a PCI-E running at full x16 speed) if necessary. Is this as simple as a PCI-E slot running at x4 speed or something else? The video card is an e-GeForce 7100 GS and worked perfectly with my previous Abit IP-95 Board, and currently works perfectly with XP.

This is the error that I get when trying to enable the Nvidia restricted Driver, thus leading me to believe it's a ethernet connection problem.:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/poo...-14.8_i386.deb](http://archive.ubuntu.com/ubuntu/poo...-14.8_i386.deb)
Could not resolve 'archive.ubuntu.com'

Furthermore, I'm not able to get any updates, or go online when I install with the PCI-E card. Is it possible my chipset isn't supported? Can a PCI-E card stop networking? I feel like a complete beginner all over again!
Any and all suggestions would be great! Thanks so much!

---

### Post by mikeyphi on 2007-10-17
Go to Systems/Administration/Software sources and enable the repositories.
From a fresh install these need enabling!
Hope that's all the problem is!

---

### Post by Imsati on 2007-10-17
Well, after trying to give that a shot, I found myself not being able to load the Xserver. :confused: I even went so far as to try a new install via Live CD and ran into the same problem as I originally had with this board: the CD would load halfway, then switch to lines of code, then the xserver would crash/would not load.

I'm done with this Board. I'm returning it today and keeping the Abit I was going to send back instead. I have one problem with that one though, Ubuntu does not recognize it as being able to scale the CPU. XP can do it, so I know the Board is capable of such a task, but why can't Ubuntu do it? It's an Abit IL9 Pro.


Ooo, I just looked on ebay and they have my old before that I *adored* (Abit IP-95) for a Buy It Now price of about $30, plus 22 shipping. I used that for a long time and know it's 100% Ubuntu-friendly, zero issues whatsoever. Should I just go for that you think or stick with the Abit?

---

### Post by Sef on 2007-10-17
> Ooo, I just looked on ebay and they have my old before that I *adored* (Abit IP-95) for a Buy It Now price of about $30, plus 22 shipping. I used that for a long time and know it's 100% Ubuntu-friendly, zero issues whatsoever. Should I just go for that you think or stick with the Abit?

I would stick with what works the best.

---

### Post by wpshooter on 2007-10-17
Have you tried installing your ECS board from the ALTERNATE CD instead of the live CD ?

I think you might have a better chance at success.

---

### Post by Imsati on 2007-10-17
Sef, I think you're right. I want to wait a few more hours though until I do.

wpshooter, I'll try it, but my Alt-CD of Kubuntu Dapper wouldn't work, so I'm too optimistic about this one. Downloading now.

---

### Post by maniac_X on 2007-10-17
ECS has not really had a great record when it comes to boards. They produce mainly ultra low budget boards. Sometimes it's very hit and miss as to boards working good and unstable...sometimes even within the same revision. I know I've had my share of issues with them and have quit buying them. There are other mobo makers of low budget boards that will be much more reliable than ECS.

---

### Post by Imsati on 2007-10-17
I'll never buy an ECS again after this. I'd rather sacrifice a CPU idling at 10*C higher (on the Abit) and still be able to use Ubuntu than have cooler temps and being forced to run XP. I'll just grab a new case for better airflow and deal with it.

---

### Post by Imsati on 2007-10-17
RMA is all set for the ECS :)  I know the Abit IP-95 and Abit IL9 pro work, but do I spend $57 (shipped to my door) off Ebay for a new IP-95 with only 2 gigs of maximum RAM, and 1.5 GB SATA 1; or keep my IL9 Pro, with 4 gigs total RAM and 3.0 GB SATA II  and spend $47 (shipped to my door) for a new case for better airflow from TigerDirect, and try to work around my CPU scaling feature in Ubuntu that's giving me trouble?

I guess since I don't do any graphic-intensive game like WOW or whatever the popular ones are today, or do video editing or anything like that, (also, Vista will *never* touch any computer in our household) I really don't need more than 2 gigs of RAM, huh?

---

### Post by kerry_s on 2007-10-19
for maniac_X

---

### Post by maniac_X on 2007-10-23
> **Imsati said:**
> 
I guess since I don't do any graphic-intensive game like WOW or whatever the popular ones are today, or do video editing or anything like that, (also, Vista will *never* touch any computer in our household) I really don't need more than 2 gigs of RAM, huh?

grats on the RMA! better to be rid of that problem. :) as for 2GB and no intensive  graphics stuff.....yea, 2GB should do you fine.


and THANK YO VERY MUCH Kerry_S for the wall paper!! Fantastic!

---

### Post by Blaze1024 on 2007-12-13
Even though this thread is kind of old, I thought I would toss out some ideas 

I have experimented with the ECS 945GZT-M main board and discovered that Linux does not play well with its SATA controllers. If you have any SATA drives connected Ubuntu will not boot. If it does boot it will run painfully slow taking up to 15 min to boot. The solution for me was to disable  the on board SATA and just use my PATA drives.

---

