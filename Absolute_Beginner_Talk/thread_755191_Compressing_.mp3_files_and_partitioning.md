---
title: "Compressing .mp3 files and partitioning"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by SigmaHog on 2008-04-14
2 Questions:

1: If I want to compress my music library (over 1700 songs) from windows then load it onto Ubuntu... what is the best way to do it?

2: Also, I want to dual boot Ubuntu before I do away with windows completely to see if I can do everything I need to without relying on crappy windows.... How do I go about doing that from windows? I've tried in Ubuntu but it said I didn't have enough space so I've deleted a few unessecary things and once I partition, can I change the sizes later?I have a 40GB HDD but plan on getting a bigger one because my music library is so big and I can't live without it :(

---

### Post by Aeph on 2008-04-14
As far as the music goes, once you install Linux, you can easily mount your Windows partition and access the files that way, without having to copy them.

---

### Post by conscious on 2008-04-14
If you have Windows and Ubuntu installed on one disk, there will be no need to transfer files. You just mount the Windows partition from Ubuntu and access the files. Or, alternatively, you can just copy them to Ubuntu partition.

You will need to have several GB free on your drive in order to create a new partition and install Ubuntu on it. The disk can be repartitioned later, for exapmle, with gparted.

---

### Post by stchman on 2008-04-14
> **SigmaHog said:**
> 2 Questions:

1: If I want to compress my music library (over 1700 songs) from windows then load it onto Ubuntu... what is the best way to do it?

2: Also, I want to dual boot Ubuntu before I do away with windows completely to see if I can do everything I need to without relying on crappy windows.... How do I go about doing that from windows? I've tried in Ubuntu but it said I didn't have enough space so I've deleted a few unessecary things and once I partition, can I change the sizes later?I have a 40GB HDD but plan on getting a bigger one because my music library is so big and I can't live without it :(

Yes mounting NTSF and FAT32 partitions is a snap in Ubuntu.

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

Also mp3s are already compressed so I don't understand compress your library.  Yes 40GB is too small in today's age and especially since you have 1700 songs.  You will need to give Ubuntu at least 10GB when you install.  Make sure you make free space when you install. and select free space on the installer.

---

### Post by northern lights on 2008-04-14
For a complete Gutsy installation, official minimum requirements are given as 4GB including swap space.

Since you most likely will want to run a few apps from Ubuntu right away, I'd say anything under 5GB for the Linux ext3 wouldn't be too sensible. But you could do with 3, if that's all you can afford. 
My system, for instance, is right now is 10.8 gig large, including a 7 gig home folder - meaning the OS & a good number of apps amount to 3.8 gig.

The necessary size of your swap (this is the equivalent of the pagefile in windows - virtual memory, and a separate partition in Linux) highly depends on the size of your physical memory, i.e. RAM, and the sort of apps you want to run. In general, I'd say a gig is about right, but since you're space is limited you could do with less. How much RAM do you have?

Bottom line is, free between 4 and 10 gig, however much you can afford, and install Ubuntu. It should actually mount your windows partition (all ntfs partitions) out of the box.

Two tips:
1. If you're not too happy with your Windows (old installation, slow, infected, etc...) and nevertheless plan on dual booting for a good while, it might be a good idea to do a fresh Windows install before setting up Gutsy. When installing Linux, it adds a bootloader (in this case GRUB), which will include an option to boot Windows. When installing Windows, it rewrites the MBR and you will have to deal with recovering GRUB to boot your Ubuntu.
2. Especially if you plan to follow the idea of reinstalling WIndows, but also in general, it might be a good idea to store your music on a separate partition anyway. It should be ntfs also, since then both Windows and Ubuntu will read from and write on it out of the box. It gives you the freedom to easily un/reinstall Windows.

---

### Post by freackout on 2008-04-15
> **SigmaHog said:**
> 2 Questions:

1: If I want to compress my music library (over 1700 songs) from windows then load it onto Ubuntu... what is the best way to do it?

2: Also, I want to dual boot Ubuntu before I do away with windows completely to see if I can do everything I need to without relying on crappy windows.... How do I go about doing that from windows? I've tried in Ubuntu but it said I didn't have enough space so I've deleted a few unessecary things and once I partition, can I change the sizes later?I have a 40GB HDD but plan on getting a bigger one because my music library is so big and I can't live without it :(

use a2mp3 (a2mp3 --help shows how) also use mpck or checkmp3 or mp3check however mpck -q -B -R *.mp3 > mymp3bad.txt shows document that contains corrupted mp3's u may wanna get rid of those first.. ps aint found an easy way to delete them all in one go though... leave feedback.

---

### Post by mozetti on 2008-04-15
mp3 files are already compressed. You're really not going to be able to squeeeze them down much farther (if at all).

---

### Post by freackout on 2008-04-15
> **stchman said:**
> Yes mounting NTSF and FAT32 partitions is a snap in Ubuntu.

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

Also mp3s are already compressed so I don't understand compress your library.  Yes 40GB is too small in today's age and especially since you have 1700 songs.  You will need to give Ubuntu at least 10GB when you install.  Make sure you make free space when you install. and select free space on the installer.

use a2mp3 compresses further ie optimized mp3 but u loose some sound try on a song see if u like the diffrence about 3/4 size of original mp3.... also use mpck - q -B -R *.mp3 > mylistofbadmp3s.txt

then read the txt file this should save u a packet.......
from freackout.

---

### Post by Trail on 2008-04-15
> **freackout said:**
> use a2mp3 (a2mp3 --help shows how) also use mpck or checkmp3 or mp3check however mpck -q -B -R *.mp3 > mymp3bad.txt shows document that contains corrupted mp3's u may wanna get rid of those first.. ps aint found an easy way to delete them all in one go though... leave feedback.
How about awk? Something like

```

awk '<filters> {system("rm " <column>)}'

```

---

