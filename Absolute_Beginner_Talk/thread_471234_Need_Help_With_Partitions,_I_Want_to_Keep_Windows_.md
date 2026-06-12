---
title: "Need Help With Partitions, I Want to Keep Windows &amp; My Files"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by zeonsoul on 2007-06-11
Hello everybody!
I am new in this whole Ubuntu OS.
I just got the CDs I requested at the website, and tried to install the Fiesty Fawn today.
I inserted the CD, and after selecting the first option, and waiting some time, the system started running. It was quite slow, due to the fact that the data was being obtained from a disc.
Anyway, after proceeding to the installation, I got to the part where it asks me about partitions...That is where the problem started.
I tried clicking "Create New Partition" but it only let me erase everything I had OR keep the configuration I already had.

What I want to know is...How exactly do I make another partition specially and just for Ubuntu, and still keep the Windows one with my files without being deleted?

I have tried reading other posts about how to do some of these steps, but they begin in other places where I am not yet, or that use other procedures that don't fit in my case.

Thanks in advance guys! :)

---

### Post by saxuntu on 2007-06-11
granted i'm new to linux too, but from what i read it ain't gonna happen.

---

### Post by zeonsoul on 2007-06-11
> **saxuntu said:**
> granted i'm new to linux too, but from what i read it ain't gonna happen.

What is not going to happen?
Hopefully someone will know what to do... :O

---

### Post by bodhi.zazen on 2007-06-11
LOL

Set up your partitions with gparted (it is on the feisty CD). The run the installer.

1. Back up your windows data.

2. Defragment your windows partition.

gparted : [http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Partitioning : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

---

### Post by zeonsoul on 2007-06-11
All right, I will try that out and ask if I need anything else or have some kind of problem.
Thank you very much! :D

---

### Post by veerakumar on 2007-06-11
Use PArtition MAgic or similar one to rsize partitions.

---

### Post by bodhi.zazen on 2007-06-11
> **veerakumar said:**
> Use PArtition MAgic or similar one to rsize partitions.

Partition Magic is not so good to partition with as it can cause problems with Linux.

Best to use gparted. Gparted is included on the Ubuntu CD so no need for partition magic.

---

### Post by bone43 on 2007-06-11
> **zeonsoul said:**
> All right, I will try that out and ask if I need anything else or have some kind of problem.
Thank you very much! :D

Not to scare you away but as was all ready said and cant be stressed enough Backup your important windows files just in case! :D

---

### Post by Bruce S on 2007-06-11
> **veerakumar said:**
> Use PArtition MAgic or similar one to rsize partitions.

I used Partition Magic, to resize and add partitions ready for Ubuntu. It worked very well.
Did a swap partition etc.
Highly recommended (by a 76 year old ,non geek)

---

### Post by zeonsoul on 2007-06-12
All right.
I have followed the provided links, partitioned the hard disc in different ways and the installer keeps telling me I need a place for "/". I partitioned one part of 19GB (ext3) , then, next to it, added an extended one, which contains a linux-swap one. When doing this, the partitioner does not let me complete the action: it closes automatically before closing, or says that the process could not be completed...
I am using the GNOME Partition Editor and following the manual installation.
What else do I need to do? What is wrong? Should I choose other type of installation?
I have been trying and trying since my first post and no progress...All I could achieve was partition the disk once, but not as Ubuntu installer requested...

Thanks to everyone for their help, but I just can't get it right...Apparently...

[B]EDIT: Magically, I managed to get it right using the manual installation and creating partitions for / and swap...now the problem is that after I click forward, it takes me to the "Migrate Documents and Settings" section. When I get there, it starts scanning for the information, and after a minute or less, the screen freezes and I can not get through that...Actually, I need to turn off my PC in the "improper" way, keeping the on button pressed.
Any ideas of what I should do?
Thanks in advance guys! :D[/B]

---

### Post by bodhi.zazen on 2007-06-12
Can you just say "No" to importing ?

---

### Post by sifanuba on 2007-06-12
1. Defrag the hardisk
2. Use Powerquest Partition Magic to set up the partition for linux
    Create 2 logical partition: 1. Type: ext2 2. Type: Swap
    Restart windows
3. Restart again with ubuntu cd in cd-rom drive
    Install ubuntu
    choose 'manual' partition
    place the root "/" on ext2 partition (check format box)
    and swap
    and...

---

### Post by zeonsoul on 2007-06-12
I stayed up really late, but finally managed to successfully install Ubuntu on my PC! :D
Looks like the step when it asked me about migration only needed some time to load. About 5 minutes or more, so I waited long enough and kept going through the installer.
The partition I used was an ext3 and a Swap. That is what I was supposed to partition like, right?

Thanks a lot to everyone who helped me out in process, I really appreciate your help and I am very glad to now be part of this incredible community! :D

---

