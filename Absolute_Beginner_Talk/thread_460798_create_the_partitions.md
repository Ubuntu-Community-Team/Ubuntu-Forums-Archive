---
title: "create the partitions"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by enfantterrible on 2007-06-01
hello all and sorry if this has been asked already, but couldn't find the detail i needed!

decided to install ubuntu in dual boot with winxp. my winxp now is on a 80GB harddisk (ide1) and all the data in a FAT32 320gb (ide2) that i want to use as a shared data repository.

my idea is to split the 80gb into 2 40gb partitions for the 2 OS (plus a 2gb swap partition).

question now is... all the tutorials i have found show you the "theory" on how to partition, but never how to ACTUALLY do it in the ubuntu 7.04 install.

i go for "manual" since the automatic wants to install ubuntu on the ide2 (the data) drive, that i instead want to leave as is.

so, after manual i see my two hd but then i dont know if i have to edit partitions, create partitions etc... if i chose to edit it asks me what size but i have no clue if it's asking me the size of the new partition of the size of the old one etc... it's just a big mess and i cant afford to lose my winxp partition at this moment.

do anybody have a step by step (with screenshots is better..) of the right procedure to split my ide1 in half and leave the xp half alone?!


thanks

---

### Post by sankarv on 2007-06-01
You have some screenshot based installations here. hope this might help you.


[http://www.howtoforge.com/ubuntustudio_7.04]("http://www.howtoforge.com/ubuntustudio_7.04")

[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")


i think your ide1 will recognized as hda and ide2 as hdb. the partitions are labelled as hda1,hda2,etc and hdb1,hdb2,etc...


you need atleast 4GB freespace for installing Ubuntu. so you must have that much amount of free space for creating partitions.

those links might help u....

---

### Post by Kobalt on 2007-06-01
Hello,

You'll find a step by step illustrated guide on installing Ubuntu [here]("http://www.psychocats.net/ubuntu/installing"). It also explains partitioning very well.

---

### Post by enfantterrible on 2007-06-01
hi guys thanks both for help

unfortunately i had already checked those websites and - although they give a nice overview of WHAT partitions are and how to set them up "in theory", they still lack the level of detail i was looking for.

so, to make a direct question: you have an 80 gb hard drive and you want to split it in two but the automatic option does not work for you (as it suggests to put ubuntu on another drive, which you dont want to touch). which steps do you take in ubuntu 7.04 installation to resize your win FAT32 partition and create a new linux partition?

my doubts are about editing/creating etc... i dont know if i need to EDIT current partition (to make it smaller) or CREATE a new partition (a 40gb one) and so on...

thanks again... 
r

---

### Post by indytim on 2007-06-01
You can do the partitioning a number of ways:

1.  Through the installer (where you're at right now).
2.  Through the LiveCD
3.  Booting to GParted Live and manually do your partition work before installing.

My recommendation is to go the GParted Live route.  It's a good utility to have on hand irregardless of your immediate needs.  The advantage is that you boot to it and nothing else is running.  It gives a very good graphical representation of what's going on in each of your harddrives with respect to partitioning.

After you have finished your partition layout in GParted, go ahead with your installation.  At the point where you come up to the partitioning part of the install, select the manual partition.  Once there identify your /swap and "/" from the partitions you already set up.  

Here's the link for GParted Live:

[http://gparted.sourceforge.net/index.php]("http://gparted.sourceforge.net/index.php")

As I said at the outset, this is one of several approaches to your partition issue.

Also, as is frequently mentioned on the boards here.... defragment, defragment and backup before doing any partition work.

Good Luck,

IndyTim

---

### Post by enfantterrible on 2007-06-01
good tip, thanks ! 

anyway... i defragmented once last night (took it all night! - europe here) cause i moved approx 20 gb of data to the 320gb hard disk... i hope defragmenting once is enough, as i heard people saying to defrag more!

thx

---

### Post by toontastic on 2007-06-01
I did it twice on mine cause I had heard of problems people had still had after doing it once. I do the defrag through safe mode though and it seemed to run much quicker than just doing it normally in windows.

---

