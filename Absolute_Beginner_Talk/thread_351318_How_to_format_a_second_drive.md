---
title: "How to format a second drive??"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by RandyOldgeek on 2007-02-01
I have 6.06 loaded on one of two drives in my PC.  I want to format the second drive to be able to use for data storage.  Is there some way to do this?  I don't seem to be able to find out how in the documentation.  I am probably using the wrong terminology. 

Thanks.

---

### Post by bodhi.zazen on 2007-02-01
Yes, you can do this graphically with gparted. Install gparted with aptitude, synaptic, or apt-get.

You can also do this from the command line.

After you format you will need to edit /etc/fstab and will have to set your permissions.

See these links for further assistance:

[http://www.ubuntuforums.org/showthread.php?&t=282018](http://www.ubuntuforums.org/showthread.php?&t=282018)

Instruction for the CLI is near the bottom of this first link.

[http://www.ubuntuforums.org/showthread.php?&t=283131](http://www.ubuntuforums.org/showthread.php?&t=283131)

This second link will guide you on fstab and permissions ...

HTH

---

### Post by aktiwers on 2007-02-01
gparted is a good program to format harddrives and setup partitions.

Type in Terminal
```
sudo apt-get install gparted
```
and run it by typing
```
sudo gparted
```Good luck :)

EDIT: You beat me bodhi.zazen :)

---

### Post by RandyOldgeek on 2007-02-01
Thanks ......will give it a try.

This is definitely like learning a second language after being a windows guy for so many years....ha.

---

### Post by rocknrolf77 on 2007-02-01
```
gksudo gparted
```

Use gksudo for graphical applications! :)

---

### Post by louieb on 2007-02-01
Open System>Administration>Gnome Partition Editor. This will open up Gparted.
If it is not installed.
Open System>Administration>Synaptic. 
along to top you will see a search button  click it and search for gparted.
When you see the list right click on the entry and mark it for installation.
Then click on the apply button and wait.

The hardest part of using Gparted is selecting the dirve you want to format. 
In the upper right hand corner click on the drop down box and select the new drive.
Then select the unused space, create a new partition and format it. 
I think the p..cats link in my signature has some good info on using it.
:o  LOL: there weren't any replies when I started typing this.

---

### Post by aktiwers on 2007-02-01
> **RandyOldgeek said:**
> Thanks ......will give it a try.

This is definitely like learning a second language after being a windows guy for so many years....ha.

hehe yeah felt the same way when I started using Linux.. it will go over fast.


@rocknrolf77: Why is gksudo better for grafical apps? 
What makes the difference? 
Thanks

---

### Post by RandyOldgeek on 2007-02-01
> **louieb said:**
> Open System>Administration>Gnome Partition Editor. This will open up Gparted.
If it is not installed.
Open System>Administration>Synaptic. 
along to top you will see a search button  click it and search for gparted.
When you see the list right click on the entry and mark it for installation.
Then click on the apply button and wait.

The hardest part of using Gparted is selecting the dirve you want to format. 
In the upper right hand corner click on the drop down box and select the new drive.
Then select the unused space, create a new partition and format it. 
I think the p..cats link in my signature has some good info on using it.
:o  LOL: there weren't any replies when I started typing this.

WOW...thanks for this....I never would have figured this out without your step by step to-do. 

Just one question.....I have one partition on the drive in question and it is formatted FAT32.....do I delete that partition and then create a new one.  Then is the new one a primary or secondary partition...since this is my second drive??

Thanks.

---

### Post by louieb on 2007-02-01
Yes you can delete the existing partition. After you delete it. The simplest thing to do is  create a single primary partition and format it EXT3. 
It doesn't matter if the drive is the first or second drive. When it comes to partitioning each physical hard drive can have up to 4 primary partitions. 

And just to  confuse you there is a way to have more that 4 partitions on a single hard drive.  But I don't want to explain extended and logical partitions. 

Or your could just leave it alone as a fat32 formatted partition. The advantage of that is if the PC dual boots windows both windows and Linux can use the drive. The disadvantage is that fat32 is slower and more buggy than EXT3.

After you get it formated I guess you will want to use it. 
I am using Ubuntu Dapper and it was smart enough to mount my second drive after I rebooted the PC.
If you don't see the second drive when you open the file manager then you need to
open System>Administration>Disks 
Select the drive, then click the partitions tab. It will list the partition(s) on the hard drive and let you mount then. I have never used it so I not sure how. So if you run into problems here maybe some else can help.

---

### Post by RandyOldgeek on 2007-02-01
Thanks again louieb.

---

### Post by rocknrolf77 on 2007-02-01
> @rocknrolf77: Why is gksudo better for grafical apps? 
What makes the difference?

