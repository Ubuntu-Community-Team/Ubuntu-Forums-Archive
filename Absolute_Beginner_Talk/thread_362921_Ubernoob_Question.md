---
title: "Ubernoob Question"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by aheicher on 2007-02-16
Hi everyone!  I have been in Linux for a little while, but alas my understanding of it has much to be desired.  I have a few questions that I ask will be answered in as much detail as possible.  First of all, I have Ubuntu running as and .iso image from a burned CD and it is working fine.  I have 512MB of Ram and 29.5GB left on my hard drive.  I would like to install Ubuntu from the CD (Which I know how to do) so that I will be able to Dual Boot it with my Windows XP (Intel Processor).  The windows XP is running on a Dell computer with comcast high speed internet.  The modem for the internet is connected with ethernet.
What I would like is for someone to explain to me the Dual Boot process if possible, screen shots would be nice, again, if possible.  How much will this slow my windows XP down?  Will it delete all of my windows XP data?  **Will I be able to save the changes I make to Ubuntu, which I cannot do from the CD?**  Please answer as many questions as you are capable of answering in as much detail as possible, especially the one in bold.  Thank you for listening to the ramblings of an UberNoob
Hail Gallifrey!
AH
One other thing-One hard drive, one partition.
Thanks!
BTW-I did read the "READ THIS FIRST" sticky post-so dont yell at me about it

---

### Post by hanexar on 2007-02-16
> What I would like is for someone to explain to me the Dual Boot process if possible, screen shots would be nice, again, if possible.  

