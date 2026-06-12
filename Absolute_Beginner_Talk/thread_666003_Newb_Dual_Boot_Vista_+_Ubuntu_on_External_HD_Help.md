---
title: "Newb Dual Boot Vista + Ubuntu on External HD Help"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by dnguyen1022 on 2008-01-12
Ok I just bought a WD 250gb Passport to dual boot with vista on my laptop (Sager2090/compal ifl90).  I haven't opened it yet, and don't plan on to unless I think I have a good idea of how to dual boot on an external hard drive.  I've read through many threads and it seems complicated.  I'm not sure if others are installing from a regular computer or a laptop either.  Can you guys lead me in the right direction with threads or instructions on how to install Ubuntu on an external hard drive that is usb powered.  I have burnt a copy of the Ubuntu 64 bit desktop version.  I just need proper instructions now.  Are there any known errors with the WD Passport external hard drives by the way?  THANKS!!!

---

### Post by blueridgedog on 2008-01-12
See this thread:

[http://ubuntuforums.org/showthread.php?t=652134](http://ubuntuforums.org/showthread.php?t=652134)
(you may want to correspond with the OP)

See this howto:

[http://ubuntuforums.org/showthread.php?p=3995006#post3995006](http://ubuntuforums.org/showthread.php?p=3995006#post3995006)

---

### Post by CCNA_student on 2008-01-12
I put instructions for this on my Linux blog. [http://wheatlandlinux.wordpress.com/instructions-and-how-tos/]("http://wheatlandlinux.wordpress.com/instructions-and-how-tos/")
These instructions worked for me anyway. I hope that you succeed.


     Sin Cere,

     CCNA

---

### Post by dnguyen1022 on 2008-01-12
thanks but wheres the beginning instructions of actually installing ubuntu onto the external hard drive? sorry im a real newb...it seems that howto posted by CCNA_student is based on installing on the same hard drive?

---

### Post by blueridgedog on 2008-01-12
When you install Ubuntu, you will have an option to pick the destination, at that point pick the external drive.  Read through the entire thread and the howto before proceeding as if done right, you can boot Ubuntu with the drive plugged in and Windows with it removed (that was the goal of the OP in the thread I sent you, hence the suggestion that you correspond with them).

---

### Post by dnguyen1022 on 2008-01-12
Soo I just plug the external drive in and pop ubuntu into my dvd/cd drive and run the setup picking my external as the destination?

---

### Post by bossie7079 on 2008-01-12
I don't think my Post will be that helpful. I am as lost as you might be. I got a new Lap Top. Unfortunately i am not a programmer, I have been searching on the internet about all the Linux Distributions. 

**My  brand new  Lap Top came w/ W Vista**, but I tried to **Install Ubuntu 7.10** but when the partition choice comes up I'm so scared that I don't want to mess up my new computer. I have **2 hard drives. 160  GB each.**I don't know what to do. Spite I have the user's guide.

I got the Ubuntu user Guide and it's been helpful. 

One great thing I have to say about GNU Linux is that you have many many **free software** available. At least it fits my needs. But still** I need Auto Cad, Sketch Up 3d Max, Photoshop and I don't know if those applications comes for Linux...**

If some one could advise me I'd really appreciatte your help.

bossie

---

### Post by dnguyen1022 on 2008-01-13
another quick question...i just reformat my whole drive to ntfs will installing ubuntu automatically reformat it?  is there any possible way for me to create two partitions on the external?  one for ubuntu and one simply for storage?  or just a simple way to access files from both os..



> **dnguyen1022 said:**
> Soo I just plug the external drive in and pop ubuntu into my dvd/cd drive and run the setup picking my external as the destination?
still need help with that ^^

---

### Post by dnguyen1022 on 2008-01-13
quick bump before i sleep..

---

### Post by Presto123 on 2008-01-13
The external installation can be annoying if not done right due to the grub loader being installed directly to the main HD resulting in you having to have the external connected for it to load. That issue CAN be fixed if this problem happens, but you would have to go into GRUB or have a SuperGrub disk handy.

Otherwise, if you follow directions on some of these sites that explain the whole thing, you can get it right. I think the two posted above will help you with GRUB.

---

### Post by blueridgedog on 2008-01-13
> **dnguyen1022 said:**
> Soo I just plug the external drive in and pop ubuntu into my dvd/cd drive and run the setup picking my external as the destination?

Yes, that is the really really short version.  But, reading the links I sent should enlighten you as to the potholes down the road.

My personal approach (and one that others my find objectionable due to experience or personal choice) is to remove your internal hard drive (a simple mater of one screw and a slide out tray on a laptop), boot on the install CD with the external USB drive attached, install Ubunut, then replace your hard drive and set your bios to but USB before internal hard drives (important, this must be an option in your bios).

The end result is the Ubuntu and grub (the software that loads operating systems) will reside on the USB drive) and your current hard drive will not be affected at all.

So, when the USB drive is plugged in, it is first, grub loads and loads Ubuntu, if unplugged, you get windows without any action on your part.

---

### Post by dnguyen1022 on 2008-01-14
I found out I have the ability to disable my hard drive so that it does not work at all from my BIOS.  Makes it much easier.  The installation doesnt seem to be going well though..I can't reach the test version of ubuntu.  It just tells me to configure my graphics card and then ends up at some black screen that uses dos like commands at which point im clueless.

---

