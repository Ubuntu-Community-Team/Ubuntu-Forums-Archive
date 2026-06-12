---
title: "Ubuntu dualboot partition"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by someguy91 on 2007-06-24
Currently I have 3 partitions. I installed vista and put it into the 2nd partition. 

Right now, I am using the alternate CD installer and confused about the partition Utility. 

1. Do i have to select a partition, a file system and a root? so do i have to select f ext3 /  or will that be done automatically later???

2. Do i have to manually set up a swap partition.. and must it be its own partition?

Your help is appreciated

---

### Post by oilchangeguy on 2007-06-24
try this:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Hobo Joe on 2007-06-24
You'll have to make space from your other partitions(s). As much as you want Ubuntu to have.

You need:
1. A partition to install Ubuntu on, like I said, make it as big as you feel like you need it to be. Format to ext3.
2. A 'swap' partition. To be honest I don't really know what it does, but I know that you need it. Make it about 2 GB. Format to 'linux swap'.

Thats it! When you install Ubuntu, just select the one you made.

---

### Post by someguy91 on 2007-06-24
Problem is that it does not give me the option of a guided install to a certain partition.

The options i get are 

Guided - use entire disk
Guided - use entire disk and set up LVM
Manual

I think I have to use manual...

---

### Post by someguy91 on 2007-06-24
> **Hobo Joe said:**
> You'll have to make space from your other partitions(s). As much as you want Ubuntu to have.

You need:
1. A partition to install Ubuntu on, like I said, make it as big as you feel like you need it to be. Format to ext3.
2. A 'swap' partition. To be honest I don't really know what it does, but I know that you need it. Make it about 2 GB. Format to 'linux swap'.

Thats it! When you install Ubuntu, just select the one you made.

ok so in manual text mode.. all i have to do is choose a partition... make it ext 3... turn it into root...?
and make another partition.. and turn it into a swap?

so after i add a swap partition i will have 4 partitions.

---

### Post by ajgreeny on 2007-06-24
If you are going to let Ubuntu partition your whole Ubuntu space according to the default, just make space of the total size you want, but don't bother to format it at all, the installer will do that automatically for you.  Now when you get to the partitioning bit of the install, chose the free space you just made and let Ubuntu make a root and swap partition for you.  The root will be ext3 and swap will show as swap, though it is ext3 as well, I think.

One warning:  Don't make the space too small thinking you will not use it much.  This system gets rather under your skin and in your blood, and you may well end up never really using windows again.  I shall certainly never again buy a copy of any type of MS Windows, unless forced to by it being pre-installed on a machine at such a good price that it is cheaper to buy with it than build a machine from scratch.

Best of luck and welcome to Ubuntu

---

### Post by someguy91 on 2007-06-24
> **ajgreeny said:**
> If you are going to let Ubuntu partition your whole Ubuntu space according to the default, just make space of the total size you want, but don't bother to format it at all, the installer will do that automatically for you.  Now when you get to the partitioning bit of the install, chose the free space you just made and let Ubuntu make a root and swap partition for you.  The root will be ext3 and swap will show as swap, though it is ext3 as well, I think.

One warning:  Don't make the space too small thinking you will not use it much.  This system gets rather under your skin and in your blood, and you may well end up never really using windows again.  I shall certainly never again buy a copy of any type of MS Windows, unless forced to by it being pre-installed on a machine at such a good price that it is cheaper to buy with it than build a machine from scratch.

Best of luck and welcome to Ubuntu

yea... i got a 320gb hdd... 38 for ubuntu 2 for swap 40 for vista.. rest for data... I game... so... gotta keep vista or xp or what not around :/ and we all know the GPU situation with linux in general...

Thx. I'm sure it'll be a great time :) Planning on using it fulltime anyway... except for gaming... except for iD games... i think Valve games can be run on linux too meh :)

GRUB installed itself perfectly. and I was worrying it was gonna be ugly heh.

---

