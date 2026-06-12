---
title: "Can I expand an existing partition by adding another HDD"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by mmathur on 2007-05-21
I have a MythTV setup and have a 500GB hard drive that I partitioned (20GB for ubuntu OS - Feisty Fawn, 2 GB swap and the remaining for my media) and I am running low on disk space and have bought another 500GB hard drive that I want to place in this machine and I would like to expand the partition that I created for my media onto this drive.

Can I convert the partition(s) to a logical partition without losing all of my data?

---

### Post by Terl on 2007-05-21
You can format the drive and mount it as you would any other drive.  You wouldn't be extending an existing partition.

---

### Post by vtel57 on 2007-05-21
You can't "expand" a partition on a certain drive to a new drive. However, you can copy the entire partition to the new drive, then once you're sure your data is safe on the new drive, you can wipe the old partition and use it for other stuff. 

You'll need advanced knowledge of Linux to do this manually, or you can use a partitioning application, like Partition Magic or Norton Ghost. Note: data should not be lost. However, poop happens, so be careful.

---

### Post by superm1 on 2007-05-22
> **mmathur said:**
> I have a MythTV setup and have a 500GB hard drive that I partitioned (20GB for ubuntu OS - Feisty Fawn, 2 GB swap and the remaining for my media) and I am running low on disk space and have bought another 500GB hard drive that I want to place in this machine and I would like to expand the partition that I created for my media onto this drive.

Can I convert the partition(s) to a logical partition without losing all of my data?
I **just** responded to a really similar query in another thread.  Take a look here:
[http://ubuntuforums.org/showthread.php?p=2698729#post2698729](http://ubuntuforums.org/showthread.php?p=2698729#post2698729)

---

### Post by mmathur on 2007-05-30
So I followed the high level instructions and backed up the partition (mount point was /var/lib) I wanted to convert to a logical volume, but after I created the volume group and PV and tried to setup the partition to mount, I lost GDM.

I rebooted and I now get an error message on startup:

Server Authorization derectory (daemon/ServAuthDir) is set to /var/lib/gdm but this does not exist.  Please correct GDM configuration and restart GDM.

I have a backup of that entire /var/lib/ directory on the 2nd disk, but I can't mount that second disk (it used to appear as /media/disk, but that I cannot access the drive and all I have is a terminal window and no graphical UI.

Any suggestions on how to reconfigure GDM so I can get the GUI back and hopefully copy the contents of the 2nd disk back into the /var/lib partition?

---

### Post by superm1 on 2007-05-30
> **mmathur said:**
> So I followed the high level instructions and backed up the partition (mount point was /var/lib) I wanted to convert to a logical volume, but after I created the volume group and PV and tried to setup the partition to mount, I lost GDM.

I rebooted and I now get an error message on startup:

Server Authorization derectory (daemon/ServAuthDir) is set to /var/lib/gdm but this does not exist.  Please correct GDM configuration and restart GDM.

I have a backup of that entire /var/lib/ directory on the 2nd disk, but I can't mount that second disk (it used to appear as /media/disk, but that I cannot access the drive and all I have is a terminal window and no graphical UI.

Any suggestions on how to reconfigure GDM so I can get the GUI back and hopefully copy the contents of the 2nd disk back into the /var/lib partition?
Yick,
Honestly, didn't anticipate for this :)
OK.  you can manually mount that disk for now by making a directory in /mnt or /media manually in that terminal, followed by a command similar to this:

```
mount /dev/sda1 /media/mount_point
```

---

### Post by mmathur on 2007-06-01
Great, that worked and I'm able to access the second drive where I backed up the partition.

Now, I hope this is my last question:
The partition that I added to the LVM that I created was formated as XFS.  Do I need to format that partition to XFS after i've added it to the LVM?

Or 

Can I just copy over the backup back into the partition and once I confirm all the data is back, I can format the 2nd drive and add it to the LVM??

Thanks.

---

### Post by superm1 on 2007-06-01
> **mmathur said:**
> Great, that worked and I'm able to access the second drive where I backed up the partition.

Now, I hope this is my last question:
The partition that I added to the LVM that I created was formated as XFS.  Do I need to format that partition to XFS after i've added it to the LVM?

Or 

Can I just copy over the backup back into the partition and once I confirm all the data is back, I can format the 2nd drive and add it to the LVM??

Thanks.
Once you copy the data back over, you will reformat that second drive.  You need to go in fdisk and change its type to LVM.  Add it to the volume group and then to this partition group.  You will then "grow" the xfs filesystem across it.

---

