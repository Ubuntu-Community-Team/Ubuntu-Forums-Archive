---
title: "Stupid question about double boot"
date: 2009-02-20
forum: Apple Hardware Users
---

### Post by Romu on 2009-02-20
Dear all,
I've been using my Macbook Pro with Ubuntu, exclusively, for more than 2 years now. But I need to use Sketchup and as it doesn't work with the ATI I'm thinking about installing a double boot Tiger/Ubuntu.

My question is about upgrading Ubuntu, I don't trust the upgrade processes, and so I always do a fresh install for Ubuntu.

So I wonder if I'll have to re-install the whole computer (rEFit + OSX + Ubuntu) for a new Ubuntu, or if, once rEFit + OSX done, I'll be able to only redo the fresh Ubuntu installation without breaking the rest of the disk.

Thanks in advance for the help.

---

### Post by pedja_portugalac on 2009-02-20
I presume you must first make partitions for any OS you plans to install, for example with gparted live CD. After that you just install OSs and in the end ubuntu will install GRUB loader so you can choose into which system to boot.

---

### Post by lukjad on 2009-02-20
**From what I know** installing a new version of Ubuntu is just like installing it the first version. I have never installed Ubuntu on a Mac, but that should not be much different. If you have the other two OSes installed first, and then reinstall Ubuntu on itself, the only thing you should be affecting is Ubuntu. The only possible problems I can see is if you were to choose to install on the wrong partition, or GRUB, for some rare reason does not recognize the other OSes. If you have Ubuntu already installed, there should really be no problem there. 

It is recomended to always have backups of all important data, if just to save yourself from human (or whatever species you belong to) error. :D

So, basically, if you are careful, there should be no problem.

---

### Post by cyberdork33 on 2009-02-20
I really think that you should be able to get sketchup working, but anyhow

get any data off the Ubuntu partition that you want, then boot from the OSX Install DVD, and start Disk Utility. There you can completely reformat the hard drive, starting from scratch. I would recommend creating two partitions, one for OSX, and the other a FAT32 partition that will be replaced by Linux later.

Once you have done that, and finished the installation of OSX, install refit. (It is also a good idea to create a refit cd so that you have it in case the installed version does not work. See the refit website for details). Now boot the Ubuntu LiveCD, start the partition editor (gparted) and delete that FAT32 partition you created, leaving free space. Then start the ubuntu installer and choose to install to the "largest free space", choosing to install GRUB to the Ubuntu partition rather than the MBR. After that, you need to sync the partition tables with refit and you should be good to go. See:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

---

### Post by Romu on 2009-02-20
Thanks for all of you.

Cyberdork33, if you have a solution to run Sketchup, no problem, I'm your man. Indeed it run, but the graphic area is all but functional. And I tried with the radeon, radeonHD and fglrx drivers.

If you know specific driver tuning to make it work, I'm hearing.


Regarding the tutorial, I read it before asking my question, but you didn't answer my main point, if I do dual boot, could I upgrade Ubuntu, with a fresh install, in the future without re-doing the whole disk?

Thanks.

---

### Post by cyberdork33 on 2009-02-20
> **Romu said:**
> Regarding the tutorial, I read it before asking my question, but you didn't answer my main point, if I do dual boot, could I upgrade Ubuntu, with a fresh install, in the future without re-doing the whole disk?
yes, in almost the exact same manner. boot the live cd, delete the Linux partitions, start installer, choose to install to "largest free space".

---

