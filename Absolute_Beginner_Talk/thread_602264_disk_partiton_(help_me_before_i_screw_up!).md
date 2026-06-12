---
title: "disk partiton (help me before i screw up!)"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by josh air balloon on 2007-11-04
[IMG]http://img.photobucket.com/albums/v127/304Kills/diskpartitions.jpg[/IMG]

Above is the screenshot I took when I was in Windows Computer Management.  Those first 3 drives with no name by them are 100% free (71mb, 8.76gb, and 447mb).  Im wondering how I can put the extra space on my Linux drive, and add more room to the partition my ubuntu OS is on.  Also, the hard drive (C: ) has about  20 gb unused, and Id also like to put that in the same partition as the other 3.  And I would also like to use that Unallocated space (4.95gb and 3.51 gb)  I would like to do this, because I only have about  1.4 gb of free room in ubuntu right now

ps- I am dual booting, and already have and use ubuntu 7.10

---

### Post by Malta paul on 2007-11-04
Hi, welcome
As you are already using Ubuntu I would myself use 'Gnome Partition Editor'
Go to Applications>Add/Remove then search for Partition Editor, It will install in 'System>Administration. You might also like to check out: [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index) 
If you need more info just post, Have fun :)

---

### Post by josh air balloon on 2007-11-04
On the psychocats link you gave me, do I click on the "plan partitions" link on the left side?

I installed the partition editor, but not really sure where to go from here, Im afraid Ill screw something up.

---

### Post by jpittack on 2007-11-04
Oh boy.  One of those partitions is labeled a recovery partition, probably installed by the manufacturer.  I know that a forum member deleted his recovery partition and his xp would not boot.  This was a dell.

I suggest finding out more information about these partitions.  The best way to find out is in Ubuntu, as their names will be labeled to them, unlike in Windows where they are hidden.

---

### Post by jpittack on 2007-11-04
On a second look, did you create that partition?

---

### Post by josh air balloon on 2007-11-04
The 2 unallocated partitions I created before I installed Ubuntu.  They are just sitting there not being used, along with alot of space in Windows.  Do I just delete those 2 unallocated partitions?  The one labeled recovery is the backup/recovery drive for vista.  I obviously dont want to touch that one, i know that.

---

### Post by jpittack on 2007-11-04
Ok.  Well if those two partitions are blank, Delete them.  They will become one space.  If you want to add them to something else, then need to be at the end of the partition that you would like to grow.  If you will just use them separate, don't bother with moving them.  A gparted live cd can accomplish everything you will need, if you are moving them.  Back up data and you will be fine.  Ask if you have trouble with anything.

---

### Post by josh air balloon on 2007-11-04
[IMG]http://img.photobucket.com/albums/v127/304Kills/Screenshot.png[/IMG]

Heres what I got when I opened the partition editor.  Id like to add the 2 entire "unallocated"  partitions and add them on to /dev/sda5, id also like to take 10 gigs from /sda3 and add it on to /sda5.

---

### Post by josh air balloon on 2007-11-04
bump

---

### Post by josh air balloon on 2007-11-04
Im Only able to resize/move /sda 1.  Anytime I right click on any of the other /sda, resize/move is not an option.  Any reason why?

---

### Post by Malta paul on 2007-11-04
sda3 is formated as NTFS it looks as though it is used by windows for booting.
If you delete it my screw up your duel boot. I would use sda2 which is empty, You can Format to NTFS and use for both windows and Linux or  format to ext3 for linux files. 
Reformatting sda2 will enable you to use your unallocated space.
bye the way sda5 is your Ubuntu root area - Don't Touch
Have fun:)

---

### Post by antoz on 2007-11-04
What I would do is create a separate home partition with those unlalocated partitions, that would be fairly easy by deleting them and if you shrink your windows a bit you should end up with a decent size. The best way to go about it is to use the live cd, you will have to unmount any partition would want to change before it will let you alter anything. While there is no problem with data loss I would make sure to back up any partition before starting.
Hope this helps,A

---

### Post by josh air balloon on 2007-11-04
I tried doing this with the live cd, and its to confusing.

Would it be easier to just delete windows altogether?  I never use windows anymore since I made the switch.  How would I go about doing this?

---

### Post by Malta paul on 2007-11-04
I wouldn't delete windows yet till you are totally at home with Ubuntu and you know how to  do all the things you could do in windows, take a little time to learn Linux as it is a bit different - But great.
Try to format as in my last post, if you screw it up so what, put in the live CD in and install Ubuntu using the default settings.
Have fun thats what Linux is about :)

---

### Post by jpittack on 2007-11-06
You can move the free space to sda5, but you will need to move the windows partition more towards the begining of the drive.  Using a gparted live cd, click on the windows partiton and choose to move it.  Slide the bar up to all the way left.  Repeat with any following partitons until the free space is directly after sda5.  The you can expand sda5 to the free space.

---

### Post by corowakid on 2007-11-06
Before you go any further, may I suggest you look at this site:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

I got into the trouble you're in, and a member here gave me this site to look at. Did it first time, without any problems. You can print those parts that you think you'll need.

Personally I'd go for the Ubuntu Alternate Desktop routs - its got a more usable partitioner. Just remember to use the MANUAL partitioning option - that way you can resize your C: drive, add the free space to those 2 partitions you've got, then follow the instructions for setting Home, Swap and Ubuntu partiitons.

I hope it works as well for you as for me.

---

### Post by nblue on 2007-11-06
I think the reason is because they are mounted. Check to see if you can unmount/swampoff/... them when you right click on the partition.

---

### Post by Bartender on 2007-11-06
jpittack is right - 
Download/burn a copy of Gparted LiveCD.  Don't use the Ubuntu Live CD.  With a GParted LiveCD you circumvent the problems that arise when the partition is mounted.

For some operations, GParted won't respond when you click on the graphic display of the partition on the top of the screen.  When that happens, click on the text describing the partition below the graphic.

---

