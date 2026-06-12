---
title: "Dual-Boot Partitioning Woes"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by TheMemphisExperience on 2008-01-17
I've been running Windows Vista on an ACER Aspire 5920 and decided to dual-boot with Linux so I could get a feel for the OS. I downloaded Ubuntu, defraged my drives(single Toshiba 200GB[ 4 partitions]), and got to the disk partioner.

Then, I ran into some problems. [http://i235.photobucket.com/albums/ee55/TheMemphisExperience/Screenshot.png?t=1200555778]("http://i235.photobucket.com/albums/ee55/TheMemphisExperience/Screenshot.png?t=1200555778")[http://i235.photobucket.com/albums/ee55/TheMemphisExperience/Screenshot.png?t=1200555778](http://i235.photobucket.com/albums/ee55/TheMemphisExperience/Screenshot.png?t=1200555778)

I reduced the size of the third item( my D drive)by 20GB, but the screen then displayed 20000MB of unusable under the third slot. I right clicked and told it to remove changes.

Some tinkering and internet searches later, and I have to go to bed because I have work in 5 hours. 

If anyone can point me in the right direction so I may finish this tomorrow, it'd be grand.

Then I may turn to attempting to configure these temporarily useless buttons the ACER is replete with.

---

### Post by camnor on 2008-01-17
By taking a look at your screenshot there, the problem is is that there is already 4 partitions and, you said you were wanting to make a new partition, it won't allow you because you have already reached the maximum number of partitions on your hard disc.  What my suggestion would be is to create an extended partion and house one of your four partitions in there as well as your two linux partitions.  That should solve your problem.  As well, I         feel you pain about the buttons on your acer, I myself have an hp laptop with a bunch of windows specific buttons that I haven't had time to tinker with yet.
Hope this helps :KS

---

### Post by chewearn on 2008-01-17
Instead of trying to repartition from within the installer, I suggest to prepare the partitions before hand.

Close the installer; then run GParted:
System > Administration > Partition Editor.

Resize your partition, free up some space.  Let the freed space **unallocated**.

Note: GParted in the LiveCD will likely crash after each operation is completed; just ignore that, and relaunch it.

Then run the installer again; you should now be able to choose "Largest continuous empty space".

---

### Post by plucky on 2008-01-17
check out this [website](http://www.psychocats.net/ubuntu/partitioning) for further information on partitioning.

Good luck and have fun.

p.s Use Vista's disk management to reduce the size of your partitions.

---

### Post by TheMemphisExperience on 2008-01-18
> **camnor said:**
> By taking a look at your screenshot there, the problem is is that there is already 4 partitions and, you said you were wanting to make a new partition, it won't allow you because you have already reached the maximum number of partitions on your hard disc.  What my suggestion would be is to create an extended partion and house one of your four partitions in there as well as your two linux partitions.  That should solve your problem.  As well, I         feel you pain about the buttons on your acer, I myself have an hp laptop with a bunch of windows specific buttons that I haven't had time to tinker with yet.
Hope this helps :KS

I remembered the limit on primary partitions as I drove to work and cursed Acer for giving me those two smaller recovery/??thing?? partitions.

I eventually bit the bullet and killed my D drive to give Ubuntu 20GBs to play with. Thanks for your help.

So the experiment begins.

---

