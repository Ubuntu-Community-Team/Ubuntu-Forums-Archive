---
title: "Just getting started - trying to figure it out one challenge at a time - video 1st"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by Episteme on 2006-08-27
I've tried to set up linux several times in the past, with varying degrees of success. However, I now realize that any flavor of linux is only as good as what I put into it – the more committed I am to getting it to run the more I'll get out of it.  I don't expect it to work right out of the box – window's didn't either – but at least I can learn to fix and change things myself now. I expect a stiff learning curve, but at least there's hope now that I've fdisk/mbr windows off my machine once and for all. 

Soooo, here I am, linux day 2 – a complete and total lidiot – I've just installed the generic 64bit version, and starting to take stock of getting the hardware setup properly. It's been said that if you have more than two devises that don't work you should get another distro...well, not all distro's have a philosophy like ubuntu – besides, there's opportunity for growth in any challenge.  I may ask alot of simple questions right now, and will get frustrated at times – but so long as I'm showing patience in learning,  please show patience in teaching.  Everytime I have a problem, I'll do my best to solve it – and share the solutions in 'newbie speak' for others to follow.

Sooo, on with the show... my hardware looks like this, m'kay:

Motherboard / CPU:  ASUS A8V-E Deluxe AMD Athlon 64
(I have no idea if it is set up properly, let alone optimally, but it works so far...) 
Videocard: MSI GeFORCE 6 series (Nvidia NX 6800 PCI)
(again, clueless)
Soundcard: On board Realtek ALC850 8-channel CODEC
Not working properly... I'm only getting 2 channels rather than the 7.1 she's capible of. Also, I'd love to figure out how to get DVD's to passthrough the optical direct to my sound system.
TVTuner:  ATI TV Wonder Elite (THEATER™ 550 PRO VIDEO Processor)
I have no idea where to start with this one yet.
Monitor: Dell MP3600 projector @ 1024 768 native resolution and 60Hz
**_I keep changing my resolution to match up using SYSTEM > PREFS > SCREEN RESOLUTION, and it keeps reverting up... driving me nuts._**
Camera: HP Photosmart R607
Haven't tried it yet
Webcam: Logitech QuickCam Pro 5000
Haven't tried this yet either.
Harddrives: I have two slave drives I use to store my media – I would LOVE to figure out how to access them.  At least then I can listen to my music while I work.
Ipod: Haven't plugged it in yet – kind of scared to until I get everything else sorted out.

Once I've got the hardware properly configured, I want to do the following:

1.TV Tuner – I really need to get Myth set up... I miss being able to record CSI when I'm at work.
2.DVD's – I got them to work in Gxine (YEAH ME!), but I can't figure out how to send out the dvd sound directly to my sterio system by way of the spdif optical cable so that I can use all my speakers. I'll wait until I have my soundcard set up properly first. I would also like to be able to copy my DVD's over to my harddrive in DIVX – I could do this in windows easily enough...
Heck – wouldn't it be cool to set it up so that when I put in a new DVD, it checks against my data base of movies, and if I don't have it saved yet give me the option of copying it or playing it in Gxine?  Yes, that would be very cool! And could be an excellent learning experience to be able to do it myself.
3.Security – The reason I picked up linux – I got tired of being hacked to ribons. I would love to view the packet info the next time some putz of an ex with too much time on her hands decides to read my email or crash my bios. Memo to me – never date an evil computer tech.
4.Get my videocam up and running again so I can chat with my brother in NY.


So, I guess my first thing to do is get my sound and video tweeked – getting my resolution down to match my monitor is first. Making sure I have the optimal drivers for my Nvidia (MSI) card is second.

After that I'll tackle my sound issues.

It's nice to be here!

---

### Post by xmastree on 2006-08-28
> **Episteme said:**
> Soooo, here I am, linux day 2 – a complete and total lidiot – I've just installed the generic 64bit version...Before you get too far into it, I would start over and install the 386 distro instead.
Although you do have a 64 bit cpu, the 64 bit distro isn't quite as fully fledged as the regular one.
Basically, it's not for beginners.

The 386 distro will work just fine, if not better.


> Videocard: MSI GeFORCE 6 series (Nvidia NX 6800 PCI)
(again, clueless)
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)

> Harddrives: I have two slave drives I use to store my media – I would LOVE to figure out how to access them.
[http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)

First you define a mount point. This can be anywhere on the system but there are two 'traditional' locations /mnt and /media . The latter will place them on the desktop.
Then you tell the system about the disk by inserting a line in /etc.fstab for each disk.

---

### Post by handy on 2006-08-28
I agree, i386 is a great place to be, fewer problems, more compatability.

With patience & the willing community ALL that hardware should get sorted.

When you are ready have a look at the [Automatix]("http://www.getautomatix.com/") site, on installation, it will present you with a menu of over 46 of the most popular softwares, codecs & the nVidia proprietary drivers.  You choose what you want to install & then Automatix does the hardwork, incredibly reliably.

Welcome **Episteme**, I hope that you enjoy the trip? ... :KS

---

### Post by Cynical on 2006-08-28
64-bit ubuntu is not for impatient people. If you want things to 'just work' more often then it would be better to use the 32-bit version.

---

### Post by handy on 2006-08-28
Having multiple drives, you may like to look into having a drive as your **/home** or at least a look into having a **/home** partition, it is most beneficial when you have to rebuild your system due to having messed it up, or if it needs a clean install Ubuntu upgrade, hardware failure...

[Here is the link.]("http://www.psychocats.net/ubuntu/separatehome.html")

---

### Post by TwistesdTexan on 2006-08-28
I agree with Handy and like the use of Automatix. Alot of people disagree though because it doesn't teach you how to download, install, and setup the programs your self. I don't have the patients or the time to do all of this each time I decide to do a complete re install or upgrade. I do though on ocation search through synaptic for different programs. I have a P4 3ghz with a gig of ram. I am running i386 Dapper Ubuntu. To many problems with the 64 bit Dapper (Booting up). I have stayed with Ubuntu for the same reason as you. People here are willing to help you out with problems.:-D

---

### Post by Episteme on 2006-08-29
Hey,

Thanks for all the replies and words of encouragement.

I decided to stick with the 64bit version - I can be fairly percistent (stubborn?) when facing a challenge, and I'll never become patient by taking the easy way out... speaking of which - automatrix definately did the trick for solving most of my issues - and so it doesn't look nearly as daunting today.

Again, many thanks.

---

