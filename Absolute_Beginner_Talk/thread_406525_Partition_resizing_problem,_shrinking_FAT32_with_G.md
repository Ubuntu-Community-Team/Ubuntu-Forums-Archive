---
title: "Partition resizing problem, shrinking FAT32 with GParted"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by Drithyin on 2007-04-11
I am installing Ubuntu as a second OS on a machine already running Windows XP. I have 2 hard disks. Currently, the master harddrive (120gb) is one large FAT32 partition with XP on it. (FAT32 instead of NTFS because it was an upgrade instal from Win98 and I was too lazy at the time to fresh format the whole thing)
My second harddrive is a ful 240gb partition of Ext3, which will eventually be my /home partition. I also have a program that lets Windows XP read and write to Ext2/3 file systems, so it will also be shared storage.

My problem comes in when I try to shrink my FAT32 partition. I want to cut it to half (approx 55-60% free space) and make the other half my Ubuntu partition, with the linux swap on the end.

So, I run GParted (from the Ubuntu Live CD) and tell it to resize the primary FAT32 partition to 60gbs, which leaves around 8gbs or so of free space left in the FAT32 partition, and the rest of the drive unallocated.

It managed to make it through the first test, then when it attempts to resize, I am told that the, "file system is reporting free space as 0 clusters not 19XXXXXXX clusters" (forgot exact number, not posting from main box)

I have run a scandisk and am currently running a defrag that will take approx 15 years. Any idea what would be causing that sort of error? I have a funny feeling it will do the same thing after the defrag.

Thanks in advance

---

### Post by devnulljp on 2007-04-11
If defrag is taking forever, you can copy your data off onto something else andthen back onto the fat partition -- that will do the same thing as defrag and shoudln't take too long. (The lazy way always has  payback time)

---

### Post by Drithyin on 2007-04-11
That would be tempting, but I am hesitant to pick up and move my Windows installation and all the stuff that's sitting with it.  Windows gets tempermental is you start moving things, and I would have to chop a chunk out of my Ext3 on drive 2 to move it somewhere. 
I have, honestly, never heard of this functioning like a defrag. However, I have never researched it either.

Regardless, I am wondering if a defrag will even have anything to do with the error I am getting.

Consider this a bump for the morning crowd as well.

---

### Post by Drithyin on 2007-04-11
Another quick thought:

I am curious if it is because my pagefile or some other windows system files are deep into free space. My green bars of unmoveable files on Disk Defragmenter are about 3/4 into the big bar that represents my drive. I have no idea if that has any real meaning, but it makes me wonder.

Please don't tell me I need to run "Perfect Disk" again after this...

---

### Post by Drithyin on 2007-04-11
Disk Defrag and scandisk did nothing to remedy my woes.

I'm still getting *File system is reporting the free space as 0 clusters, not 1980483 clusters.*

Desperate for help.

---

### Post by Drithyin on 2007-04-11
Update: I tried copying my entire FAT32 partition to my secondary drive and sizing it there, on the off chance that there was an issue with the hardware. Negative. The copy was also giving the same error. 

I'm at a loss on this.

---

### Post by Patrick K on 2007-04-12
If you have a place to backup everything on the partition/drive in question, probably the best bet is to backup and delete the partition. Then create the partitions you want and restore the data. That's the approach I'd use.

---

### Post by Drithyin on 2007-04-12
I broke down and did, more or less, that.
I tried moving the entire partition onto the other drive and resizing it to see if it was a hardware problem with my drive. No such luck, same error. So, I saved all of my irreplacables and such onto my secondary drive (the full Ext3, future /home partition) and deleted the entire FAT32. Then I just made an NTFS for XP and an Ext3 for Ubuntu, with a 1.7GB swap. I'm going to instal both OS's later. That tired me out last night and I called it a day. 

/thread

---

