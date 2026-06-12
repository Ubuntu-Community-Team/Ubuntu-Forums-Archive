---
title: "What is where??"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by lost4now on 2007-08-11
Below is an fdisk -l of my system.  Can someone tell me from this where my system is installed and where the data is.

Thanks

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19080   153260068+  83  Linux
/dev/sdb2           19081       19457     3028252+   5  Extended
/dev/sdb5           19081       19457     3028221   82  Linux swap / Solaris

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       24321   195358401   83  Linux

---

### Post by Nexus... on 2007-08-11
I'm no expert but I would say your Linux partition(s) have been installed on the sdb1-3

[COLOR="DarkRed"]Device Boot Start End Blocks Id System
/dev/sdb1 * 1 19080 153260068+ 83 Linux                                                  [Main File System (includes files such as /home]
/dev/sdb2 19081 19457 3028252+ 5 Extended                                           
/dev/sdb5 19081 19457 3028221 82 Linux swap / Solaris[/COLOR]

This is my guess I'm not totally sure so don't hold me on it :)

EDIT - I just re-read your question what did you mean when you asked and where is the data?

---

### Post by lost4now on 2007-08-11
Somehow I am under the impression that the saved data or  maybe better called /home directory is not on the same partition as the system. I am quite new to this so the terminology may not be right either.

Thanks

---

### Post by logos34 on 2007-08-11
if you specified a separate /home partition during install, then it looks like your data's here:
**/dev/sdc1 1 24321 195358401 83 Linux**

sdb1 is root

---

### Post by lost4now on 2007-08-11
Then I assume everything needed to restore the system is on sdb1  as long as /home wasn't relocated.  My next step is to make a an image backup with partimage for backup purposes. 
sdb1 should contain everything needed to do that right.

---

### Post by BobCFC on 2007-08-11
if you type **sudo mount** you should be able to tell if /home is on a separate partition from the root / 

(ignore the /proc stuff)

---

