---
title: "Installation Problems (Partitions) first time user"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Bironibbler on 2007-04-23
Hi,

I'm trying to install ubuntu 7 for the first time from the live CD. The live CD runs great (infact i'm writing this in it now) but when i go to install i get stuck on the partition bit. Basically i have a 250gb HD with windows XP on it and it looks like a small 3 gb partition which i think Dell puts on for backup or something.

I have a 100 gigs free and intend to use 50 in total for ubuntu. I run the installer and go through the time zone etc and into the partition bit. It finds the 250 HD and I have a few options 
guided - use entire disk
guided - use largest contin.. free space 
Manual

The top option i'm assuming will format the whole 250 and use that?
I have tried the second and get an error saying 'Failed to partition the selected disk' - This probably happened because the selected disk or free space is too small to be automatically partitioned'
I then try the manual and am presented with [http://img356.imageshack.us/my.php?image=screenshotmm6.png](http://img356.imageshack.us/my.php?image=screenshotmm6.png)

I'm a bit lost from here as to how to resize the windows partition if possible i could use that dell backup partition? Thats only 3 odd gig so I would need some room for vids and docs etc. Any help much appreciated.

Cheers

---

### Post by Cypher on 2007-04-23
All of your HD space has already been partitioned for XP. The free space you have is within the NTFS partition, you would need to re-size your current XP partition to make about 50 GIGs of unpartitioned free space that Linux will use to create it's own partitions.

Choose the "Manual" option and see if there is a Resize option when you're looking at the big 250GB partition. I install Ubuntu on a new HD with no partitions, so I didn't explore the Manual options.

Regards

---

### Post by Bironibbler on 2007-04-23
I tried looking for something like that and couldn't see anything. Would it be an idea to get partition magic or something and partition the drive within XP?

Cheers

---

### Post by Cypher on 2007-04-23
I know there are re-sizing tools within Linux. GParted, PartMagic and others. Not sure if you can run them from the LiveCD, if so you should be able to do all the work from within Linux itself and not have to buy Partition Magic.

Regards

---

### Post by jasonlfunk on 2007-04-23
That would work but there is always a danger of it screwing up your partition tables. The safe bet would be backing up all neccesary data and completely reformat and repartition.

---

### Post by Cypher on 2007-04-23
I just found [GParted - LiveCD](http://gparted.sourceforge.net/livecd.php). You should be able to do all your work within that..

As always, of course, have valid backups before you start messing with all of this.

Regards

---

### Post by Bironibbler on 2007-04-23
Many thanks will give that a go now.

Cheers

---

