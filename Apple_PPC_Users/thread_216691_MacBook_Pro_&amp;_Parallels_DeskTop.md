---
title: "MacBook Pro &amp; Parallels DeskTop"
date: 2006-07-15
forum: Apple PPC Users
---

### Post by Chairwalker on 2006-07-15
Hi everyone,

I'm the happy owner of a new MBP. I installed a virtual machine emulator (namely Parallels DeskTop) under Mac oS X and used it to install and run successfully Windows XP.

A friend of mine gave me a two disks package (Ubuntu 5.04 for Intel x86) to see if I could installed it under Parllels DeskTop.

Unfortunately, during the Ubuntu installation process, I got an error message (unable to install base package).

Before spending more time trying to install Ubuntu, does anyone has ever succeed doing what i'm trying to attemp?

A screenshot ( sent at   safeluke -at- mac.com ) would be a cool proof.

Thanks,

LukeChairWalker

---

### Post by hajk on 2006-07-17
It should be possible to install Ubuntu Linux in the Parallels VM, but you should do that with a more recent version. The 5.04 version ("Hoary") is more than a year old, the most recent version is 6.06 ("Dapper"). 

You should download from [http://releases.ubuntu.com/6.06/](http://releases.ubuntu.com/6.06/) the Desktop CD image for the PC(Intel x86) platform. No need to burn it to disk, you can just mount the image in the Parallels VM that you make for Ubuntu, and start from there. Note that this image (unlike the 5.04 version) is a liveCD, meaning that a fully-fledged Ubuntu session will run first off the image, with an option to start installing it.

Good luck, let me know how it went because I'll be doing the same thing on my new MB shortly...:D

---

### Post by chasisaac on 2006-07-17
> **Chairwalker said:**
> Hi everyone,

I'm the happy owner of a new MBP. I installed a virtual machine emulator (namely Parallels DeskTop) under Mac oS X and used it to install and run successfully Windows XP.

A friend of mine gave me a two disks package (Ubuntu 5.04 for Intel x86) to see if I could installed it under Parllels DeskTop.

Unfortunately, during the Ubuntu installation process, I got an error message (unable to install base package).

Before spending more time trying to install Ubuntu, does anyone has ever succeed doing what i'm trying to attemp?

A screenshot ( sent at   safeluke -at- mac.com ) would be a cool proof.

Thanks,

LukeChairWalker




Make sure that you have dapper and it will run great.

---

### Post by Chairwalker on 2006-07-18
Thank you hajk !

Everything went just fine with the most recent version is 6.06 ("Dapper"). 

I download and ISO image an told Parallels VM to use that file as a CD. I made sure to change the booting sequence (CD first) and assigned device 0:0 to the virtual disk and 0:1 to the CD.

The virtual machine boot with the CD and the installation on the virtual disk work just fine. At the end of the process, I was offered to eject the CD and reboot or continued using the live CD. I choose the latter and then shutdown Ubuntu.

Back in the virtual machine, I change the booting sequence and told Parallels to use the default CD drive rather than an image.

I rebooted and voilà!

Good luck and thanks for the tip.

Luc (see the screenshot attached to this message)

---

### Post by FierceBob on 2006-08-05
Luc -

Thanks to your experience and your post, I am successfully installing Ubuntu in Parallels on my MBP right now.  I had tried installing from the CD I burned a few times, but the installation kept hanging on "Detecting File Systems" at 15%.  Should have thought of installing straight from the disk image myself.

Anyway, I did as you suggested, and it's going smoothly even as I type.  Just passed 50%.

Thanks again.

FB

PS: The installation did complete without incident, and I now have a working Ubuntu installation inside of OS X.


"Avoid f**kers."
- William S. Burroughs

---

### Post by Ebabylon on 2006-09-13
Try Ubuntu 6.06 on Parallels Desktop. Work just fine. I have a Mac Book Pro with Windows xP Pro and Ubuntu. Both runs faster in my Mac that on any other PC on the market.

---

### Post by mike3k on 2006-09-13
I've installed 6.06 on Parallels and it works great. How's this for sick -- the VM resides on a NFS server volume which happens to be my real Ubuntu box :cool:

---

### Post by geodude on 2006-09-21
When running Ubuntu in Parallels on the MBP, does the wireless work?

---

### Post by hajk on 2006-09-22
Yes, OS X keeps on working underneath and so does does the Airport wireless interface. The Parallels VM itself has an Ethernet interface (modelled in software). The two can be connected with "Internet Sharing", something that you set up in OS X.

---

