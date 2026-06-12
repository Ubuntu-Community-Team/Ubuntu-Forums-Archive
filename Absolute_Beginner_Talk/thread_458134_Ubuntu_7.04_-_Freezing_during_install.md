---
title: "Ubuntu 7.04 - Freezing during install"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by cmcm on 2007-05-29
Hi, I'm new to the world of Ubuntu, and Linux in general, but I've spent a lot of time working with different types of software in hardware for about 10 years now, so I'd like to think I'm fairly educated about most computer-related tasks. I have come to a snag and was hoping I could request some help from the Ubuntu vets here.

I'm excited about getting my first Linux OS installed, and have done some research to see what will work and what won't. Here is a list of my specs to get started:

CPU: AMD Athlon X2 5200+ Socket AM2
Mainboard: ECS KN3 SLI2
RAM: 2x1GB Crucial Ballistix Tracer DDR2-1000
GPU: 2xGeForce GTS 8800 320MB
Sound: Creative X-Fi Fatal1ty
HDD: 2xWD Raptor 74GB SATA RAID0 + WD 500GB SATA
Optical: Generic SATA DVD-RW DL

My current setup before beginning to install Ubuntu was a WinXP Pro installation across the RAID0 array on the Raptors (as drive C) and all my important documents stored on the 500GB standalone (as drive E). Both the RAID0 array and the 500GB were formatted as NTFS.

After reading up on how to prepare your computer for Ubuntu installation, I found that I should have an EXT3 partition for the install, and a swap partition. I also found that Ubuntu has some trouble with RAID drives, so I used PartitionMagic 8 and created 2 partitions at the end of my 500GB - a 40GB EXT3 Primary partition and a 2GB swap partition. I then proceeded to install Ubuntu.

I downloaded and burned the AMD64 7.04 release of Ubuntu. When I first booted off the CD, I chose the first option, "Start or install Ubuntu." I then proceeded to get a black screen for the next several minutes, and no response from my CD or hard drives. I rebooted and figured it may be the video, so instead of using the default of "VGA" I chose "1024x768 32bit" and that seemed to work. Orange loading bar, got the desktop, found the installer on the desktop and double clicked.

I worked my way through the installer until it got to where I chose where to install. I don't know too much about what I was doing, but from my limited experience I think I did it right. I chose my standalone 500GB drive, chose the 40GB EXT3 formatted partition for my root, and also selected the mount point as "/", and for my swap partition, I chose the 2GB swap partition I created. It proceeded to install, and at about 15% it froze. No response from mouse or keyboard; numlock light would not turn on and off when I pressed it. Hard-reset the computer to try again.

I tried these same steps again and it locked up at the desktop before I could double-click the installer. Reset the computer and tried again, and made it to the orange-background, but the desktop didn't load. Reset the computer again, and made it all the way to the installer, but froze as I was typing in my username and password.

I'm not sure which direction to look. I've been told by my friend who has successfully installed Ubuntu on his laptop before that I needed no drivers until I got it installed, but if I can't get it installed, then what do I do? I hear things about how there are driver incompatibilities with most Linux distros for fresh hardware like the 8800GTS, the X-Fi, and numerous onboard devices - could this be what is causing problems? My motherboard has no Linux drivers for the chipset (nForce 590 SLI); at least on ECS's website there are none.  I know my Windows usage has been flawless so far, so as far as I am aware I don't have any faulty hardware.

Anything else I can try?

---

### Post by santy_kushwaha on 2007-05-29
it does happen sometimes. I faced the same problem when i was installing the ubuntu 7.04. what i found in my case was that i freezes on the last step when it checks the hard drive to install ubuntu. so i install old version of windows2000 and then i install ubuntu it works like a charm...

         try it and have fun

---

### Post by cmcm on 2007-05-29
Also, I should mention I tried the 32bit version, and it did the same thing. I also ran a verification on both disks which came out with no errors.

In response to installing Win2k first, I don't really understand how that would help, as I already have XP installed, and I didn't see any way to install Ubuntu onto another partition from within Windows. I'm just booting off the LiveCD and attempting to install that way.

Is there another method I should attempt? Possibly, anything non-GUI based? I don't *think* it's the UI messing up, as I was able to browse the 'net from the LiveCD directly. Any ideas please post.

---

### Post by Benbow on 2007-05-29
When I insalled Feisty my creative sound card gave me a lot of problems and in the endt I removed the card, uninstalled the creative drivers and I now rely on the motherboards internal sound which is fine. 
Just a thought.;)

---

### Post by cmcm on 2007-05-29
> **Benbow said:**
> When I insalled Feisty my creative sound card gave me a lot of problems and in the endt I removed the card, uninstalled the creative drivers and I now rely on the motherboards internal sound which is fine. 
Just a thought.;)

I would hate having to remove hardware just to make Ubuntu work, but I will certainly give this a try when I get home today. In the meantime, any other ideas are appreciated!

---

