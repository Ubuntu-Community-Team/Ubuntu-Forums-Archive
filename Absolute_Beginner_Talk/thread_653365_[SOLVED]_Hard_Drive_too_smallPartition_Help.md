---
title: "[SOLVED] Hard Drive too small/Partition Help"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by fireboy129 on 2007-12-29
I just got into Ubuntu. Im trying to dual boot w/ Windows cause i have games, music... stuff like that. i have an 80GB hard drive, and i have 11GB free. i get to step 5 of the install, the bit about partitioning, and it says that the free space that i'm trying to install on is too small. how much space do i need? its really starting to bug me.

ive already defragmented.

plz plz help. thanks already.
JRT

---

### Post by bunnynuts on 2007-12-29
I have installed on less space. Before we get into using other utilities to partition the drive before installation please answer the following. Are you running windows XP or Vista? Is your disk already partitioned? If so, did you create the partitions or did they come from a factory install (Dell usually has some odd partitioning going on). Finally, if it is partitioned, how many are primary partitions?

Thanks

---

### Post by taurus on 2007-12-29
You need about 2.5GB if you install Gnome.  Then, you probably need some space for swap partition.

---

### Post by fireboy129 on 2007-12-29
running XP. sorry... forgot 2 say that.

it is a dell, but i have no idea if its partitioned or not and i dont know how to tell. do u know? thanks.

---

### Post by fireboy129 on 2007-12-29
plz help!

just bumpin.

---

### Post by taurus on 2007-12-29
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

p.s.  Words of caution.  _ALWAYS_ back up your important files before you resize your harddrive.

---

### Post by Moop on 2007-12-29
Boot from the live cd and go to System-Administation-Partition Editor. There you will see the partitions on your hard drive. 

The Vista Partition will need to be resized to make room for Ubuntu.The free space on your hard drive needs to be a separate partition.

---

### Post by fireboy129 on 2007-12-29
its not that.

even if i try to do it manually, it doesnt work. ill post again in a minute once i get ubuntu loaded up again. thanks.

---

### Post by phuck_windows on 2007-12-30
I have a similar problem.  I was able to dual boot Ubuntu 7.10 and Windoze XP pro SP2 using this how to: [http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu) .  Being I only want XP for Dreamweaver and ConvertxtoDVD i decided I would give XP 20 gigs and Ubuntu 80.  Unfortunately it backfired on me and I gave XP the 80 and  Ubuntu the 20.  Can anyone help me fix this?  Sorry if this is in the wrong place and if so please move it.  I will also have you know I am a newb with Ubuntu (3 days) but very proficient in XP.

---

### Post by hums07 on 2007-12-30
> **fireboy129 said:**
> 
even if i try to do it manually, it doesnt work. ill post again in a minute once i get ubuntu loaded up again. thanks.
It might be not defragmented well. Try defragmenting with JkDefrag. When Windows is shut down, it writes personal settings, so the contiguous free space may not be 11 GB any more.
Try not using all the free space (which is 11 GB), 5 GB of space is sufficient just for Ubuntu.

---

### Post by bunnynuts on 2007-12-30
There are several problems that could be causing this. As you have a Dell, it may be that you have 4 primary partitions (not all of which are needed) and you therefore can not make any more. To view these in XP, right click on 'My Computer' and choose 'Manage.' Next, click on Disk Management on the left side (under 'storage' I believe). This should show you the partitions on your drive. If you see that there are 4 you may have a problem (likely they are all primary). Dells often have the root partition for XP, a small partition that may cause problems with booting if deleted, a restore or 'D' partition, and then another blank primary partition. You have many options, but if you have 4 primary partitions one needs to become your root installation for Ubuntu and the other can become the swap, or you can make into a logical and use part of it for swap. 

Having typed all of that...this may not be the problem. 

As was stated before, if you are not comfortable with what you are doing be sure you have backed up your files...and spend some time ensuring that you have backed up all of them! 

It looks like you have a lot of help here, so let us know what you find.

---

### Post by fireboy129 on 2008-01-03
bunnynuts, i love you forever.

IT'S ALIVE!!!

but my internet's not.

---

### Post by bunnynuts on 2008-01-04
Glad to hear that it is working for you. 

Now, if you installed ubuntu without an internet connection, chances are that the repositories will not be available to you. I do not understand the reasoning behind this (not to say it is bad, just that I have not looked into why it is) but when you install without a recognized internet connection the repository list has all the repositories commented out. So you have to go through it an delete the # symbol before each repository that you want enabled. 

You can find the file at /etc/apt/sources.list

---

### Post by fireboy129 on 2008-01-04
not sure what you mean...

i have a wireless card, a linksys wireless-G PCI adapter. it won't connect to my home network...

i enter in the network name, it scans, and says the network and the name, but no connection.

ARRGH!!! enough windows! give me my ubuntu!

---

### Post by fireboy129 on 2008-01-04
> **bunnynuts said:**
> Glad to hear that it is working for you. 

Now, if you installed ubuntu without an internet connection, chances are that the repositories will not be available to you. I do not understand the reasoning behind this (not to say it is bad, just that I have not looked into why it is) but when you install without a recognized internet connection the repository list has all the repositories commented out. So you have to go through it an delete the # symbol before each repository that you want enabled. 

You can find the file at /etc/apt/sources.list

it tells me access denied when i type /etc/apt/sources.list...

any advice?

---

### Post by bunnynuts on 2008-01-04
My last advice may have been premature. Once you are able to connect to the internet then you will need to update/install etc... However, enabling the separate repositories won't do anything if you do not have internet access. 

If you have internet access then check the file sources.list using the following:
```
sudo vim /etc/apt/sources.list
```

If there is a wall of # signs on the left side then all the repositories have been commented out. and you will need to uncomment them to look something like the following:

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted

```

However, if you do not have internet access yet search the forums for help, or let me know and we can see what we can do. Also, post what type of a router/wap you use, what type of encryption if any.

---

### Post by fireboy129 on 2008-01-04
got the internet to work. yay!

it was my wireless card. stupid linksys...

this is my first post on ubuntuforums from ubuntu!!! yay linux. 

thanks for your help bunnynuts.:lolflag:

---

