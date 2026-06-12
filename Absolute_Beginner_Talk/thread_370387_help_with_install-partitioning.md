---
title: "help with install-partitioning"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by zbeau on 2007-02-25
I'm a Linux newbie and I was installing ubuntu on my Windows PC and I got to the prepare disk space screen and selected the 1st option(Resize IDE1 master, partition #2(hda2) and use free space) and then hit forward and waited.  The cursor changed to show it was busy, but then it stayed like that for at least a 1/2 hour before I canceled the installation.  I don't know much about manually partitioning a drive so I don't feel comfortable doing that and I also want to keep Windows so I can't reformat the hard drive.  Any help would be greatly appreciated.
Thanks,
Zack

---

### Post by george29 on 2007-02-25
First thing to do is backup any data you really don't want to lose onto DVD's or CD's or an external hard drive if you have one.
 
secondly you need to defragment your windows partition - do this a couple of times. 

then boot into the ubuntu liveCD, which has a program called gparted. use this to shrink the windows partition to create space for the ubuntu install. use the liveCD installer and follow the instructions.. make sure you know which partitions are which.

windows is very likely to be hda1, but gparted should be able to tell you the information so you know where to install to.


lots of lovely information at the following website for you to read.

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

