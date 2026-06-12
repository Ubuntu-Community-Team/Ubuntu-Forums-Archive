---
title: "Removing Everything"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by SexyLexie on 2007-11-28
I'm trying to get rid of all the partitions on my disk and just strip down to one OS. However, in the process, I have found myself unable to delete the partitions I wanted to remove, and also unable to access the Vista, which is the OS I am keeping. When I tired to re-install Vista, I was unable to as apparently the partition was not formatted correctly, despite having Vista already installed on it. I tried to restore to factory image, but an unknown error occurred halfway through, so that didn't work either. Also I have attempted to use GParted, but my computer was unable to burn it to disk, for some reason. 

Long story short, I think I'm going to have to remove everything from the computer and start from fresh. How can I do this in Ubuntu?

---

### Post by mellowd on 2007-11-28
So you want to go into ubuntu to remove ubuntu to install vista?

the easiest way is to boot off your vista cd and delete and recreate all partitions. 


back up everything you want to keep first of course

---

### Post by SexyLexie on 2007-11-28
I tried doing that, but the windows installer was both unable to install to the Vista partition, and unable to delete the Ubuntu partition, stating [Error: 0x80042448]

---

### Post by mellowd on 2007-11-28
But it should see your disk? Tell it to just format the entire disk, ignore the partitions on there

---

### Post by Sef on 2007-11-28
> Also I have attempted to use GParted, but my computer was unable to burn it to disk, for some reason. 

Read [[URL="http://isorecorder.alexfeinman.com/isorecorder.htm"]How to Write ISO Files to a CD]("http://www.petri.co.il/how_to_write_iso_files_to_cd.htm")[/URL], and download ISO Recorder.

---

### Post by SexyLexie on 2007-11-28
I can only see partitions of the disk, not the disk as a whole. All I see is:

Disk 0 partition 2
Disk 0 Unallocated Space
Disk 0 Partition 3
Disk 0 Partition 4
Disk 0 Partition 5 MEDIADIRECT

Refresh   Delete   Format   New
Load Driver    Extend

And the partition sizes etc.
When I try to format partition 4 (containing ubuntu) I get error 0x80004005.

---

### Post by Tomosaur on 2007-11-28
Sounds like the partition table / MFT is corrupt or something like that. Easiest way is probably just to use GParted to format your entire disk. You can use the partitioner on the Ubuntu install CD, if you're finding it difficult to burn GParted to a CD.

---

### Post by indytim on 2007-11-28
If you want to start over to a native condition on your hard drive (nothing there) I'd suggest a "low level" format.  After that's completed, then insert your Vista disc and let it do it's thing as far as partitioning and installs.

Note : This approach will wipe out EVERYTHING on your hard drive!!

IndyTim

---

