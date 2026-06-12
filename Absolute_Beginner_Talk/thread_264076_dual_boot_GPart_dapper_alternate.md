---
title: "dual boot GPart *dapper alternate*"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by carverj on 2006-09-24
G'day,
Am having problems with the partitioning step of a dual boot
install. I have a Pressario AMD 533 with ntfs on the first partition. First it crashed and now when I try to add a primary ext3 in the unallocated space, it comes up with a little yellow "!"
warning and doesn't recognise the partition (black border).it will not let me allocate a / partition in the final step and just has
the media mount point for the ntfs partition.
It also fails to recognise my secondary drive
Could this be a bug with the alternate parted disk or is it likely that I have made the error?
Cheers guys

---

### Post by Sef on 2006-09-24
I would download and use [GParted.]("http://gparted.sourceforge.net/livecd.php") See if you get the same problem.  It could be your disk has gone bad.

---

### Post by cotcot on 2006-09-24
I think that Sef means GParted LiveCD.
I fully agree. I have never had problems with this CD. I think the gparted of Dapper has problems with unexpectedly trying to mount the partition you are formatting and that you get therefore the yellow "!" .

---

### Post by Sef on 2006-09-24
> think that Sef means GParted LiveCD.
I fully agree. I have never had problems with this CD. I think the gparted of Dapper has problems with unexpectedly trying to mount the partition you are formatting and that you get therefore the yellow "!" .

Cotcot > you are right.

Note: The warning sign: I had the same problem on another computer.  Just confirmed that the hard drive is bad and needs replacing.

---

### Post by carverj on 2006-09-25
Ok, so I downloaded the .iso and burnt it to disk.
Now, when I boot I get a dos interface and access to fdisk
Is this the right disk I need and if so what do I do next?
I have a 16.9GB (18,169,606,144 bytes capacity according to Windows C:\ properties) ntfs partition on a 40 G primary disk!
Could someone please reply with the command I need to format some space to insert my Ubuntu partition/s
Cheers

---

### Post by Herman on 2006-09-25
Did you download [gparted-livecd-0.3.1-1.iso]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828")? :confused:

Something is very seriously wrong if you are getting a dos interface.

You should be booting up into a Linux Live CD operating system, with a Window Manager and a Graphical display showing your partitions.For an illustrated GParted LiveCD how-to by Larry T, [Click Here ]("http://gparted.sourceforge.net/larry/livecd/main/livecd.htm")

GParted LiveCD is really great, it should be so easy to use that you wouldn't need to even bother asking! You won't need to know any commands, it's all point and click. There's a terminal in it you can use though, if you want to. I think probably something is probably wrong with your download, or your burning to disk, or something.  

Regards, Herman :D

---

### Post by carverj on 2006-09-25
Right I'll definately look into that Herman.
With regards to the installation, I had another crack at it and
managed to get the alternate live CD (Ubuntu) to partition, made a new primary partition for Ubuntu next to ntfs, neglected to chooose a swap partition on the primary drive because it seemed to notice the swap partition on my secondary hard drive and I wanted to see if I could point fstab to it after installation.
So started to install base files OK and then crashed 82% of the way through !! I have 256MB RAM, AMD 533MHz processor. Is there a problem with this new way of installing Ubuntu or is it likely to be caused by my poor system specs ?
Cheers fellas

---

### Post by confused57 on 2006-09-25
> **carverj said:**
> Right I'll definately look into that Herman.
With regards to the installation, I had another crack at it and
managed to get the alternate live CD (Ubuntu) to partition, made a new primary partition for Ubuntu next to ntfs, neglected to chooose a swap partition on the primary drive because it seemed to notice the swap partition on my secondary hard drive and I wanted to see if I could point fstab to it after installation.
So started to install base files OK and then crashed 82% of the way through !! I have 256MB RAM, AMD 533MHz processor. Is there a problem with this new way of installing Ubuntu or is it likely to be caused by my poor system specs ?
Cheers fellas

You might be able to install with 256MB RAM using the live cd, that's probably the minimum amount of ram for a successful install...guess you could try it again & if it doesn't work, you'd probably have much better success with the Dapper alternate cd.
Here's a guide to burning an iso:
[http://psychocats.net/ubuntu/iso](http://psychocats.net/ubuntu/iso)

This site has some excellent screenshots of the alternate cd installation(this is Herman's website, which he's already provided links to):
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

I've had no problems using the alternate install cd on a 500MHz, 256MB ram computer...I've never installed with the live cd, just prefer the alternate text-installer.  I once had the alternate install stop at around 80%, but worked OK on the second attempt.

After reviewing Herman's reply, I believe I've just managed to repeat everything he'd already told you...as I mentioned, you may just want to try installing again.

---

### Post by rbailey on 2006-09-25
I am currently having the same issues with installing v5.10 on an amd k5-500mhz machine with 2 drives.   master has win 98 on an 8 gig drive devoted to fat 32 and slave drive is a maxtor 20 gb drive for use with ubuntu.   The 5.10 live cd boots fine, detects everything.   installer disk gets through base packages and dies every time while copying packages to the drive.   I can get pass this point and get the grub installed but then the system wants to install and not boot to an option.  I have even partition magic'd the master drive to only use 3 gbs and gave 5 to ubuntu with the same results.  I am currently running the live and trying copy the installer disc to the drive and I am going to try the install from the local drive.   
Does anyone know the command to kick off the installer from the local machine?
I previously had Red Hat on the slave drive running a dual boot so I know the drive is good.  I have also tried the v6 graphical installer and found that I get an I/O error while unpacking the kernel everytime.  I am so confused.  I have tried both burned discs and discs sent from ubuntu.

---

### Post by carverj on 2006-09-26
It's OK now. managed to install on the next attempt.
Just wondering though if anyone knows of a decent web development
package for Linux. I am thinking of installing mono project for
C# development, but don't think it can handle web stuff yet
Cheers for all your help guys.
Appreciate it (feel like I got a new toy again)

---

### Post by Herman on 2006-09-26
I don't know, I use NVU. When you have all your repositories enabled, just do a search in synaptic and you'll find that. It does everything I need, but I'm just a beginner as far as web site developing goes, (or maybe not even a beginner yet). I just want to be able to get a lot of work done fast.   :D  
I have a feeling you are looking for something more advanced and fancier. 
I also have screem but I haven't really tried it out. that might be worth looking at. 
Regards, Herman :D

---

