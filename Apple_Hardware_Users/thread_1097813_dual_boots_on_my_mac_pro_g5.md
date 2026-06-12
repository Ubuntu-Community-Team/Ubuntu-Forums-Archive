---
title: "dual boots on my mac pro g5"
date: 2009-03-16
forum: Apple Hardware Users
---

### Post by bigfefan on 2009-03-16
okay, I installed ubuntu on my macpro g5 in the basement. it is PPC. I gave ubuntu the entire hard drive. mac os is completely gone. What I want to do is make it so that when I turn the computer on, I get a menu that lets me pick other distros. I want the macpro on a dual boot of ubuntu and kubuntu. how do I do that?

btw how much ram and cpu does kubuntu need to run well?

---

### Post by tiresia on 2009-03-16
You have a PowerMac G5. A MacPro is the same case but an Intel Processor
I don't understand in your post, if you still want to run MacOSX on your Mac or you want to have just Ubuntu and Kubuntu.
Can you please post as well more info about your computer (RAM, Processors and so on...) Anyway you won't have any problem running both systems

---

### Post by bigfefan on 2009-03-16
> **tiresia said:**
> You have a PowerMac G5. A MacPro is the same case but an Intel Processor
I don't understand in your post, if you still want to run MacOSX on your Mac or you want to have just Ubuntu and Kubuntu.
Can you please post as well more info about your computer (RAM, Processors and so on...) Anyway you won't have any problem running both systems

oh you're right. it's a powermac. and mac os is gone. I don't want mac os. how do I make dual boots of different distros? (kubuntu was an example, I really j=want ubuntu and opensuse)

it's got 512 mb ram and like 900mhz cpu or something. runs ubuntu just fine

---

### Post by tiresia on 2009-03-16
You just need to make two partitions with parted and install the two OS's on each of them. I would suggest you to install OpenSUSE as first in the first partition.

When you start from the CD to install the second GNU/Linux System, let's say Ubuntu, don't choose automatic installation otherwise you will get twice the Apple_Bootstrap partition and the Swap partition.
Choose to set manual the partitions, and use the three partitions of SUSE that you can use for both Systems. 

You should read some docs to get more info about this.
[http://ubuntuforums.org/showthread.php?t=994882](http://ubuntuforums.org/showthread.php?t=994882)

---

### Post by bigfefan on 2009-03-19
> **tiresia said:**
> You just need to make two partitions with parted and install the two OS's on each of them. I would suggest you to install OpenSUSE as first in the first partition.

When you start from the CD to install the second GNU/Linux System, let's say Ubuntu, don't choose automatic installation otherwise you will get twice the Apple_Bootstrap partition and the Swap partition.
Choose to set manual the partitions, and use the three partitions of SUSE that you can use for both Systems. 

You should read some docs to get more info about this.
[http://ubuntuforums.org/showthread.php?t=994882](http://ubuntuforums.org/showthread.php?t=994882)

...say I installed hardy first with the entire hard drive. Would I have to start over or can I edit the partitions within hardy and install suse on one of them?

and although you've been incredibly helpful, I still want to know my minimum system requirements for using the effects in KDE 4.2

and by any chance have you had any luck with playing embedded media (youtube, dailymotion, etc) on ppc? I installed gnash and it doesn't do anything ever. I still have to download every video I wanna watch, even though it says that gnash works with youtube. and if u don't know, can you direct me to another place where I could ask that one?

---

### Post by tiresia on 2009-03-19
> **bigfefan said:**
> ...say I installed hardy first with the entire hard drive. Would I have to start over or can I edit the partitions within hardy and install suse on one of them?
Installing Linux on a PowerPC requires at least 4 Partitions (3 if you don't use a swap partition - this is possible but not advisable). 
1. Apple Partition Map
2. Apple Bootstrap Partition
3. GNU/Linux OS
4. Swap Partition

You want to have a Dual Boot with two different Linux Distros. This means that, if you let the installer partitioning for you the HD, you will get 4x2=8 partitions. This can work, but it doesn't make any sense, and you will loose a lot of space. 
A possible solution is: 
1. make two unformatted partitions
2. install say OpenSUSE on the first space, letting the installer make and formatting partitions as it likes
3. when you are ready with the first install, start from UBUNTU. Choose now to edit manually your partitions. Now you can set the already formatted as you need, and add a new partition for UBUNTU root.
It should look like this (sorry for my english!!!)

/dev/sda1 Apple Partition Map
/dev/sda2 Apple Boostrap
/dev/sda3 OpenSUSE
/dev/sda4 Swap
/dev/sda5 UBUNTU

This way the two OS's share the three partitions they can use together 

> I still want to know my minimum system requirements for using the effects in KDE 4.2 I don't know so well KDE, but I guess you shouldn't have problems with it (by the way, you say you g5 as a 900 MHz Processor, it is not possible - there isn't any PowerMac like that)
> and by any chance have you had any luck with playing embedded media (youtube, dailymotion, etc) on ppc? I installed gnash and it doesn't do anything ever. I still have to download every video I wanna watch, even though it says that gnash works with youtube. and if u don't know, can you direct me to another place where I could ask that one?
This is really a problem on such machines (this forum has plenty of threads about this issue) 
On my PowerMac g5 and now on my PowerMac g4 I can watch video in YouTube, but I think I'm quite lucky, the quality is not good, and Gnash takes too much power. You can download anything you need with 'clive' (or similar tools) or if you really need a really working flash, you should think to keep together with OpenSUSE and Ubuntu also MacOSX.

---

### Post by bigfefan on 2009-03-20
> **tiresia said:**
> 
It should look like this (sorry for my english!!!)

/dev/sda1 Apple Partition Map
/dev/sda2 Apple Boostrap
/dev/sda3 OpenSUSE
/dev/sda4 Swap
/dev/sda5 UBUNTU

This way the two OS's share the three partitions they can use together 

 I don't know so well KDE, but I guess you shouldn't have problems with it (by the way, you say you g5 as a 900 MHz Processor, it is not possible - there isn't any PowerMac like that)

This is really a problem on such machines (this forum has plenty of threads about this issue) 
On my PowerMac g5 and now on my PowerMac g4 I can watch video in YouTube, but I think I'm quite lucky, the quality is not good, and Gnash takes too much power. You can download anything you need with 'clive' (or similar tools) or if you really need a really working flash, you should think to keep together with OpenSUSE and Ubuntu also MacOSX.

Well, opensuse and kde seem to really suck. no apple keyboard layout, I couldn't even get the disc out! had to restart holding alt to eject it. I reinstalled hardy. will jaunty be a good idea, for my system?

your english is fine. what's your mother tongue?

and why does gnash use too much power?

---

