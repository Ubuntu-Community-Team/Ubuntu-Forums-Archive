---
title: "Partition...basic Q"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by john.n on 2007-01-10
Iv been trying to get it to automatically partition my hdd, but it wont work. So using the gparted option on the live cd...what exactly does "Remember to assign at least one partition for swap space and to mount a partition on /." mean. Mostly about the "/" partition. Any help would be great, thanks.

---

### Post by meng on 2007-01-10
/ is where the main filesystem (the Ubuntu OS) resides. Therefore, you obviously need to allocate space for it!

---

### Post by bodhi.zazen on 2007-01-10
/ is the root partition

/ = C:\

This is where you will install Ubuntu.

---

### Post by john.n on 2007-01-10
You both just said diff things...? bit coonfused

---

### Post by Sef on 2007-01-10
Swap is for when your system runs out of ram and needs more memory.   It should be double the ram.  Over 1 gb it is not really necessary unless you do video editing or heavy gaming.

Update: > / is where the main filesystem = > / is the root partition=> / = C:\ c: is for Windows root; / is for Linux root.

---

### Post by john.n on 2007-01-10
now i makes more sense

---

### Post by meng on 2007-01-10
> **john.n said:**
> You both just said diff things...? bit coonfused
No we both just said the same thing. We phrased it differently. I suggest you do some reading into Linux filesystems, it is a change from other OSes, by which I mean it's different from Windows.
[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)
This is a start. Google has more to say on the subject.

---

### Post by john.n on 2007-01-10
does the swap partition need to be "linux-swap" type, and is the main one fat32 or....?

---

### Post by Sef on 2007-01-10
> now i makes more sense

Glad it does. 

Please post any other questions that you have.

---

### Post by meng on 2007-01-10
> **john.n said:**
> does the swap partition need to be "linux-swap" type, and is the main one fat32 or....?
The swap partition should be linux-swap. The main one should be ext3, unless you have a strong preference for reiserfs or xfs.

---

### Post by john.n on 2007-01-10
ok, cant do a partition. Wont let me make the main one smaller so i can create the new two...? Any ideas (or should i just give up on ubuntu?)

---

### Post by meng on 2007-01-10
Well there are a number of reasons this may be the case, and you haven't given us any clues to work out what's going on. I wonder whether your main partition may be Windows, in which case it is possible that the drive is fragmented, with data at the end of the partition, therefore making it impossible to resize it. It is generally recommended that you run Windows disk defragmenter at least once before attempting a repartitioning. Even then, sometimes Windows identifies "immovable" data that can't be shifted to another part of the drive.

---

### Post by bodhi.zazen on 2007-01-10
LOL john.n

Sorry for the confusion there. Made sense to us Linux Heads :p

To Install:

Defragment your hard drive (from windows)

Back up critical data (although data loss is rare)

Then follow this guide:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

You may also want to look at this:

[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

Or for Edgy:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

---

### Post by housam on 2007-01-11
Try to read [this site ]("http://community.linux.com/howtos/Partition/index.shtml")for partitioning your HDD, It w'll explain every thing.

---

### Post by housam on 2007-01-11
Do the defrag once more and look for the unmovable data green mark(windows system files)where it is , because you can't partition the HDD before resizing it to just before that mark or you will damage windows.that means if it is located in the middle , your windows partition will be not less than the half of its capacity . leaving the rest of the HDD unallocated.
You can use Gparted tool to do the partitioning manualybefore starting the installtion( it is in the live CD >> system >>.
During the installation process chose the manual partitioning to just put every thing in the right order.
You need to devide the unallocated part to three partitions  :
- 10 - 15G ext3 /. for root
- 1G swap
- The rest Gb is ext3 for /home
Good luck

---

### Post by Sef on 2007-01-11
> - 1G swap

How much swap depends on your ram.  It should be double your ram.  However, if you have a gb or more of ram then it isn't really necessary unless you do video editing or heavy gaming.

---

