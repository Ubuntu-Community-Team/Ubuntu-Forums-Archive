---
title: "Miissing hard drive space"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by ol_smokey on 2007-06-10
Hello All,

I was just in the middle of installing and had got to the partitioning stage when I noticed I have the following problem.

My main hard drive where I have my XP install has soemthing peculiar going on with it.

In Windows the C: drive shows that it is only 30 GB but when I go into device manager it says the the drive has an 80 GB capacity. It appears that I have a ghost partition that Windows isn't seeing. I need this space for my Ubuntu install so if anyone knows how I can get it back without nuking my XP install I would be very grayeful.

Cheers
smokey

---

### Post by KingJohn on 2007-06-10
I'd start, actually, by putting in a Ubuntu liveCD, starting the installer, and seeing what it has to say about your HDD size.  If you really do have 50GB unused, then the Ubuntu installer should see that partition and let you format it and use it for your Ubuntu installation, without affecting your XP partition.

If you don't see that spare partition, it may be that Windows Device Manager is lying to you, and you only have a 30GB drive.

---

### Post by Bakerman on 2007-06-10
It's unlikely that the missing 50GB is a hidden 'ghost partition'. Depending on the PC manufacturer, this type of back-up/system restore partition wouldn't usually exceed 4GB. I would think that the missing drive space is probably unallocated space. If you're still using WinXP, you can go to Control Panel > Administrative Tools > Computer Management. There is a section for Disk Management. Open it up and you'll see how the disk partitions are set up. I would think that the WinXP partition is the first partition, occupying just under half of the drive by the sound of it. If the rest of the drive is unallocated space, it can be partitioned and formatted. Be careful not to nuke any recovery partition if you have one. The WinXP disk management has the necessary tools for partitioning and formatting if you'd rather not use the Ubuntu installation disk to do the job. Also, remember that formatting will take approx 6GB of an 80GB drive. I have a 120GB drive that shows a formatted size of 110.2GB.

---

### Post by KingJohn on 2007-06-10
I wouldn't bother with XP's partitioning tools.  I'd just let the ubuntu installer handle it.

And it's not the formatting that takes up that much of the drive, it's that a "120GB" drive is actually a 120,000,000,000 byte drive - or, since 1 KB = 1024 B and 1 MB = 1024 KB and 1 GB = 1024 MB, 111.78 GB.

(And, really, it's not EXACTLY a one hundred and twenty billion byte drive.  It's a little less than that, which is why your drive is 110.2 and not 111.8)

---

### Post by ol_smokey on 2007-06-10
Thanks Guys,

In XP computer management it is showing that my hard drive is 75.5 GB, so allowing for the 6 gb of formatting that sounds about right,

It appears that C: is a partition on that drive which is only 30GB capacity. Is there anyway to get C: to extend to the whole drive?

I tried to use the windows Deskpart tool in DOS but it would not let me extend the C: partition to take up the rest of the drive, do I have to make the drive 'dynamic' before I can do this?

smokey

---

### Post by ol_smokey on 2007-06-10
Here's a screenshot if that helps.

---

### Post by KingJohn on 2007-06-10
Interesting.  It really does look like you've got an 80GB drive in there, and the PARTITION appears to be the full drive, but the FORMATTED part appears to be just 30.  I don't know how you'd do that, or why you'd want to.

Download the gparted iso, from [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
Burn it to a CD.
Boot from the CD.

This will take you to the Gnu Partition Editor, which should let you see what the partition REALLY is, and also let you shrink the C drive down to a 30GB size, leaving you with a pile of unpartitioned space that you can use for Ubuntu.

After you resize the NTFS partition, your system *will* insist on scanning the disk the next time you boot into Windows, and you should let it do so completely before you do anything else - so my suggestion is, 

1. make the gparted CD, 
2. boot to it, 
3. resize the partition,
4. boot back into Windows, let it scan and load completely
5. boot using the Ubuntu liveCD
6. install Ubuntu into the newly freed blank partition.

---

### Post by ol_smokey on 2007-06-10
Thanks KingJohn,

I'm not sure how it happened either.
Can I use the Partition tool on the Ubuntu 7.04 Live CD I burned earlier?

smokey

---

### Post by KingJohn on 2007-06-10
I don't know what the tool is.  As I recall, the partition tool on the 6.06 LiveCD only let you create and delete partitions, not resize them, so if it's the same one, then it won't help you.  

If it's not the same one, well, why not try it?  See if it's got the option to shrink the partition, and, if it does, use that.  If it doesn't, I swear by gparted for a reason.

---

