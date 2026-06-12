---
title: "Getting Linux to work on a Mac"
date: 2010-09-21
forum: Apple Hardware Users
---

### Post by grandjackal on 2010-09-21
Hello, new to the forums and most likely only going to have this one topic to ask a simple question. How would I go about getting the Linix operating system to work on a Mac OS X laptop computer? I'm rather hesitant to trying myself just winging it, since I'm lucky to even have this thing. However, if there is a safe way to get Linux to work on this thing, I'd like to do so safely since the Mac operating system is too restrictive for my purposes.

I'm not sure what more info would be required, but I'll bring it up if asked.

---

### Post by redbook4574 on 2010-09-21
> **grandjackal said:**
> Hello, new to the forums and most likely only going to have this one topic to ask a simple question. How would I go about getting the Linix operating system to work on a Mac OS X laptop computer? I'm rather hesitant to trying myself just winging it, since I'm lucky to even have this thing. However, if there is a safe way to get Linux to work on this thing, I'd like to do so safely since the Mac operating system is too restrictive for my purposes.

I'm not sure what more info would be required, but I'll bring it up if asked.

I believe most linux distro's will run quite happily on a mac (especially the newer type with intel processors). It is after all just a laptop, try running a live version first from cd and see if you hit any major issues, if you do not, try a dual boot install.

---

### Post by bradleypariah on 2010-09-21
I'm running Ubuntu 10.10 64-bit on a Mac right this moment.  Macs are meant to be compatible with UNIX.  Linux, being a derivative of UNIX is an easy substitute.  I had a couple issues with Broadcom wireless drivers, but as you can see by my internet connection (I was able to post here, in other words), it is fixed and I never have problems

---

### Post by grandjackal on 2010-09-21
Oh, had no clue that Macs actually were easy to work with Linux (Since they're a pain in the *** to work with nearly anything else). Ok then, I'll be sure to try out the solutions given to me, as they sound simple enough. 

Well, thanks for the quick responses to my simplistic question. Uhhh, sorta new here so do I mark this topic as solved? Or does it really matter if I do it or not?

---

### Post by bradleypariah on 2010-09-21
You're welcome.
So, if you have a G4 or older, you probably have a Power PC.  So, make the correct choice when deciding which version of Ubuntu to download.
If you have a Quad-Core processor, it's safe to download the 64-bit version of Ubuntu.  If you're not sure what you've got, but you know it's Intel, then download the 32-bit (x86) version of Ubuntu.
Once the download is finished, open your downloaded .iso file with Disk Utility.  Hilight the .iso in the new window and choose **Burn** (or **Burn Image**?  I forgot.)
If you have Boot Camp Assistant, use it to partition a space on your drive and let it guide you through the installation process.  It will tell you that you are trying to install Windows, but ignore that.
If this sounds like too much of a commitment, then just do as RedBook suggested above.  
Once you've burned your .iso to a disk, just reboot your Mac with the CD in the drive and hold down {option} through the boot process.  You'll see the Ubuntu disk there and just arrow over it and hit {enter}.  When prompted, choose a "Live" desktop instead of an install, and within a couple minutes, you'll be running Ubuntu.
If you like it, the Live environment can install the OS.  If you change your mind, just restart the computer and remove the disk.  Everything will be back the way it was.

I forgot how to mark a topic as solved...

---

### Post by grandjackal on 2010-09-21
I'll just try the live CD version, though thanks for the info if for some reason I have to use non-CD versions.

---

### Post by DougieFresh4U on 2010-09-21
You may want to check this [Apple Users]("http://ubuntuforums.org/forumdisplay.php?f=328") here at the Forum

---

### Post by srs5694 on 2010-09-21
Be aware: I've been seeing a lot of posts on this site lately (such as [this one](http://ubuntuforums.org/showthread.php?t=1578694)) from people who have problems because one of the tools or procedures in at least one common Linux/OS X dual-boot tutorial is producing dodgy [hybrid MBRs.](http://www.rodsbooks.com/gdisk/) People who aren't experts are left floundering at this point, and posts sometimes produce well-meaning but counterproductive advice from people more familiar with commodity BIOS-based systems than with Macs.

FWIW, I know a lot about MBR, GPT, and hybrid partitions, but I know relatively little about how Macs boot. Thus, I've got half the expertise needed to solve this problem, but my knowledge will only go so far. I strongly suspect that the install tutorials that are commonly referenced are sub-optimal, even aside from the issue of whatever bug is producing those flawed hybrid MBRs. I'd like to get an Intel-based Mac to experiment with, but I don't have the cash just now....

---

### Post by -kg- on 2010-09-21
> **bradleypariah said:**
> You're welcome.
So, if you have a G4 or older, you probably have a Power PC.  So, make the correct choice when deciding which version of Ubuntu to download.
If you have a Quad-Core processor, it's safe to download the 64-bit version of Ubuntu.  If you're not sure what you've got, but you know it's Intel, then download the 32-bit (x86) version of Ubuntu.

Alternatively (if you have a good high-speed internet connection with no bandwidth limitation), you can download the 64-bit first and try it on Live CD.  If your system isn't 64-bit, it won't run, in which case you know you need to download and use the 32-bit disk.

---