> NEVER use sudo to start graphical programs. You should always use gksudo or kdesu to run such programs, otherwise new login attempts may fail. If this happens and at login an error message reports: "Unable to read ICE authority file", log in using the failsafe terminal and execute the command below substituting user for your username. 

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) :)

---

### Post by ricardisimo on 2007-02-01
OK, so I've read through a good chunk of the links above, so I have the faintest grasp of what's going on. I just purchased a 320 GB hard drive, with some specs below:
```
description: ATA Disk
                   product: Hitachi HDT725032VLAT80
                   vendor: Hitachi...
blah, blah, blah... stuff, things...
size: 298GB
                   capabilities: ata dma lba iordy smart security pm apm
                   configuration: apm=off mode=udma6 smart=on
```
```
Disk /dev/hdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
```

My original intention was simply to expand my space, mostly for music. I never plan on having Windows on this compootor ever again, although conceivably I might one day want to take a peek at Red Hat or some other OS... can't say right now. What would be an ideal partitioning scheme for me under these circumstances. Can I just do one partition now and then later on split it up and rearrange it without losing any data on the drive? [I know, I do always have to leave some space to work with] 

One last question: What's with the 22GB discrepancy between this new disk's size and capacity? 22 Gigs is not a small amount of lost space. Thanks in advance.

---

### Post by bodhi.zazen on 2007-02-02
```
sudo tune2fs -r 0 /dev/hdb1
```
	
sets the number of reserved blocks in the filesystem to 0.

Reserved blocks are available only to specific users (normally root), so that the system can continue to function if the filesystem gets filled up.

---

### Post by Patrick K on 2007-02-02
> One last question: What's with the 22GB discrepancy between this new disk's size and capacity? 22 Gigs is not a small amount of lost space. Thanks in advance.

System overhead and the fact that drive mfgs use 1000 for one K and the OS uses 1024 for one K. Not much of a difference on small drives but it adds up when you have billions of bits involved.

---

### Post by ricardisimo on 2007-02-02
> **Patrick K said:**
> System overhead and the fact that drive mfgs use 1000 for one K and the OS uses 1024 for one K. Not much of a difference on small drives but it adds up when you have billions of bits involved.

Thanks! I never knew that.

---

### Post by ricardisimo on 2007-02-02
> **bodhi.zazen said:**
> ```
sudo tune2fs -r 0 /dev/hdb1
```
	
sets the number of reserved blocks in the filesystem to 0.

Reserved blocks are available only to specific users (normally root), so that the system can continue to function if the filesystem gets filled up.

What the... ? Whoa. You are either 40 steps ahead of me or - what's more likely - this is just another reminder of the very real possibility that I am in WAY over my head with Linux.

I just wanted to know about having one partition or two/three/etc., with or without a /home partition, etc. However, in all fairness to myself and to you, I just re-read a few sections of your partitioning guide, and I can see already that I will need that second ("swap") partition. Is a 10 GB swap too big? I don't understand just what the debate is with this issue. Do you think that for my purposes (music storage, basically) that I need a /home partition?

Also, your fstab guide is very comprehensive and, again, way over my head. Am I editing /etc/fstab and /etc/mtab with <sudo gedit>? If so, can someone hand-feed me what lines to put where? Thanks again.

P.S. - Going back to your comment, when does ```
sudo tune2fs -r 0 /dev/hdb1
``` come into play?

---

### Post by ricardisimo on 2007-02-02
I think I've been able to piece some of this together, but I need a "mount point", and I have no idea what that is or how to make one. Does this look fairly workable so far:

```
[device] = /dev/hdb (or should this be /dev/hdb1?)
[mount point] = ???
[filesystem] = ext3
[options] = defaults
[dump] = 0
[fsck] = 1
```

Also, via gparted I currently have two partitions on my new drive; a 288 GB ext3 and a 10 GB swap. Does this seem OK? Thanks again.

---

### Post by aktiwers on 2007-02-02
10 gb swap? I think thats a lot. I really think you would do fine with 2-4gb. 
I only have 1gb swap, and I never use it all.

---

### Post by bodhi.zazen on 2007-02-02
LOL ricardisimo :lol:

Sorry about the confusion.

First, the swap issue. the general advice is RAM X 2, max 1 Gb. If you have a laptop then RAM = swap. As **aktiwers** indicated with increasing RAM you will use swap less (with less RAM you need more swap to compensate).

Second, mounting. Yes, I think you are getting the general idea.

1. Make a mount point. Generally, /mnt is used for internal HD and /media for removable devices (CD/DVD, USB drives, zip drives, etc) although it is not critical.

2. Mount your partition.

3. Edit fstab. You do not need (and should not) edit /etc/mount ...

4. /dev/hdb = the entire (second) HD
   /dev/hdb1 = first partition on second HD

