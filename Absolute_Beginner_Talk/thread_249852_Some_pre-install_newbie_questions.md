---
title: "Some pre-install newbie questions"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by neus on 2006-09-03
Ahoy, neus here. I'm about to set up a dual boot of Ubuntu and Windows XP and I sure could use some help. 
So far, I've burned the lastest Ubuntu ISO. 

Alright, now my computer: 
Drive C, 74 GB, NTFS - single partition, Windows XP, mostly programs and very few files
Drive G, 232 GB, NTFS - single partition, mostly files - movies, pictures, songs etc. 

1. I have a 64bit AMD Athlon 3000+ processor. Can I still install the 32 bit version of Ubuntu? (I have the 32 bit version of XP so I'm hoping this is possible on Ubuntu as well.)

On drive C I'm using about 33GB and there are 41GB free. The entire drive is in a single, 74GB NTFS partition. 
I want to resize that partition down to 40GB and leave 30GB for Ubuntu. 
2. How do I do this? (I've heard talk of PowerQuest PartitionMagic 8.0 ... should I use it or something else?)

Also, once Ubuntu is installed and happy, I wish to be able to access the files on drive G - the pictures, movies and such I've stored there. 
3. Is this possible? If so, how do I do it? 

That's all. Please be as detailed as you can - I'm totally new to all of this :)

---

### Post by dbasis on 2006-09-03
to question 2:
only defragment your harddisk in windows, and the rest can be done by installation.

---

### Post by dbasis on 2006-09-03
to question 3: just write the harddisk to be mounted in etc/fstab
"mounting ntfs" would be a good search command.

---

### Post by whizbaby on 2006-09-03
> **neus said:**
> 
I want to resize that partition down to 40GB and leave 30GB for Ubuntu. 
2. How do I do this? (I've heard talk of PowerQuest PartitionMagic 8.0 ... should I use it or something else?)

It's a good idea to use one of these because the present ntfs-write support state is still 'beta' (doesn't have to work, could mess up your data if stars alligned negatively, personal experience).
> 
Also, once Ubuntu is installed and happy, I wish to be able to access the files on drive G - the pictures, movies and such I've stored there. 
3. Is this possible? If so, how do I do it? 

After installing ubuntu the data should already be accessible in the folder /media.
(e.g. /media/hdb2 is the second partition on the second hard drive, /media/hda5 the fifth partition on the first hard drive and so on)
If not it's easy to make it accessible (post again). If you want a drive which is accessible to both, windozer and linux, you should consider making a FAT32 partition (because of ntfs-write beta. linux can write without any problem to FAT32)
good luck!

---

### Post by Blondie on 2006-09-03
To question 1 (since nobody specifically answered it)
The answer is yes you can.

---

### Post by steve.horsley on 2006-09-03
> **neus said:**
> Ahoy, neus here. I'm about to set up a dual boot of Ubuntu and Windows XP and I sure could use some help. 
So far, I've burned the lastest Ubuntu ISO. 

Alright, now my computer: 
Drive C, 74 GB, NTFS - single partition, Windows XP, mostly programs and very few files
Drive G, 232 GB, NTFS - single partition, mostly files - movies, pictures, songs etc. 

1. I have a 64bit AMD Athlon 3000+ processor. Can I still install the 32 bit version of Ubuntu? (I have the 32 bit version of XP so I'm hoping this is possible on Ubuntu as well.)
Yes. I would recommend the 32-bit version to beginners - the 64-bit version still has some issues that a beginner would have trouble with.
> On drive C I'm using about 33GB and there are 41GB free. The entire drive is in a single, 74GB NTFS partition. 
I want to resize that partition down to 40GB and leave 30GB for Ubuntu. 
2. How do I do this? (I've heard talk of PowerQuest PartitionMagic 8.0 ... should I use it or something else?)

Partition magic should be fine. Haven't heard of PQ. The Ubuntu installer can do it too. Do **not** try and create partitions for Ubuntu - leave the space un-partitioned and let the Ubuntu installer make its own partitions as it sees fit in the unused space.
> 
Also, once Ubuntu is installed and happy, I wish to be able to access the files on drive G - the pictures, movies and such I've stored there. 
3. Is this possible? If so, how do I do it? 

Yes. See this guide for details:
[http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)
> 
That's all. Please be as detailed as you can - I'm totally new to all of this :)

Good luck.

---

