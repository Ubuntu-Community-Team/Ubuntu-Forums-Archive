---
title: "Mounting a Drive issues"
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by WoodyMahan on 2006-03-08
I have 3 drives in my system. 2 are 16 GB and one is 70 GB.

Drive 0 runs Win Server 2003 (16GB)
Drive 1 runs Ubuntu Linux 5.10 (16GB)
Drive 2 has 2 partitions. A 30 GB partition that is NTFS formatted to work with Windows and a 40 GB partition that I just formatted through Ubuntu Disk Manager I will call this the "Storage" drive.
The partition formatted fine and I marked it enabled. The Disk Manager Utility can see the "Storage" Drive and even let me create a test folder on that drive.
When I go to Places > Computer, it does not see the Storage Drive, only the File System.
I tried creating a document through OpenOffice and saving it to the "Storage Drive", but I only have access to what I will call the File System Drive because I don't know what terminology to use.

Any suggestions on how I get Ubuntu to let me save files to this second drive? Rebooting the system did not help.

I tried messing with the the Access Path for the Partition in question, but that just really made a mess.  Fortunately when I reboot, it clears up but still cannot access the drive.

Thanks

Wood

---

### Post by animesh on 2006-03-08
you can write on a NTFS drive.....from linux.....but its a very risky business... the file to be overwritten should have same size as the file to be written

---

### Post by WoodyMahan on 2006-03-08
The issue isn't the NTFS partition.  I won't be writing to that partition through Linux.  The issue is the ext2 partition that (I thought) should be no problem at all to write to since that partition was formatted through the Ubuntu interface.

---

### Post by animesh on 2006-03-08
in this file system go to home and there u will see a folder named after user ....there you can save whatever you want ....

---

### Post by WoodyMahan on 2006-03-08
I have 2 hard drives in play here.  the one I installed Ubuntu on, and the one that I formatted to be a storage area.  "Saving whatever I want" is not insuring that the info saved is going onto the Storage Drive.  I want to insure that I keep my main OS drive as clean as possible.

---

### Post by meborc on 2006-03-08
i guess one of you is talking about the yard and the other about the hole in the yard :-k it sounds better in estonian... enywayz

i think what you are looking for is how to mount the partition you created... you can search this forum for mounting or ubuntu wiki... which will lead you to some place like this: [https://wiki.ubuntu.com/AutomaticallyMountPartitions?highlight=%28mounting%29](https://wiki.ubuntu.com/AutomaticallyMountPartitions?highlight=%28mounting%29)

hope it helped!

EDIT: Mounting partitions manually - is the section you need in that link

---

