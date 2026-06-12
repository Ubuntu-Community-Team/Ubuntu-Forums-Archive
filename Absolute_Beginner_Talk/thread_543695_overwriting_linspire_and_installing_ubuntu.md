---
title: "overwriting linspire and installing ubuntu"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by kuch_rox on 2007-09-05
i have on my computer windows XP and linspire in a dual boot.
I'd like install Ubuntu  over linspire but i don't know how to remove linspire i dont know what to do.
will Ubuntu recognize that i have another linux on my computer or not?!
i have two hard disks and windows and linspire are on the same one so i cant just format the disk with linspire because windows is also on it!!!

please help!!

---

### Post by wolfen69 on 2007-09-05
during setup, just point ubuntu to the linspire partition, and it will overwrite it.

---

### Post by deadgobby on 2007-09-05
[http://screencasts.ubuntu.com/Installing_Ubuntu_with_Windows_Dual-Boot](http://screencasts.ubuntu.com/Installing_Ubuntu_with_Windows_Dual-Boot)
 Yes it can and will whip out the Linspire partition if you wish. 
GObby

---

### Post by Brightbelt on 2007-09-05
I don't know how to do this in Linspire, but it might help you to find out the name of the partition upon which Linspire is installed. (For example, it might be: Sda1 or Sda2 etc) 

What I would do is this: Go ahead and install Ubuntu and when you reach the partition section where it asks you how you would like to do the partitioning, choose 'Manual'.  It will bring up all your present partitions including windows. 

By looking at the sizes listed there in terms of bites, you should be able to confirm which one is your windows partition and which one is Linspire.  Also, your window's file system is listed as NTFS, so that would also help you identify which is which.


Highlight the partition with Linspire on it and choose 'Edit Partition' (the button is below the partition list). Then set the mount point as '/' (that's right: just a slash) and set your file format to be 'Ext3'. Click Ok and on the partition list click the check box by your Linspire partition that says to format the partition.

Then click ok to move forward. Somewhere in the next three steps, based upon what you've entered there, the Ubuntu install will list the partitions that are going to be reformatted and the one upon which Ubuntu will be installed. 

Also, since you've had a dual boot, you probably already have a swap partition (which is necessary to set up a dual boot with Linux.) The swap partition should be listed there as well.  


Just proceed forward and when you restart at the end of the install, you should see Ubuntu and Windows on your boot menu. 

Good Luck, Frank B.

---

