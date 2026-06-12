---
title: "How to &quot;repair manually&quot; failed file system check"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Graybeard on 2007-04-05
Wanting to recover unused HDD space, I used Disk Manager and gparted to reformat the partitions no longer being used into a single Ext3 partition, leaving the Ubuntu and Swap partitions untouched. The next time I booted Ubuntu I got the lines:

Failed to open the device '/dev/hda6' No such file or directory.
File System check failed. Please repair manually.

Ctrl D exits the window and finishes the boot and everything works but it's a nuisance to have the boot interrupted this way. How do I "repair manually'? I want it to forget that those old partitions ever existed and notice that there is now a nice big empty partion to play around in.

---

### Post by confused57 on 2007-04-05
> **Graybeard said:**
> Wanting to recover unused HDD space, I used Disk Manager and gparted to reformat the partitions no longer being used into a single Ext3 partition, leaving the Ubuntu and Swap partitions untouched. The next time I booted Ubuntu I got the lines:

Failed to open the device '/dev/hda6' No such file or directory.
File System check failed. Please repair manually.

Ctrl D exits the window and finishes the boot and everything works but it's a nuisance to have the boot interrupted this way. How do I "repair manually'? I want it to forget that those old partitions ever existed and notice that there is now a nice big empty partion to play around in.
You can open a terminal, check the output of:
```
sudo fdisk -l
```
the -l is a small "L"
this will show your current partition tables

What's happening is that Ubuntu is still trying to mount your /dev/hda6 from fstab, but it no longer exists.
From the output of "sudo fdisk -l", you can go into your /etc/fstab & comment(#) or delete the partitions fstab is trying to mount that are no longer there.
```
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab
```

---

### Post by mikeyphi on 2007-04-05
I believe that you need to use gparted from the Live disk...so that the drive you are altering is not mounted!

---

### Post by Graybeard on 2007-04-05
Following the advice of Confused57 I find that fstab already includes only the partitions ***after ***the gparted changes, i.e. the ones I want. But rebooting still tries to find the non-existant hda6.  ((I sometimes wish my own memory was that persistant!))

---

### Post by confused57 on 2007-04-05
> **Graybeard said:**
> Following the advice of Confused57 I find that fstab already includes only the partitions ***after ***the gparted changes, i.e. the ones I want. But rebooting still tries to find the non-existant hda6.  ((I sometimes wish my own memory was that persistant!))
I'm not sure what's going on...does the swap partition number from "sudo fdisk -l" agree with the partition number for swap in your fstab...that's the only other thing I can think of is that your swap partition designation may have changed by repartitioning?

---

### Post by Graybeard on 2007-04-05
Confused57

As far as I can tell the current fstab has just what I want; hda1=Ubuntu, hda2=swap, hda3=the new ext3 partition for data. The sizes for all three look appropriate.

Before the gparted changes I had hda1=Ubuntu, hda2=swap, hda3=unused, hda4=extended, hda5=an old Xandros partition, hda6=Xandros' swap. My memory of those now-gone partitions may have some erroneous details but that's the gist of it.

.......and Ubuntu continues to remember.......................

bob

---

### Post by confused57 on 2007-04-05
> **Graybeard said:**
> Confused57

As far as I can tell the current fstab has just what I want; hda1=Ubuntu, hda2=swap, hda3=the new ext3 partition for data. The sizes for all three look appropriate.

Before the gparted changes I had hda1=Ubuntu, hda2=swap, hda3=unused, hda4=extended, hda5=an old Xandros partition, hda6=Xandros' swap. My memory of those now-gone partitions may have some erroneous details but that's the gist of it.

.......and Ubuntu continues to remember.......................

bob

You might want to download the gparted live cd(30 mb download):
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

Maybe you're already using it, but if you're not, maybe it'll help resolve your problem...I think you can right-click on a partition and select "check" and it'll do a filesystem check.  I haven't actually done this myself, but it could be worthwhile trying.

---

### Post by Graybeard on 2007-04-05
> **confused57 said:**
> You might want to download the gparted live cd(30 mb download):
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

Maybe you're already using it, but if you're not, maybe it'll help resolve your problem...I think you can right-click on a partition and select "check" and it'll do a filesystem check.  I haven't actually done this myself, but it could be worthwhile trying.

I have gparted on a "SystemRescue" CD and tried the right-click routine but didn't get a "check" option. It showed the partitions as revised yesterday, specifically:
/dev/hda1  29.29GB ext3
/dev/hda2  3.74GB  linux-swap
/dev/hda3 22.87GB  ext3
which totals 55.9 GB on a nominally 60GB drive, reasonable since Dell's BIOS resides there too.

bob

---

### Post by confused57 on 2007-04-05
The gparted live cd is a later version of gparted and I believe is capable of doing a filesystem check.

---

### Post by psusi on 2007-04-05
There is no filesystem to check as that partition is now gone.  It appears though, that it is still listed in /etc/fstab so the system tries to check it on boot, which fails since it isn't there.

---

### Post by Graybeard on 2007-04-05
Confused57; you are correct, ver. 0.3.4-5. Mine was 0.3.4. The current version does have a "check and restore" function which I ran.  It did not eliminate the "File system check failed" message however.

It is not, however, an obsolete /etc/fstab file as psusi suggests. We checked that several messages ago and found that it listed only hda1, hda2, and hda3 which are the desired partitions. The Ubuntu Disks Manager, however, continues to list partitions hda1, swap, hda3, hda4, and hda6. 

Clearly the file-system-check routine and the Disks Manager are getting obsolete information from a different source than gparted and /etc/fstab. ((and I thought my problem was due to ignorance and inexperience--this is a true puzzler.))

b

---

### Post by confused57 on 2007-04-05
Maybe you could check your /mnt or /media directories, either from a terminal or nautilus, and see if there is a mountpoint there for /dev/hda6.  I don't know how this might cause your problem at boot, but could be something to check out.

---

### Post by Graybeard on 2007-04-05
Confused57;

/dev has file listings named hda1, hda1, hda2, and hda3.

/media has subdirectories named hda4 and hda6 but no files in them.

I will now delete those subdirectories and reboot, then edit this message to include the results.


/media/hda4/ and /media/hda6/ removed and confirmed with ls.

Rebooting, the same old "Failed to open the device......" message comes up

bob

---

