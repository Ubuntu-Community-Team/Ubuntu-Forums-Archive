---
title: "Total newbee"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by Triny on 2007-05-16
Hello everybody.
I've just downloaded Ubuntu 7.04 but before I install I was wandering if you could answer a few questions.
I have a Acer TravelMate 662LCi, with a 40 GB disk and 752MB of RAM.
The disk as tow partitions, c: and d: , 27,4 GB and 9,76 GB respectively.
The second one (d:)is completely free and I also have some space in c: witch I can use, currently it’s using around 19 GB.
My questions are:
-How do I increase the size of d: to around 12/13 GB, and what would the best partition sizes to attribute considering I’m thinking of following Psychocats advice and have only three partitions and use FS-Drive to allow Windows to use the /home directory?
If I’m not making any sense please excuse me it’s how new to this I am
Thanking every one in advance
Triny

---

### Post by mahy on 2007-05-16
Not sure if i got it right, but you can always boot Knoppix and use Gparted to do the resizing. Or you can use some windows apps, but those aren't free, in either sense.

I'd put the root partition on the bigger drive and the /home partition on the smaller one.

---

### Post by forestpixie on 2007-05-16
before i installed i found plenty of references to making sure that the drive to be resized had been defragged and defragged again ( i did it again and again to be sure) 

just in case you haven't seen that any where

if it's not necessary i'm sure someone will elaborate

---

### Post by apunc1 on 2007-05-16
I assume you want your partitions to look like this

[IMG]http://www.psychocats.net/ubuntu/images/partitioning5.png[/IMG]

don't forget about that small swap partition

when using the livd cd to install feisty, gparted the disk partitioner will recognize your windows partitions c and d as two partitions in ntfs format. choose to partition manually. you can choose to resize your windows partiton (drive c) and resize and reformat your other nfts partiton (drive d) and make your /home, /, and /swap partitions from the empty space.

so your partitions would look something like this 
[IMG]http://www.psychocats.net/ubuntu/images/feistydual10.png[/IMG]

of course you can size the partitions to fit your needs. this also assumes you're not using windows vista, as only vista can resize its own partitions.

---

### Post by Triny on 2007-05-16
Thanks for the amazingly quick answers.
Yes apunc1, that was exactly what I wanted, and that answers a lot, and no I’m using XP SP2.
I have been reading every thing I can find but they all talk about a situation when the disk as only one partition to start with, and also, my c: partition, apparently as 2 unmovable sections, that is, when I defragment there are 2 green areas!!
Will that be a problem?
:)

---

### Post by dstew on 2007-05-16
The green areas are probably Windows swap files. You can turn off the swap file in Windows, defragement again, then shrink your partition.

---

### Post by Triny on 2007-05-16
Ok thanks.
Have too admit you guys are a hell of a "support and help service", should have changed to Ubuntu/Linux a lot sooner.
Thank you again

---

### Post by Talon2 on 2007-05-16
The Ubuntu installer has a section where you set up your hd.  It will allow you to delete the partitian that is now d: and I pretty sure there is an option to shrink the windows partition.

I don't have a handy link but if you search here on the word "partition" you should find more info.  I suspect you will want to select "Manual" for the partioning mode.  I'm pretty sure it will do everything want but you might want to study up on it before diving in.

---

### Post by Triny on 2007-05-16
You bet!!
Before I do anything drastic, I&#8217;m going too read a lot more.
I depend on this laptop for work (life).:) 
Going to follow the advice and run Ubuntu from the CD for a few weeks and only then take the plunge.
If there's any further advice it would be greately appreciated.

---

