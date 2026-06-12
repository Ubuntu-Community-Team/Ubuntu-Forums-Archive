---
title: "Resized Ext3 but can't access additional space."
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by Exile29 on 2006-09-05
I've been using Ubuntu more and more, so I've decided to decrease the size of my NTFS partition. I have a copy of Paragon Partition Manager in XP, so I decreased NTFS by about 44 gig and increased Ext3 by the same ammount. After the process completed, I noticed that the extra space I had allocated to Ext3 was not recognized (it is recognized, but as free space). Here are the details from Paragon for my Ext3 partition:

Partition 1, hard disk 0
Volume label:       
File system:        Linux Ext3
Drive letter:       *:
Serial number:      00000000
Sectors / boot:     2
Sectors / cluster:  8
Size (capacity):    97.6 GB (104.831.193.600 )
Used space:         53.7 GB (54%)
Free space:         44.0 GB (45%)
Physical sectors: 
First: 262694880 (Cyl  16352, Hd    0, Sec    1)  
Last: 467443304 (Cyl  29096, Hd  254, Sec   63)  
HDD info: Cyl  30401, Hd  255, Sec   63

Anyhow... I am not sure what I should do at this point.
After searching the forum, I've seen a variety of solutions for issues *somewhat* similar to mine.
Here's my take on the issue so far: I need to copy the partition to an external HDD, reformat the whole Ext3 partition, then restore my copy.

Is this correct, or am I totally wrong?
Is there a better way to do this? I've done a lot of customization to my Ubuntu install and I'd hate to have to reinstall.

Thanks in advance! :mrgreen:

---

### Post by Jussi Kukkonen on 2006-09-06
Have you tried gparted or cfdisk? 

I doubt you'll get much help with Paragon here, maybe you could try at a Paragon user forum if there is one?

---

### Post by bullgr on 2006-09-06
many partition progs are not support ext3...
i try that too with partition magic and has the same problem... its supports only ext2

you must be sure that the program you use in windows support ext3
otherwise use better qtparted in ubuntu (supports for sure ext3 :mrgreen: )

---

### Post by Exile29 on 2006-09-06
Hmmm... No. I know how to use Paragon just fine, so I'm not looking for Paragon support. Paragon does support Ext3, so that's not an issue.

To be more explicit: I need to know how to get Ubuntu to recognize the new "free space" I have assigned to the Ext3 partition.

---

### Post by steve.horsley on 2006-09-06
> **Exile29 said:**
> Hmmm... No. I know how to use Paragon just fine, so I'm not looking for Paragon support. Paragon does support Ext3, so that's not an issue.

Wrong!

If Ubuntu still sees the old filesystem size when it reboots, then clearly Paragon has not corrected the filesystem size after changing the size of the partition the filesystem is written on. Paragon has only done half the job - the easy half.

