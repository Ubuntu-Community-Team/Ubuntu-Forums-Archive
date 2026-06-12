---
title: "Please help - can't create partition"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by dmkuster on 2008-01-22
Hi all,

I have a 3ware raid controller in my box.  I had a 4 disk, raid5 array created when I installed
Ubuntu.  It is a 900 GB array.  When I installed linux this array was recognized, and I ran
GParted to created the partition and file system.

Now I installed 4 more disks (500 GB Seagates) and created a second array, so this array
is 1.5 TB.  Ubuntu sees this array as /dev/sdc, but when I run GParted it says the size of
sdc is -698707507712 B (yes, minus) and if I click on 'create new partion' it won't let me 
select a size of file system.

This is on a 3ware 7810 controller.  Can someone please help?

Thanks!

---

### Post by ItalOz on 2008-01-22
don't know if this might help but you can try boot with a GPARTED-LiveCD [(HERE)]("http://gparted-livecd.tuxfamily.org/") disk and  resize the HD with that.
It wrked for me when Gparted inside linux wouldn't let me resize the partition of my HD because it was locked

Hope it helps

---

### Post by dmkuster on 2008-01-22
> **ItalOz said:**
> don't know if this might help but you can try boot with a GPARTED-LiveCD [(HERE)]("http://gparted-livecd.tuxfamily.org/") disk and  resize the HD with that.
It wrked for me when Gparted inside linux wouldn't let me resize the partition of my HD because it was locked

Hope it helps

Thanks, I will try that.

I'm also wondering if there is a problem with the size of my RAID array (1.5 TB).

My 3ware 7810 controller allowed me to create this array and it says the array is healthy, so I don't think
the card is at fault.

Does linux have a limitation in the size of the hard disk it can "see"?

---

### Post by bakaotaku85 on 2008-01-22
By default Ubuntu uses the ext3 partition format. According to Wikipedia, even with a block size of 4kb, you should be able to get a partition of 2 TiB, and Linux should be able to see all of it. My guess is that your RAID controller may have issues with GPartEd, and is most likely not Ubuntu's fault.

[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

You may want to try the GPartEd forums and see if there is a device issue.

---

### Post by dmkuster on 2008-01-23
OK, I tried a few things and finally got the RAID5 array partitioned and formatted.

First off, the GParted liveCD would not work.  I couldn't even get it to boot up to the GUI.

Next, I tried reconfiguring the RAID 5 array using only 3 of my 500 GB drives instead of 4.  This resulted in an array that was just under 1 TB in size.

When I ran GParted it was then able to create and format the partition.

Of course, this wasn't what I wanted since I have 4, 500 GB disks.

Then I downloaded and installed a different partition table editor, 'qtparted'.  This tool _was_ able to see the 1.5 TB disk array.  

I partitioned it and formatted it and now everything is working.

I don't know if GParted simply can't deal with drives larger than 1 TB, or if it is an issuel with my 3ware 7810 RAID controller.  But in any case qtparted is a workaround.

---

### Post by Mulchman on 2008-02-06
> **dmkuster said:**
> Then I downloaded and installed a different partition table editor, 'qtparted'.  This tool _was_ able to see the 1.5 TB disk array.  

I partitioned it and formatted it and now everything is working.

Thanks for this post!

I too could not get gtparted to recognize a 1.2 TB RAID 5 array (LSI Megaraid SATA 150-06 controller) and had to go the qtparted route.

---