If you want to make a new installation of everything: [http://video.google.ca/videoplay?docid=-6104490811311898236&q=dual-boot](http://video.google.ca/videoplay?docid=-6104490811311898236&q=dual-boot)

If you want to resize your partition first, use gparted on your live CD to shrink your windows partition, then install ubuntu on the free space.

If you have two partitions / hard drive, just format the one windows is not on, then install ubuntu on the other one.

> How much will this slow my windows XP down? 

no at all  

> Will it delete all of my windows XP data?

Depens if you want to reinstall everything, or just resize your partition

>   **Will I be able to save the changes I make to Ubuntu, which I cannot do from the CD?** 

That's the point of install ;) Of course!

Welcome to ubuntu. And, suggestion, a topic name like dual-boat will get you answer quicker.

---

### Post by sloggerkhan on 2007-02-16
So defrag windows a couple of times and run the installer. Select make partition out of free space. Install. Good to go.

Dual boot will have a menu load up at boot where you choose what to boot. It will probably last for about 3 seconds, thought you can change that by editing a file called menu.lst in /boot/grub

It shouldn't slow XP down at all. It's completely unrelated unless you are talking virtual machines or something.

All the changes you make to Ubuntu will stick.
You may have to precede some of them with "sudo" as the live cd has different permissions than a actual installed Ubuntu.

I'd think the internet would autodetct.

---

### Post by mdsmedia on 2007-02-16
> **aheicher said:**
> Hi everyone!  I have been in Linux for a little while, but alas my understanding of it has much to be desired.  I have a few questions that I ask will be answered in as much detail as possible.  First of all, I have Ubuntu running as and .iso image from a burned CD and it is working fine.  I have 512MB of Ram and 29.5GB left on my hard drive.  I would like to install Ubuntu from the CD (Which I know how to do) so that I will be able to Dual Boot it with my Windows XP (Intel Processor).  The windows XP is running on a Dell computer with comcast high speed internet.  The modem for the internet is connected with ethernet.
What I would like is for someone to explain to me the Dual Boot process if possible, screen shots would be nice, again, if possible. The dual-boot process means that you run 2 (or more) operating systems on the one hard drive (or on separate harddrives) using a boot manager to allow you to decide which OS to boot into. >  How much will this slow my windows XP down?  Will it delete all of my windows XP data? It won't slow down your XP at all because they run on separate partitions within the same system. It's best to backup all your important data, just in case something goes wrong with the installation. It shouldn't happen, but just in case. > Will I be able to save the changes I make to Ubuntu, which I cannot do from the CD?Yes, the idea of the Live CD is to allow you to try the OS before installing. You can't save changes to Ubuntu in the CD because it's on CD. Once installed on your harddrive you can save changes just as you can in XP.

> BTW-I did read the "READ THIS FIRST" sticky post-so dont yell at me about itWhich part didn't you follow, so that we would yell at you about it? ;)
A great site for your installation questions and answers is [www.psychocats.net/ubuntu](www.psychocats.net/ubuntu)

---

### Post by ac7ss on 2007-02-16
The only slowdowns with XP will be:
[INDENT]Boot time with the GRUB loader (7-8 seconds)
Possibly not having as large of a swap space in Windowz.[/INDENT]
I did this on my laptop for the transition period and the only trouble I had was that I shrunk my NTFS partition a little too much and Windowz complained all the time that there was no disk space left.

You should also consider that you will not have write acces to your NTFS partition from Linux. and you won't be able to change your NTFS back to a FAT. Read access will work fine. 

While you are partitioning, create your swap partition. I suggest about 2 gig. YMMV. But a minimum of 2x your RAM should be very useful. I think you could make a FAT partition and use it for both your MS and Linux swap but I don't know for certain. But partition it out before installing Linux anyway. you can change the type and method of swap later, but the partition is more difficult to do after installation.

---

### Post by hanexar on 2007-02-16
> **ac7ss said:**
>  I think you could make a FAT partition and use it for both your MS and Linux swap but I don't know for certain. 

Yea, the Fat partition is a good idea. Make it big, so you can dump all your music, video, document on it. You will be able to use it from windows and from ubuntu easily.

---

### Post by aheicher on 2007-02-16
thanks guys-is ubuntu uninstallable?
if I hit the partitioning option in the gui ubuntu installer, it wont delete all my data right?
This is a family computer
AH
Also, something may be off with my MD5 sum-I never get the ubuntu load screen when it is booting, all i get is a blinking underscore in the upper left-hand corner.  should i download again-this same thing happened to me with SLAX
TY
With the partitioning thing in the installer my 3 options are:
Erase entire disk
use largest continuous free space
manually edit
ty (again)

---

### Post by hanexar on 2007-02-16
> **aheicher said:**
> thanks guys-is ubuntu uninstallable?
if I hit the partitioning option in the gui ubuntu installer, it wont delete all my data right?
Just be sure to hit the "manual partition" and make sure you don't erase your windows partition manually, you won't have a problems. 

I don't get the uninstallable thing... 

> **aheicher said:**
> Also, something may be off with my MD5 sum-I never get the ubuntu load screen when it is booting, all i get is a blinking underscore in the upper left-hand corner.  should i download again-this same thing happened to me with SLAX
TY

Make sure you have the same MD5sum before burning your LiveCD, and you won't have problems.

---

### Post by aheicher on 2007-02-16
by uninstalling i mean removing ubuntu from my hard drive, including the partition
what is the correct MD5sum
3d0310e32d0b174a312ed2c1f7ec022b-/dists/edgy/main/binary-i386/Release

---

### Post by hanexar on 2007-02-16
Yes, It can be easily remove. Just format the partition to FAT32 systems.

But I don't know a way to reform only one partition with windows.
In the worst case, you'll have two partitions on windows. a C: where windows is installed, and D: for your files, which is a good thing: Like that you can format windows without loosing everything.

---

### Post by hanexar on 2007-02-16
for the MD5sum

[https://help.ubuntu.com/community/HowToMD5SUM#head-0e24f0b47485dda966483fe6b4afb79c6531114c](https://help.ubuntu.com/community/HowToMD5SUM#head-0e24f0b47485dda966483fe6b4afb79c6531114c)

---

### Post by aheicher on 2007-02-16
got it-mine is b950a4d7cf3151e5f213843e2ad77fe3

---

### Post by hanexar on 2007-02-16
You need to compare it with the file on your LiveCD, as told in the HOWTO.

---

