---
title: "Installing Large Partitions"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by playswithdogs on 2007-04-21
I been trying to fix this all day any help would be really appreciated.

I'm building a mythtv box so i bought a 400gb hard drive and when i try to partition anything over around 210 gb i get an error message saying

Can't have the end before the start

any idea why this is

Thanks

---

### Post by Beezleblub on 2007-04-21
Hi, 

Im am facing  the same problem, 
I decided to go for feisty because IVTV is supported right out of the box, wich works great !

but when I try to create a large XFS partition I get the same error.

Gparted shows my hdd drive as a /dev/sda (298.09 GiB)
But if I install Feisty, the Partitioning sw say it's a 320072 MB Drive! ?

any help ?

---

### Post by matsujin on 2007-04-22
Hehe.. I have this same problem.. I was sure that it has something to do with my sata disks, but now that you say this i noticed I can create partitions if they are smaller than 200 GB..

I noticed that someone has already reported a bug [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/107787](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/107787)

Kubuntu doesn't work any better, because it uses the same installer..
But you can create the partitions with qtparted or gnome-partition-tool-whatever-it-name-was with livecd

Alternate install-cd works like a charm..

It would be nice to have a new installation cd where this is fixed..  :)

---

### Post by coxy on 2007-04-22
I'm not sure but that could be something to do with your BIOS. Maybe it doesn't support discs of that capacity? That used to be the case with older motherboards, but I am not 100% sure about more recent ones.

---

### Post by Beezleblub on 2007-04-22
I was experimenting with Edgy before, and there I did not had this problem, so looks like is is related to Feisty, not my Bios. 

For the record, I also use a Sata Drive.

I tried Gparted, you want the big partition to be XFS to run mythTv, and Garted does not support creation of XFS partitions...  :confused:

---

### Post by coxy on 2007-04-23
You could use JFS instead, it deals with large files just as well as XFS and is suitable for a MythTV data partition (I use it on my Myth box). It does not have the problems that Ext3 has when deleting large files.

---

### Post by louieb on 2007-04-23
The GUI is nice, but GParted is in active development and has some bugs. You might try the Linux version of fdisk, theres a bit of a learning curve to using it. Or my favorite **cfdisk**.  Still not a GUI but Its easy to get the hang of it.

---

### Post by najames on 2007-04-23
Thanks for starting this thread, sanity is restored.

I tried to partition

/boot   150MB
/swap 2048MB
/          15GB
/home 300GB (whatever was left of a 320GB drive)

It gave the "can't end before start" error.  It didn't matter what file system was used either, tried several too.  I had to use a 150GB for home and dumped the rest into a large_file partition and all was well.  :-\"

---

### Post by Beezleblub on 2007-04-23
Splitting up into smaller partitions is a work-around indeed. 
But for Myth TV applications, you want one big fat partition for your media files !
so you will still need to use a different tool to create the large partition here. 

It still looks like some Insanity is left here :)

---

### Post by matsujin on 2007-04-24
I suggest people with this problem using alternate install-cd..
Though it would be nice to have a new fixed installer. Can someone verify is this problem only with the final release. Could it be possible to use one of the herd cds? :confused:

---