Example:

```
sudo mkdir /media/music
sudo mount /dev/hdb1 /media/music
```

You still will need to deal with permissions ....
With the partition mounted:
```
sudo chown user_name:users /media/music
sudo chmod 777 /media/music
```
Where user_name = your log in name
users= group users 
And you can use chmod 770 if you are more paranoid.

See here for Linux permissions: [http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

Example fstab:

> /dev/hdb1 /media/music auto defaults 0 0

Post if you have questions. Don't worry, yes it can feel overwhelming at first, but it gets better ...

Last, the command : > sudo tune2fs -r 0 /dev/hdb1

Linux puts aside a part of your partition for system files and admin access in the event the disk gets full. This is necessary on your root partition ( / ), but not on a data partition.

If you run that command your will reclaim much of your missing "22GB discrepancy" in the size of the HD 8)

---

### Post by ricardisimo on 2007-02-02
Now I've gone and done it... I've successfully mounted the new drive, and done all but create a symbolic link (I also have not done the <sudo tune2fs -r 0 /dev/hdb1> bit). Somehow, while i was not looking, a smidgen of comprehension snuck into my brain, and I think I might be able to do this again. However, I also think I'd like to start over, or at least go back and resize - or even eliminate - the swap. I tried just resizing it, but of course the extra 9 Gigs I gained didn't get added onto the first parttion, they're just floating there. How do I erase the whole drive and start over?

---

### Post by bodhi.zazen on 2007-02-02
Adding free space to a partition is tricky.

If you have no data on the HD, sure reformat.

If you prefer to tinker, boot the the live CD and you will need to move then resize the partitions.

Example:

Swap
free_space
Partition to add

Move the partition such that your get:

Swap
Partition to add
free_space

Then resize the partition, adding the free space.

The free space must follow your partition to resize. You can add space at the end of the partition but not the beginning (you must move partitions so that free sapce follows the partition).

HTH

---

### Post by ricardisimo on 2007-02-02
> **bodhi.zazen said:**
> LOL ricardisimo :lol:

Sorry about the confusion.

First, the swap issue. the general advice is RAM X 2, max 1 Gb. If you have a laptop then RAM = swap. As **aktiwers** indicated with increasing RAM you will use swap less (with less RAM you need more swap to compensate).

Second, mounting. Yes, I think you are getting the general idea.

1. Make a mount point. Generally, /mnt is used for internal HD and /media for removable devices (CD/DVD, USB drives, zip drives, etc) although it is not critical.

2. Mount your partition.

3. Edit fstab. You do not need (and should not) edit /etc/mount ...

4. /dev/hdb = the entire (second) HD
   /dev/hdb1 = first partition on second HD

Example:

```
sudo mkdir /media/music
sudo mount /dev/hdb1 /media/music
```

You still will need to deal with permissions ....
With the partition mounted:
```
sudo chown user_name:users /media/music
sudo chmod 777 /media/music
```
Where user_name = your log in name
users= group users 
And you can use chmod 770 if you are more paranoid.

See here for Linux permissions: [http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

Example fstab:



Post if you have questions. Don't worry, yes it can feel overwhelming at first, but it gets better ...

Last, the command : 

Linux puts aside a part of your partition for system files and admin access in the event the disk gets full. This is necessary on your root partition ( / ), but not on a data partition.

If you run that command your will reclaim much of your missing "22GB discrepancy" in the size of the HD 8)

Doesn't seem to be working. Now the drive weighs in at 293 GB. I lost 5 Gigs! :-({|= Oh, well... I'm sure they'll find their way back home. Any idea what to do about this? Thanks.

---

### Post by bodhi.zazen on 2007-02-02
Can you post your partition table or a picture of what you are seeing with gparted?

---

### Post by ricardisimo on 2007-02-02
I have no clue how to view my partition table, but here are the screenshot of both drives in gparted:

---

### Post by bodhi.zazen on 2007-02-02
What is not working ?

FYI you might try the command I gave you to see if you can reclaim some of your HD space.

---

### Post by ricardisimo on 2007-02-02
Here's my current fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=f7733fa7-4cce-4d65-9ec8-c43327e30716 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=c4176c38-a4dd-4eb2-afe4-b883a51472a3 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
# /dev/hdb1 -- adding new 320 GB drive
/dev/hdb1 /mnt/hdb1 ext3 defaults 0 0
```
And here's fdisk output:
```
Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4910    39439543+  83  Linux
/dev/hda2            4911        4998      706860    5  Extended
/dev/hda5            4911        4998      706828+  82  Linux swap / Solaris

