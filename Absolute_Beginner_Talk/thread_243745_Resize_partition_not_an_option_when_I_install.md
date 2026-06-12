---
title: "Resize partition not an option when I install"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by reeceaxl on 2006-08-25
I have seen similar problems listed in this forum, but none of the situations apply to me (IE an old computer, low disk space). 
I have lots of space on my computer- it's a new Dell Inspiron 6400. 
I have been following the directions here: [http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)
to create a partition with windows. When I get to the screen that says: prepare disk space, the first option "Resize IDE1..." is not available. 
Anyone have any suggestions?
thanks.

---

### Post by cptjaben on 2006-08-25
are you trying to resize a windows partition so you can use the new space for ubuntu? if so, i believe you can run ubuntu live cd and use gnome partition editor. Hope this helps.

---

### Post by reeceaxl on 2006-08-25
Thanks for responding. I am trying to partition so I can add ubuntu. 
I am trying to use the live CD as per the psychocat instructions, but at the step I mentioned, the option that I would like to use is missing- the one that lets you resize.

---

### Post by az on 2006-08-25
> **reeceaxl said:**
> Thanks for responding. I am trying to partition so I can add ubuntu. 
I am trying to use the live CD as per the psychocat instructions, but at the step I mentioned, the option that I would like to use is missing- the one that lets you resize.


The partitioner is very cautious.  It will chicken out and not give you the option of resizing if it thinks it can fail for any reason.

You probably have to defragment or have a problem with your partition table which is preventing the ubuntu installer from safely being able to partition your drives.

Can you post what your current partitions are like?

---

### Post by Jerome36 on 2006-08-25
Did you defrag your hard drive in Windows?  If not I'd do that first.  When I did a dual boot I defragged the drive, did the install via the Ubuntu Live CD, and I selected the option to have Ubuntu find the largest free space on the drive.  A slider then appeared, where I could raise and lower the amount of space that'd be used for Linux.

---

### Post by reeceaxl on 2006-08-25
Thanks, I will try to defrag. I haven't done that.
I haven't partitioned it at all, so it is just as it comes from Dell. 
Cheers.

---

### Post by reeceaxl on 2006-08-26
Well, I defragged and I tried using a different disc- one of the Ubuntu free discs instead of a burned disc image. 
Ubuntu works fine when I start it up. The disc check at the beginning says that nothing is wrong. I can use the disc live, and begin the installation process but not the partitioning. 
Instead of the resize choice, it asks if I would like to use the largest continuous space and if I select this option, it says there was an error and asks if I would like to wipe out my entire drive.
Does anyone else know something I could try?

---

### Post by Jerome36 on 2006-08-26
> **reeceaxl said:**
> I can use the disc live, and begin the installation process but not the partitioning. 
Instead of the resize choice, it asks if I would like to use the largest continuous space and if I select this option, it says there was an error and asks if I would like to wipe out my entire drive.

Does anyone else know something I could try?

Hmmmm, that was the option I used (though I said "largest free space on the drive") before.  Was there a specific error that it gave you?

---

### Post by confused57 on 2006-08-26
> **reeceaxl said:**
> Well, I defragged and I tried using a different disc- one of the Ubuntu free discs instead of a burned disc image. 
Ubuntu works fine when I start it up. The disc check at the beginning says that nothing is wrong. I can use the disc live, and begin the installation process but not the partitioning. 
Instead of the resize choice, it asks if I would like to use the largest continuous space and if I select this option, it says there was an error and asks if I would like to wipe out my entire drive.
Does anyone else know something I could try?

You can try the latest version of the gparted live cd(approx 30 mb) to resize your Windows partition:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

I believe the newer versions of gparted have better support for resizing NTFS partitions.

---

### Post by reeceaxl on 2006-08-30
Thanks for all the help. I ended up manually partitioning and that worked, thankfully.

---

