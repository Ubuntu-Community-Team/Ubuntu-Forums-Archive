---
title: "Manual partitioning - only one primary possible? (Dual boot)"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by bettyhills on 2007-05-28
Attempting to install U-FF 7.04 dual boot onto existing WinXP single SCSI drive.  It already has three primary partitions on it, one for WinXP, and two mysterious pieces installed by Dell.  

In Partition Magic, the WinXP partition was reduced to leave 70GB unallocated space on the drive.

I understand I can install only one more primary partition (4 max), but many logical.  I am choosing to install "Manual" to insure that the U-FF installation goes onto the unallocated section of the drive.  Ubuntu is asking me to create a new partition.  Are the answers?...

Type:  Primary?
New partition size:  70GB?
Use as:  ext3?
Mount point:  ????

If I do this, will I be able to create logical /, /boot, /swap, and /home partitions in that linux primary partition?

Any help will be appreciated.

---

### Post by vigleik on 2007-05-28
Run qtparted (or is it gparted?) from the live CD before installing. Create an *extended* partition, and then create partitions inside the extended partition for /, /home and swap.

---

### Post by flip_flop on 2007-05-28
I recomend you back up defrag your hard dives beforehand dell and acer leave a section on your hard drive which is not visible by most partition managers this hidden section contains about 3 to 5 gig of OEM files for windows.  Backing this up at least is a good idea.  Not sure how to do it on a dell.

---

### Post by Bartender on 2007-05-28
Is it a Media Center PC or straight XP?  
One of the "mystery" partitions will be a recovery partition.  If you can copy that to a DVD (maybe do it twice just for safety) then you should be able to remove it entirely, freeing up space for another primary.

With a Dell Media Center PC, the other partition has something to do with the Media Center functions.  You can dump that partition also, but then you'll lose some of the Media functions.

You could just leave all the Windows stuff alone.  I would be surprised if Ubuntu lets you build a 4th primary.  Every time I've partitioned using a LiveCD or a partitioner like GParted LiveCD, the partitioner won't build a fourth primary, instead steering you towards building an extended partition.

There's no reason not to build an extended partition, then build your logical partitions (/, swap, home, whatever else) inside.

---

### Post by bettyhills on 2007-05-28
Thanks all for the guidance.

---

### Post by Happy_Man on 2007-05-28
Yeah, I'd go with creating an extended, and then dumping /boot, /home, swap, etc. in there.

---

### Post by steve.horsley on 2007-05-28
Agreed. Go for an extended partition.

Just to explain, an extended partition is a special type of primary partition (so it must be one of the four primary partitions) and it acts as a container for all the logical partitions. The reason for this strange arrangement is that when they designed the layout for hard disks, they didn't think that more than 4 partitions would ever be wanted.

Incidentally, if you tell the installer to use the unallocated disk space, it will create an extended partition and create a / and a swap partition in there.

---

