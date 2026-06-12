---
title: "How do I install Ubuntu on only part of a hard drive?"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by SquallLeonE on 2007-06-26
I've installed Ubuntu before, but last time I installed it, I installed it on one hard drive completely(a 200gb hard drive).  I recently realized that that wasn't the best thing to do in my situation, being that my hard drive that is running Windows XP is running out of room and I need more space.

So, after wiping my hard drive that has Ubuntu on it completely, I decided to reinstall it on part of the hard drive.  So, I put the Ubuntu CD in and started it up.  I go through the installation and get to step 4 and select the option "Guided - resize SCSI 1 (0,0,0), partition #1 (sda) and use freed space".  For the scroll bar, the only parts of the hard drive that I can use are 93%(95.1GB) - 100%(102.3GB).  To remind you, my hard drive is 200GB.  So, I select 93% and hit "Forward", it tells me that I can't undo the operation, I hit "Continue", then it says "An error occurred while writing the changes to the storage devices.  The resize operation is aborted."  Argh!

I've never installed any operating system on part of a hard drive before, so I'm not sure what I'm doing wrong.  I downloaded partitioning software and created two partitions (150GB and 50GB), but when I tried to install Ubuntu, it wouldn't let me select to install it to the 50GB partition(it wasn't an option).

Any help would be appreciated.

---

### Post by Nekiruhs on 2007-06-26
Go into the Live CD. Press Alt + F2 and type ```
gksudo gparted
```. Resize the partitions there, or make a new one. Install Ubuntu to the new partition by choosing manual and selection the / mount point via the right click menu > Properties.

---

### Post by SquallLeonE on 2007-06-26
Ok, I created two partitions, both with the NTFS type.  I get to the partition selector and select Manual, and from here I don't get what you mean exactly.  Here's what my list looks like:

/dev/hdd
  /dev/hdd1  ntfs  /media/hdd1    []    31453MB  64MB
  /dev/hdd2  ntfs  /media/hdd2    []    168593MB  72MB

I right-click the first line(/dev/hdd) and I can only choose "New Partition Table" and "Undo Changes to Partitions".  I right-click the other two lines and I get "Edit Partition", "Delete Partition", and "Undo Changes to Partition".  I can't seem to get the "Properties" to show up wherever I right-click.  Am I clicking in the wrong spot, perhaps?

Also, when I click "Forward", it says "No root file system is defined.  Please correct this from the partitioning menu."

---

### Post by Nekiruhs on 2007-06-26
You need to make a new ext3 partition for Ubuntu to install to. Open Gparted like I said above, and resize an ntfs partition.

---

