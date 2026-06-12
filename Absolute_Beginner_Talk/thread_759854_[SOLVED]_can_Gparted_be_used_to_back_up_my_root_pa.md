---
title: "[SOLVED] can Gparted be used to back up my root partition?"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by boyofford on 2008-04-19
Hi, been playing with gutsy 32bit for a few months and have got stuck a few times installing things only to leave me with a slow gutsy installation, no problems, just reinstall, but a bit of a pain re-installing everything and updates.

Just gone through a reinstall with Ubuntu studio64bit and mostly setup as i want it.

I have never used Gparted, but have read that it can copy partitions.
If thats the case(?) can it be used to copy the root partition to somewhere else on hardrive and to put copy back into original partition if i mess things up? 
My home folder is on separate partition so would only be 25gig partition(mostly empty) that i would be backing up.

---

### Post by drs305 on 2008-04-19
If you are only interested in gparted, disregard the following. 

I do this regularly with both my root and home partitions, but the program is PARTIMAGE. I boot from a rescue CD or the live cd and run partimage from there. Just note which partitions you want to make images of beforehand.
It will use only a slightly larger amount of disk space than the actual data on the partition; the file will not be as large as the entire partition unless it is full. This would be an advantage over gparted, whose copy would have to be an identical partitiion to the original.

Here is how I do it:
Boot with rescue or LiveCD to a prompt.
Make a temp mount point  [mkdir /mnt/temp ]
Mount an existing partition on which you want the backup to the mount point you just made  [ mount /dev/sdaX /mnt/temp ]   (it could also be /dev/hdaX depending on your system)
start partimage  [partimage]
Select the parition you want to backup
Name the new filename: /mnt/temp/backupfilename

There are other and perhaps easier methods but I've used this for a long time without problems.
If you already knew of this method and were looking for someone with knowledge of gparted, hopefully they will respond.

---

### Post by bodhi.zazen on 2008-04-19
To answer the question, yes you can do this with gparted.

You will need to manually configure grub and fstab.

Here is how :

[http://ubuntuforums.org/showthread.php?t=316237](http://ubuntuforums.org/showthread.php?t=316237)

---

### Post by boyofford on 2008-04-21
Think I'll give both options a go then! cheers fellas

---

