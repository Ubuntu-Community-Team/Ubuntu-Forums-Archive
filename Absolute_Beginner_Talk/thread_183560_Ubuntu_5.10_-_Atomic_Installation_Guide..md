---
title: "Ubuntu 5.10 - Atomic Installation Guide."
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by ATOMIC2 on 2006-05-28
Here in Australia, we have a magazine called, Atomic. In their lastest issue they wrote out a detailed guide to installing the current version of, Ubuntu. I've followed their guide exactly and have been running a very smooth and happy OS. I've been so pleased with it, I've decided to totally dump, Windows and run the Ubuntu Linux distribution on all 3 PC's in my home. However, before I do this, I need to troubleshoot a problem I had come accross today.

Luckily enough for me, in their guide, their HDD happens to be the same brand and size as the one I've been testing on. The following is their partition setup of, Ubuntu and mine.

```
IDE1 master (hda) - 120GB WD
#1 primary - 98.7mb - /ext3
#2 primary - 119.9GB - lvm

LVM VG ubuntu - lv home - 3.2GB
#1 - 3.2GB - XFS - /home

LVM VG ubuntu - lv root - 3.2GB
#1 - 3.2GB - XFS - /

LVM VG ubuntu - lv swap - 2.1GB
#1 - 2.1GB - swap - swap
```

My problem is, everything i've downloaded and installed and transfered over from another PC has almost filled my #1 primary while my #2 primary still has 111GB of space left on it.

How can I utilize the space remaining on #2 primary so my HDD or #1 primary doesn't have to cop it all?

> Don't worry that we're not using all of your hard drive space - we can tweak things later when you need more storage. - Extract from the guide.

They intend to make a follow-up guide next month, but we're looking mid next month and i'd like to know how to get some free space asap.

[http://www.atomicmpc.com.au/forums.asp?s=2&c=16&t=3906](http://www.atomicmpc.com.au/forums.asp?s=2&c=16&t=3906) - Similar post I've made on the magazines official forums.

Thanks in advance!
Christopher van Dal.

---

### Post by catlett on 2006-05-28
They set up your install with lvm. lvm lets you distribute free space to partitions when needed. this documentation should tell you how.[http://tldp.org/HOWTO/LVM-HOWTO/](http://tldp.org/HOWTO/LVM-HOWTO/)

P.S. I would start next time with at least 20gb for home, the rest are fine but if you have the space.
Swap is like windows swap file, it is used as ram when your ram is maxed out. You shouldn't need more than 512mb for regular use . Your root is the base system and any new programs, Since you have space do 10gb. And for home do at least 20gb. You should do the rest of the disk but it doesn't matter when you install with lvm.  lvm can resize without data loss.

---

### Post by gommle on 2006-05-28
Programs --> Accessories --> Terminal
```
sudo apt-get install gparted
sudo gparted
<insert user password>
```

Now you should select your HD and click something like "New Partition". Just select max size if you arent planning to dual-boot. If you are planning to install another OS, choose a few gigs less than max. Filesystem ext3. Its readable by windows if you install ext2ifs on windows xp.

I cant give exact howto now because ive got no space left to format.

---

### Post by ATOMIC2 on 2006-05-29
What are the benifits of using LVM? Is their a performance increase in some way compaired to just simply having your root, home and boot in the 1 partition and another partiton for the swap area?

---