I suggest that you grab the gparted ISO from here
[http://prdownloads.sourceforge.net/gparted/gparted-livecd-0.2.5-5.iso](http://prdownloads.sourceforge.net/gparted/gparted-livecd-0.2.5-5.iso)
and burn that to a CD, and boot that to move the partition end very slightly. See if that does the trick. 

Failing that, yes, you will have to copy all the data off, reformat the partition, and copy all the data back, probably using a live CD of some sort. Use cp -a or tar to make the copy.

---

### Post by Exile29 on 2006-09-06
Okay, so if the free space was allocated to the Ext3 partition but the existing partition hasn't been extended, then I am going to use gparted to extend the Ext3 partition an additional 44 gig.

That raises the question: What file system is the current (44 gig) free space formatted with? 

Partition 1, hard disk 0
Volume label:
File system: Linux Ext3
Drive letter: *:
Serial number: 00000000
Sectors / boot: 2
Sectors / cluster: 8
Size (capacity): 97.6 GB (104.831.193.600 )
Used space: 53.7 GB (54%)
Free space: 44.0 GB (45%)
Physical sectors:
First: 262694880 (Cyl 16352, Hd 0, Sec 1)
Last: 467443304 (Cyl 29096, Hd 254, Sec 63)
HDD info: Cyl 30401, Hd 255, Sec 63

---

### Post by Jussi Kukkonen on 2006-09-06
According to Paragon output it is part of your ext-partition, but since linux doesn't see it, it's clearly wrong... I suggest using gparted (or qtparted) to find out.

---

### Post by Exile29 on 2006-09-06
Gparted seems like the way to go. 
I'll give it a try when I get home.

Thanks!

---

### Post by msandersen on 2006-09-06
I'm not familiar with Paragon, I use Partition Magic on Windows. But in either Windows or Linux you should be able to see if the partitions are OK. Except of course Windows doesn't recognise ext3, but at least will tell you if the partition is OK. Paragon would show some sort of partition map too.
If you already use Linux, then either use qtparted or gparted. Although qtparted is a KDE tool, it's more complete.
They are both Partition Magic clones, and they'll show you if the partitions are Ok and any unallocated space.
As for the data, if you can log in and all the data is there, and the partition map looks OK with no unallocated space, don't worry.

If you want to see your Linux partitions in Windows, the [Ext2/3 IFS Driver]("http://www.fs-driver.org/") is the way to go (Note: Ext3 is Ext2 with journalling, there is no practical difference).

---

### Post by steve.horsley on 2006-09-06
Hoping not to offend you with a silly analogy, but it occurs to me that is's a bit like extending a car park. Extending the partition is like extending the area of tarmac. But that doesn't change the way the car park is marked out. A partition contains a filesystem, carefully marked out with numbered data blocks. So just as you have to paint out more spaces on the new tarmac with white lines, you have to adjust the filesystem to tell it there are more slots to store files in. The filesystem is very much the equivalent of the white line markings.

---

### Post by Exile29 on 2006-09-06
I think I see what has gone wrong here.
I used Paragon (much like Partition Manager) to resize the partition, but resizing the partition doesn't automatically resize the file system (like NTFS does when you resize). So I've got a 97 gig partition of which only 53 gig is recognized by the file system (Ext3).
I need to use resize2fs (or Gparted which uses resize2fs) to resize the file system. 
Ahhh... Nothing like learning a new OS! :rolleyes:

---

### Post by Exile29 on 2006-09-06
> **steve.horsley said:**
> Hoping not to offend you with a silly analogy, but it occurs to me that is's a bit like extending a car park. Extending the partition is like extending the area of tarmac. But that doesn't change the way the car park is marked out. A partition contains a filesystem, carefully marked out with numbered data blocks. So just as you have to paint out more spaces on the new tarmac with white lines, you have to adjust the filesystem to tell it there are more slots to store files in. The filesystem is very much the equivalent of the white line markings.

Your anology and my epiphany happend simultaneously. :mrgreen: 
Good one though. Thanks!

---

### Post by msandersen on 2006-09-06
> **steve.horsley said:**
> Hoping not to offend you with a silly analogy, but it occurs to me that is's a bit like extending a car park. Extending the partition is like extending the area of tarmac. But that doesn't change the way the car park is marked out. A partition contains a filesystem, carefully marked out with numbered data blocks. So just as you have to paint out more spaces on the new tarmac with white lines, you have to adjust the filesystem to tell it there are more slots to store files in. The filesystem is very much the equivalent of the white line markings.
He's familiar with Paragon Partition Manager and said he'd extended the Ext3 partition to fill the gap. Or the white line markings if you will.

---

### Post by Exile29 on 2006-09-06
Well, I got it to work with Gparted. 
I didn't see any options to grow the file system, so I shrank it back to its original size then expanded it again. 
Since I was using Gparted, it automatically ran resize2fs and grew the file system out to include the whole partition. :mrgreen: 

Thanks everybody for pointing me in the right direction!

---

### Post by FastZ on 2006-11-07
Thanks guys, I had the same problem and fixed it using gParted.  Resized my ext3 partition in windows using Partition Manager and then had to use gParted to resize it again just about 5 "clicks" smaller so that gParted would extend the filesystem to fill the entire partition size.  Worked like a charm!  Thanks again.

---

### Post by haydent on 2008-04-01
heres a little story of how i saved my  500gb hdd from being corrupted by windows ....

i keep it in external usb hdd bay, which has its own cheap issues but hasnt let me down yet...

basically i started out formateing the whole thing with ntfs when i forst got it and using it like that, but i ike linux and before long wished id formatted it ext. but by this tage it was too full for me to do anything about...

but then when it wouldnt mount in windows more and more and and i was getting ever more dispaired with windows scandisk i figured id better do something before it was any worse.

so spared up about 60gbs on other old drives and got the 500 down so only half was being used, after having plugged it into an ide cable and tower to read it as opposed to the usb case....

then i ran o & o defrag from in windows to defrag and move everything (~250gb) to teh first half of the drive, then i loaded up partition magic 8 to split and format the driev into 2 halfs. i tried boot-it ng and gparted but they both wouldnt touch it complaing to run chkdsk from windows as windows had marked it bad, but after running chkdsk /r several times, it still wouldnt unlock it. (partition magic did it anyway.)

then i copied everything over, formatted the first half to ext3, ran fsck.ext3 checking for bad blocks, (to find none) then copied everything back from the 2nd to the 1st partition. deleted the 2nd, and resized the 1st to take up all the hdd with gparted.


**this is where something went awol... **


all of a sudden i had one big ext3 partition that was saying it was full at ~480gbs when it should have been half full ? yet would only say it had ~250 gbs of data on it by certain apps)

after reading around the net i heard mention of resize2fs. and that perhaps what had happened was gparted had not resized the size of the filesystem...

so after running resize2fs /dev/hdb1 i had a full ok ext3 500gb drive again, with no bad sectors or data, that mounts in windows via ext2fsd.

:)

---

