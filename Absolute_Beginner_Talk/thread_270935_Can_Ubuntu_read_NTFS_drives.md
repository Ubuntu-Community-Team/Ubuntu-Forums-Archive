---
title: "Can Ubuntu read NTFS drives"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by delphiguy on 2006-10-04
Hi,

Im extremely new to Linux and Ubuntu.  And currently am downloading Ubuntu Desktop.  

I want to format my home machine and remove WindowsXP from it and install Ubuntu instead.  However I have a few questions.

Can Ubuntu read my NTFS formatted harddrives or do I have to reformat it in a Linux Partition?

Also I would still like to run my WindowsXP in a Virtual PC.  Is there a software that would let me do this, similar to VWWare?  

TIA
Randy

---

### Post by Imsati on 2006-10-04
> **delphiguy said:**
> Hi,

Im extremely new to Linux and Ubuntu.  And currently am downloading Ubuntu Desktop.  

I want to format my home machine and remove WindowsXP from it and install Ubuntu instead.  However I have a few questions.

Can Ubuntu read my NTFS formatted harddrives or do I have to reformat it in a Linux Partition?

Also I would still like to run my WindowsXP in a Virtual PC.  Is there a software that would let me do this, similar to VWWare?  

TIA
Randy

First, welcome to Linux and welcome to the boards.

Second, don't be hasty and delete XP right away. Linux requires a definate learning curve. Make sure you're comfortalble with the look and feel.

Third, yes, you can read NTFS with (E/K/X)Ubuntu. Further, you can make XP read ext2+3 files with a special program as well. Share and share alike:-)

Lastly, you will be given the option to resize partitions during the Ubuntu install. Perhaps make the Windows one smaller and set up a dual-boot drive? (again, for the learning curve)

Once again, welcome aboard.

~Jay

---

### Post by K.Mandla on 2006-10-04
Yes! Linux can [read and write to NTFS]("https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite"). It will require a little elbow grease though, so be prepared to get your hands dirty. To install Ubuntu fresh, you should use a blank or reformatted drive without partitions. [Dual booting]("https://help.ubuntu.com/community/WindowsDualBoot?action=show&redirect=WindowsDualBootHowTo") is a different story.

And yes, there is a [VMWare setup]("https://help.ubuntu.com/community/VMWarePlayerAndWindowsHOWTO") for Linux that you can use within Ubuntu.

EDIT: Darn. Imsati beat me to it. ;)

---

### Post by odinfromvalhalla on 2006-10-04
if you want to intall Ubuntu you will have to do it on a linux partition (i.e.: ext3 or reiserfs) not on NTFS (which is not even that good as the 2 i have mentioned).

as for virtualisation you can use  [vmware server]("http://www.vmware.com/products/server/") which is free. i use it every day. :)

---

### Post by Dual Cortex on 2006-10-04
ubuntu needs to be installed in its  own "linux format" partition. Though it can read other ntfs partitions. im a newbie too, but i do know that wine allows you to "emulate" various windows programs.

---

### Post by Titan_Prometheus on 2006-10-04
The VMWARE is one of the greatest things i've seen. I have edgy on a VM and it kicks a$$. I cant do everything, but i can do all the normal things normal people would require.

---

### Post by delphiguy on 2006-10-04
Thanks a lot for the help guys.  And thanks as well for the warm welcome:D

---

### Post by Dual Cortex on 2006-10-04
took me 7 minutes to write the above message on my psp...
btw, i also uninstalled windows  completely and installed ubuntu. the challenges make linux fun, and im starting to get hand of the basics of the terminal, sharing files÷printers to windows pc's, setting up apache/ftp servers, etc. schoolwork didnt allow me to play around with ubuntu today :(... an probably tomorrow neither. took me about 15 mins to write this post... :)

---

### Post by hyper_ch on 2006-10-04
Welcome aboard :)
I'm glad to hear you're doing so fine. I'm still a noob myself. If you have further problems just ask in here :)

---

