---
title: "Ubuntu Installation Not Detecting Vista Partitions"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by Andrew Garn on 2007-08-27
I'm trying to dual boot ubuntu 7.04 with my current installation of Win Vista Business.

I boot off the live CD and go to install, but when it gets to the "prepare disk space" section i only get the following options:

Guided - use entire disk space
     SCSI1 (0,0,0) (sda) - 320.1 GB ATA WD3200AAKS-7
     SCSI2 (0,0,0) (sda) - 320.1 GB ATA WD3200AAKS-7
Manual

There is no guided - use biggest free unformatted space option for me to select

so i click on manual and it tells me both of my disks are 320gb of unpartitioned space.

My windows vista configuration has the following disk partitions:

10gb Partition
30gb UnPartitioned Space
~550 Gb Boot Partition (c)

---------

So any suggestions to how to install ubuntu without formatting and removing vista?

I think the problem might be something to do with vista creating 1 partition that encompasses both of the hard disks and ubuntu cant handle that?

Help would be appreciated, ask if you need any more tech details.

---

### Post by henriette_holm on 2007-08-27
Do you have some sort of raid setup?

/Henriette

---

### Post by Andrew Garn on 2007-08-27
I've not come across that term before - how do i tell?

the pc came from dell preinstalled in this way.

[IMG]http://img512.imageshack.us/img512/9365/disksiq0.png[/IMG]

---

### Post by schorsch on 2007-08-27
I'd guess there is some kind of RAID involved as the Ubuntu installer detects two drives with 320 GB resp. and here you have one filesystem with 560 GB .... and man, that is a really large pic .... ;-)

---

### Post by Andrew Garn on 2007-08-27
22" widescreen :) - i guess i should resize it

I know the pc has two seperate physical hard disks if that helps.

---

### Post by henriette_holm on 2007-08-27
So you have to physical disks in the pc? Then it looks like some sort of raid. I'm sorry, but I have absolutely no experience with that.
Normally you would do a setup something like this for dual boot:

Partition1: C: (Fat32 or NTFS)
Partition2: D: (fat32 - for data sharing)
Partition3: / (ext3)
Partition4: Extended partition
Partition5: /home
Partition6: swap

Doing the above will delete your current setup, so please don't if you're not sure. I hope someone else can help you with the raid setup.

/Henriette

---

### Post by Andrew Garn on 2007-08-27
OK Thanks for replying. I'll see if anyone else has any opinions

---

### Post by Andrew Garn on 2007-08-27
> **Andrew Garn said:**
> OK Thanks for replying. I'll see if anyone else has any opinions

anyone?

---

### Post by por100pre1 on 2007-08-27
The problem is that you have 3 partitions in your Disk 0. You can only have 4 primary partitions in your HDD. Ubuntu needs to be able to create 2 partitions in order to enable the *guided - use biggest free unformatted space* option, one for Ubuntu files and one the swap file (the virtual memory or pagefile in Linux). You'll need to either get rid of one partition and move the rest (no easy task) or use the Manual option in ubuntu installer, and setup logical partitions for Ubuntu and the swap file. Hope this helps somehow. :)

---

### Post by Andrew Garn on 2007-08-27
> **henriette_holm said:**
> So you have to physical disks in the pc? Then it looks like some sort of raid. I'm sorry, but I have absolutely no experience with that.
Normally you would do a setup something like this for dual boot:

Partition1: C: (Fat32 or NTFS)
Partition2: D: (fat32 - for data sharing)
Partition3: / (ext3)
Partition4: Extended partition
Partition5: /home
Partition6: swap

Doing the above will delete your current setup, so please don't if you're not sure. I hope someone else can help you with the raid setup.

/Henriette

I am now copying files off my computer in preperation to format it all.

Would anyone like to explain to me how and which partitions to create for installation of vista/ubuntu and possibly xp as well?

---

### Post by silverglade00 on 2007-08-27
> **Andrew Garn said:**
> I am now copying files off my computer in preperation to format it all.

Would anyone like to explain to me how and which partitions to create for installation of vista/ubuntu and possibly xp as well?

Just a note: While doing this, you could very possibly be breaking the RAID setup. This will more than likely have the fun effect of killing your Windows install too. You will probably have to reinstall both operating systems (Vista first) and you could have problems getting the RAID going again if the machine is setup to force it. With that much space on your RAID drives, you might want to consider VMWare or some other VM program to run Ubuntu virtually.

---

### Post by Andrew Garn on 2007-08-27
i dont understand what raid is doing for my computer anyway

and yes i was going to reinstall all 3 from scratch

can you see any problem with this?

if i start using ubuntu live cd to partition the two disks which partitions do i create?

ideally i need to be able to share files between all 3 o/s's

is this tutorial good: [http://ubuntuforums.org/showthread.php?t=220452?](http://ubuntuforums.org/showthread.php?t=220452?)

---

### Post by Andrew Garn on 2007-08-27
[http://ubuntuforums.org/showthread.php?t=536485](http://ubuntuforums.org/showthread.php?t=536485) is another question if anyone wants to be helpful

---

### Post by henriette_holm on 2007-08-28
Hi Andrew.
If you need more information just ask. I can see you have been getting plenty of answers in the other thread.

/Henriette

---

### Post by Termy58 on 2007-09-05
I am also having this issue and I don't know exactly what to do, I just uninstalled my Wubi build and tried this I also tried Wubi on my lap top and that didn't work for a differant issue, am I just increadibly unlucky or is this common?

---

### Post by henriette_holm on 2007-09-05
Could you tell us a bit more. What are you trying to do? Your hardware setup? etc.


/Henriette

---

### Post by Termy58 on 2007-09-05
> **henriette_holm said:**
> Could you tell us a bit more. What are you trying to do? Your hardware setup? etc.


/Henriette

Well I just want to dual-boot. When I try to I don't have the top option only the Use entire disks options and Manual.

---

### Post by henriette_holm on 2007-09-06
ok, if you want to dual boot you have to have one of two things:

1) One disk with Windows installed on a partition, that doesn't take up the whole disk

2) Two disks - one with Windows and one for Ubuntu.


Make sure you have the Windows installation done first. If you have this you want to pick the manual partition option. You can read a bit more here:

[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty)

Please notice that the article comes in three parts. Have  a look through the whole thing to make sure which one you need.

/Henriette

---

