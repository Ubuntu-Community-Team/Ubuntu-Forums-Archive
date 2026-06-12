---
title: "New drive -- lost space"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by quickk on 2008-01-14
Hi everyone, 

   I just bought a new 750 GB drive, and upon formatting it with ext3filesystem, I noticed that the free space was 652.3 GB.  Is this normal?  I knew that there was some discrepancy between advertised size and what shows up in the operating system (something to do with 1024 vs 1000 definition of KB), but this seems excessive.  

Should I worry?

Thanks!

---

### Post by steeleyuk on 2008-01-14
Theres definitely something wrong there. You should have around 732GB of formatted space by my calculations.

Is this a drive with Ubuntu on (i.e. your master drive) or is this a second drive (i.e. for data and backups)?

---

### Post by dgray_from_dc on 2008-01-14
No need to worry.  In addition to the discrepancy you mentioned, there is also space lost due to the overhead of the file system.  Ergo the tables used to store the information that tells the OS where on the disk the files are physically located.

Edit: Although, since I've never had a 750GB drive steeleyuk may be right.

---

### Post by articpenguin on 2008-01-14
your using ext3 which reserves 5% of the space for the root user. Another 2% of the space is used for inodes. the 5% of the space reserved is there in case you run out of space.

---

### Post by steeleyuk on 2008-01-14
The file system shouldn't be taking 80GB off him...

I'm on a 250GB drive and it takes about 300MB from me.

@ articpenguin - makes more sense.

---

### Post by articpenguin on 2008-01-14
from tune2fs 

>    -m reserved-blocks-percentage
              Set the percentage of the filesystem which may only be allocated
              by privileged processes.   Reserving some number  of  filesystem
              blocks for use by privileged processes is done to avoid filesys&#8208;
              tem fragmentation, and to allow system  daemons,  such  as  sys&#8208;
              logd(8),  to continue to function correctly after non-privileged
              processes are prevented from writing to  the  filesystem.   Nor&#8208;
              mally, the default percentage of reserved blocks is 5%.

---

### Post by articpenguin on 2008-01-14
other filesystems JFS XFS reiserfs dont have that much overhead but they are a lot less reliable except JFS

---

### Post by quickk on 2008-01-14
Thanks for the quick replies.  Before formatting with the partition editor, the drive showed 698GB of space, after formatting, it was down to the 650GB mark, and I was really wondering what was eating up all that extra space!

---

### Post by kvonb on 2008-01-14
-

---

### Post by steeleyuk on 2008-01-14
Doesn't Reiser do some kind of check at every boot up though? I used it for a while and remember it doing a check of some sort every time I booted.

---

### Post by kvonb on 2008-01-14
-

---

### Post by quickk on 2008-01-14
> Way better than having a total disk check which takes hours on big drives, which for some reason always seems to happen when you are in a hurry to look at a file quick!

Must be that new mind reading app that gets installed silently by default: letsannoyuser-0.0.4.5-1-ubuntu6.deb 

I never realized that this annoying feature was due to ext3.  Having read this, I immediately formatted my drive as reiserfs instead.  I can't imagine how long and annoying it would be to wait for the ext3 filesystem to check the 750GB drive!!  

As an added bonus, I now have about 45GB more space on the drive: the formatted capacity with Reiserfs is 698.5GB.

---

### Post by articpenguin on 2008-01-14
be very careful with reiserfs. It takes 20 seconds to mount, when reiserfs goes down it will stay down.

I use JFS for the very reason because of ext3 hogging up 5GBs of my space and the annoying fsck.

---

### Post by kvonb on 2008-01-14
-

---

