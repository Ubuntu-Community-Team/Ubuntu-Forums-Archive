---
title: "I guess its a partition problem.."
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by l0l on 2006-06-21
So Ubuntu has been really useful up to now. I mainly use it to watch movies, because of some driver problem in Windows, but that is not the case. Here follows:

I wanted to create a new partition on my hard drive, so I tried to do that through Windoze; however, I failed. Then I decided that Ubuntu might do just what I need, so I split my partition F: to two partitions. The new partition would be FAT32 10GB, and I would then convert it to a NTFS partition in Windoze, since Ubuntu does not allow me to create an NTFS partition. It went well, but when I logged into Windoze, this partition appeared as an ext2 (problem #1) which was weird, because I remember creating this partition specifically as a FAT partition. I still figured that I would get a NTFS if I deleted this new partition and created a new one from the blank space thru Windoze, and that went just fine.
Now I have the correct partition, but Ubuntu is acting all weird. After I log into my username, everything but the clock appears on the desktop, the hard drive is active (because the little red light is on) and everything is jerky. After waiting for 10 minutes not able to do anything (because the processor is busy doing... something , i guess) a message appears saying something about not able to run the "Clock" application. 

My grand question(s): 
1. Is it possible that meddling around with the new partition might have corrupted my Ubuntu?
2. How can I fix the clock problem, if the screen is jerky (almost frozen)?

I would appreciate any kind of help.. :D

---

### Post by rowanparker on 2006-06-21
1. The only way partitioning can conflict with Ubuntu is if you mess with any filesystems Ubuntu needs.
2. Sorry, don't know.

Rowan.

---

### Post by l0l on 2006-06-21
I understand that it doesnt make much sense, but I also fail to believe that this is just a coincidence.

---

### Post by rowanparker on 2006-06-21
You think you could do a fresh install?

I know it's not the best way, unless somebody else has any ideas?

Rowan.

---

### Post by Jasper Houtman on 2006-06-21
Might be a problem with the swap partition, did you move or rezise it?

You also shouldn't rezise or try to change the linux partitions with windows software, if you did that then that could also have caused your problem.

Don't know a quick fix for this, clean reinstall worked for me.

Note: ext2 is not a file system, you have to create a fat partition inside ext2.
Sounds like you when't repartitioning on the same HD as Ubuntu, which is most likely the cause of all your problems.

---

### Post by l0l on 2006-06-21
[QUOTE=Jasper Houtman]Might be a problem with the swap partition, did you move or rezise it?

You also shouldn't rezise or try to change the linux partitions with windows software, if you did that then that could also have caused your problem.

Don't know a quick fix for this, clean reinstall worked for me.[/QUOTE]

I didn't touch the Linux partitions, however, Norton PartitionMagic stated that the newly created FAT partition was actually a ext2 partition, so maybe it messed around with the other ext_ partitions as well?

---

### Post by Jasper Houtman on 2006-06-21
OK, think I have it figured out. Partition magic was supposed to go through several steps while creating the fat partition.

For example:
step 1: resize partitions, creating free space
step 2: create Ext2
step 3: create FAT partition

For some reason this 3rd step was never implemented. Proces could have been interupted or your system may have crashed, etc

By not proparly completing step 3 Partition magic may have corrupted several partitions.

Try removing the ext2. Recreating the ext2 and fat in linux using QTparted (or equivalent). If that's not possible with partition magic, but preferably with a tool like fdisk.

Check if ubuntu works again.
If it works then you can convert the partition to NTFS in windows safely.

If not the more drastic measures are required.
Boot your ubuntu install disk. 
Use the partition tool to remove all partitions except windows.
Create all the partitions you want with the partition tool.
Reinstall Ubuntu.
Then convert the fat partition to ntfs in windows.

Note: my version of partition magic had a lot of problems with my linux partitions, and didn't function proparly would be much safer to stick to fdisk (or a similar tool).

---