Disk /dev/hdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       38913   312568641   83  Linux
```

In another thread it was recommended that I go with the UUID rather than just the descriptive. Would that be better?

---

### Post by ricardisimo on 2007-02-02
> **bodhi.zazen said:**
> What is not working ?

FYI you might try the command I gave you to see if you can reclaim some of your HD space.

I did try that command, and that's what's not working, I went from having 298 GB free space to 293 GB... I lost 5 Gigs. Not the end of the world, and my real concern right now is that after rebooting I lost everything that I had transferred as a test. Any idea what's going on with either problem?

---

### Post by bodhi.zazen on 2007-02-02
I think it is shades of gray between uuid=XXX and /dev/hdb1 ...

As to your data, well you will lose it when you repartition. Did you re-partition ?

As to the size of you HD, no not a clue.

? typo

Unmount the partition and try

> tune2fs -r 0 /dev/hdb1

That is a zero ( 0 ) and not the letter O ...

If that fails, well I would delete the partition and re-format.

---

### Post by ricardisimo on 2007-02-02
The only thing I can think is that maybe I didn't unmount first. Can I do that with gparted, then in a second terminal run the command?

---

### Post by bodhi.zazen on 2007-02-02
Yes, or in a terminal:

```
sudo umount /dev/hdb1
```

---

### Post by ricardisimo on 2007-02-02
```
ricardo@ricardo-desktop:~$ sudo umount /dev/hdb1
Password: hErEiSmYpAsSwOrD
umount: /dev/hdb1: not mounted
ricardo@ricardo-desktop:~$ tune2fs -r 0 /dev/hdb1
tune2fs 1.39 (29-May-2006)
tune2fs: Permission denied while trying to open /dev/hdb1
Couldn't find valid filesystem superblock.
```

---

### Post by bodhi.zazen on 2007-02-02
I am not 100 % on this, but you are having enough problems I would delete your current partition and reformat that *&$? thing :)

---

### Post by ricardisimo on 2007-02-02
That sounds like a plan! ;-) I've been eagerly waiting for anyone to tell me just that. So, gparted, unmount and then delete everything, then create new?

---

### Post by bodhi.zazen on 2007-02-02
> **ricardisimo said:**
> That sounds like a plan! ;-) I've been eagerly waiting for anyone to tell me just that. So, gparted, unmount and then delete everything, then create new?

Yep ...

Or if you prefer the CLI, use cfdisk, delete all partitions, make a new one on the entire HD.

[http://www.linux.org/docs/ldp/howto/IBM7248-HOWTO/cfdisk.html](http://www.linux.org/docs/ldp/howto/IBM7248-HOWTO/cfdisk.html)

Then use the cli to format the partition:

```
mkfs.ext3 /dev/hdb1
```

---

### Post by ricardisimo on 2007-02-02
[COLOR="Red"][SIZE="5"]SUCCESS!![/SIZE][/COLOR]
You know, sometimes it pays to be real stupid and real lucky. The short story is that I was asking for help in two different threads, and this appears to have been the source of both my troubles and the ultimate resolution of the problem. The somewhat longer version is as follows...

In this thread bodhi.zazen gave me these command lines regarding setting permission/ownership (please ignore the foldername fictions):
```
sudo chown user_name:users /media/music
sudo chmod 777 /media/music
```
Meanwhile in the other thread aysiu recommended the following:
```
sudo chown -R ricardisimo:ricardisimo /media/storage
sudo chmod -R 755 /media/storage
```
Neither worked perfectly well in several different attempts. Finally, I sort of combined the two, keeping aysiu's "-R" and bz's "777". It worked.

Now let me be perfectly clear about something - I have absolutely no idea what I'm doing, and so obviously this little maneuver may have had less than nothing to do with fixing the problem. However, I did it and now it's all good. That's my story, and I'm sticking with it.

I want to thank all of you for being so very patient with this numskull. Special thanks to pseudonym, aysiu and bodhi.zazen.

---

### Post by ubuntios on 2007-11-14
> **louieb said:**
> Open System>Administration>Gnome Partition Editor. This will open up Gparted.
If it is not installed.
Open System>Administration>Synaptic. 
along to top you will see a search button  click it and search for gparted.
When you see the list right click on the entry and mark it for installation.
Then click on the apply button and wait.

The hardest part of using Gparted is selecting the dirve you want to format. 
In the upper right hand corner click on the drop down box and select the new drive.
Then select the unused space, create a new partition and format it. 
I think the p..cats link in my signature has some good info on using it.
:o  LOL: there weren't any replies when I started typing this.

Hi,
Thanks for the how to , it works just fine for me :)
The only problem is that only format on reiserfs, when I try the other  formats it gives me error. 
Did you have any problems or is just me ?
Btw I'm trying to format a Toshiba 40g external/media center.

---

### Post by broderboy on 2008-05-01
thanks a lot! this helped me out

---

