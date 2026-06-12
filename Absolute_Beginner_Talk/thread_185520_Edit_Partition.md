---
title: "Edit Partition"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by likewhiteonrice on 2006-05-31
Is there a way to edit your partition?

I dual boot windows and I planned on giving ubuntu 20gigs, and leave the rest (80gb) for windows, but it happend the other way around....
thanks,
likewhiteonrice

---

### Post by Israfel on 2006-05-31
I've never actually re-sized a partition myself, but you should be able to do it from qtparted (linux) or partition magic (windows).

---

### Post by tonyr on 2006-05-31
You need to give some more specifics.  Are you installing Breezy (5.10) or 
Dapper (6.06).  Are you using an install CD or a LiveCD?  Did you already
have Windows installed, and if so what version (NT,Win2k,ME,XP)?  What
did you do to get to the partitions you have now?  Can you boot both Windows
and your installed Ubuntu now (ie, did the Ubuntu install succeed)?

---

### Post by aysiu on 2006-05-31
Boot into Ubuntu, paste this command into the terminal: ```
sudo fdisk -l
``` and then post the output back here.

---

### Post by likewhiteonrice on 2006-05-31
[QUOTE=aysiu]Boot into Ubuntu, paste this command into the terminal: ```
sudo fdisk -l
``` and then post the output back here.[/QUOTE]

  Device   Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1824    14651248+   7  HPFS/NTFS
/dev/hda2            1825        9404    60886350   83  Linux
/dev/hda3            9405        9729     2610562+   5  Extended
/dev/hda5            9405        9729     2610531   82  Linux swap / Solaris

---

### Post by aysiu on 2006-05-31
So this is what it looks like?

/dev/hda1 Windows 15 GB
/dev/hda2 Ubuntu 60 GB
/dev/hda5 swap 2 GB

And you wanted it to be

/dev/hda1 Windows 60 GB
/dev/hda2 Ubuntu 15 GB
/dev/hda5 swap 2 GB

That's going to be tough unless you have an external hard drive or iPod on which to put the Ubuntu partition temporarily.

This is how you would do it:
1. Use a live CD and PartImage to copy the Ubuntu partition image to an external hard drive.
2. Use that same live CD to delete the Ubuntu partition and enlarge the Windows partition. 
3. Then copy the Ubuntu partition back with PartImage.

Here's a tutorial on PartImage:
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

Can I ask, though, why you want the Windows partition to be bigger? With [http://www.fs-driver.org](http://www.fs-driver.org) you can read/write the Ubuntu partition from Windows, but you can only read Windows NTFS from Ubuntu (you won't be able to modify, create, or delete files).

Read more about partitioning schemes here:
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

---

