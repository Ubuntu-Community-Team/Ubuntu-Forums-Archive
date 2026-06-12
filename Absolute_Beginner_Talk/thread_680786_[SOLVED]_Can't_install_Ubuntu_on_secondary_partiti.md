---
title: "[SOLVED] Can't install Ubuntu on secondary partition"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by sheki1 on 2008-01-28
Hello, I downloaded a copy of Ubuntu 7.10 last week and attempted to install on my new HP notebook. As most notebooks (& most windows based computers) they usually come configured with a single partition. I created several partitions, C, D, E, F (it's a 250GB drive) and have Windows on drive C. I want to install Ubuntu to drive D (10GB).

The first problem I encountered was when I put the CD in the drive and rebooted, the Ubuntu install program initiated, but it looked like there were some failures (on what appeared to be a command line interface).

So I restarted by going to Ubuntu Live to check out the OS without installing it and it opened fine. However, when i looked Network connections, only two options showed: Wired and Modem. It did not list a wireless conenction eventhough my wireless system was up and running fine. I did notice that the wireless light was not on on the notebook when running the Live setup.

Then I clicked on the install icon and it took me thru a series of screens. One of the last screens found a single partition on the drive, not the multiple ones I created.  I was a bit confused because I was able to open the drives and folders from the desktop.

:confused:

So there you have it. Any help would be greatly appreciated!!!

Respecfully yours!

---

### Post by mikeyphi on 2008-01-28
What file format are those various partitions?
That is possibly why they are not seen by the installer - if you use the LiveCD and use gparted - you should be able to confirm the setup of your partitions. 
When you go to install you will need to go for the Manual option during the partition phase and choose the partition you want. 
A better option is to leave the disk as free space (except for windows) and allow the installer to find the free space - you will still want to use the Manual option to setup the partitions you want.

The wireless is a separate issue - what card do you have?

---

### Post by dstew on 2008-01-28
Boot the live CD, open a terminal window, and enter the command ```
sudo fdisk -l
```Post the results to the forum.

---

### Post by sheki1 on 2008-01-28
Windows Vista HP. All drives have been formatted using NTFS.

The included wireless card is an Atheros AR5007 802.1b/g WIFI adapter and have the standard Verizon FIOS wirelesss router.

and thanks for all your help!!

---

### Post by Hurk on 2008-01-28
I am brand new to Linux, however here's my 2 cents.  I had the same problem.  I was installing UBUNTU on a laptop that had Windows XP on it.  I ran the install for linux and encountered errors as well.  I ended up getting a copy of Partition Magic to delete the partition UBUNTU had created to begin with and ran the install again. Just an fyi, in the partionar that UBUNTU uses during install, when it gives you the slider to resize and create a partition.  The Left side of the slider is the windows partition you are reducing, and the right side is the size of the partition for linux.  If you intend on any future installs or removals of partitions on your harddrive, I would highly recommend Partitioning software.  It makes the process 100 times easier. My 2 cents good luck.

---

### Post by mikeyphi on 2008-01-28
> **sheki1 said:**
> Windows Vista HP. All drives have been formatted using NTFS.

The included wireless card is an Atheros AR5007 802.1b/g WIFI adapter and have the standard Verizon FIOS wirelesss router.

and thanks for all your help!!

OK - here's my suggestion!
Read this first: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
 - unless you're confident about partitioning (remember Ubuntu will require 2 partitions)

Delete all unused partition. Install Ubuntu and select Manual partitioning setup Ubuntu in your choice of partition size. Setup other partitions later.

Wireless - Read here:[http://ubuntuforums.org/showthread.php?t=512828&highlight=how+to+atheros](http://ubuntuforums.org/showthread.php?t=512828&highlight=how+to+atheros)

---

### Post by sheki1 on 2008-01-28
I used Acronis Disk Director Suite 10 to partition the HD into multiples.

Step 5 of the Install (Select a Disk) it only shows one option. /dev/something or other

---

### Post by sheki1 on 2008-01-28
I'll take a look at those documents, thanks.

But why does Ubuntu require 2 partitions?   I didn't see that as a requirement in the install docs I read...

---

### Post by bumanie on 2008-01-28
You must have a /root partition and a /swap partition. Many choose to also have a separate /home partition as well. This way if something goes very wrong with the main file system, all your documents etc. are safe in the /home partition as you only reinstall ubuntu to /root.

---

### Post by sheki1 on 2008-01-28
I just read on another thread that Ubuntu won't install to a NTFS drive.

Is it possible that because all my partitions are formatted as NTFS, Ubuntu's installer is having difficulty finding someplace to install and so it's trying to create a partition out of the whole?

Thanks!

---

### Post by indytim on 2008-01-28
Follow Mikephi's advice and spend a few minutes and read the references he supplied.  It'll make your journey a lot easier.

IndyTim

---

### Post by sheki1 on 2008-01-29
> **dstew said:**
> Boot the live CD, open a terminal window, and enter the command ```
sudo fdisk -l
```Post the results to the forum.

ran sudo fdisk -l and here's my results:

Disk /dev/sda: 250.0 GB 250059350016 bytes
255 heads, 63 sectors/track, 30401 cyliders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x122cd09b

Device        Boot   Start   End       Blocks             Id    System
/dev/sda1  *         1         3916     31455238+    7     HPFS/NTFS
/dev/sda2             5223   27557   179405886+  7     HPFS/NTFS
/dev/sda3             3917   28832   200137690     5     Extended
Partition 3 does not end on cylinder boundary.
/dev/sda4            28832  30401   12603052+    7     HPFS/NTFS
/dev/sda5            3917    5222     10490413+    83   Linux
/dev/sda6            27558  28832   10238976       7     HPFS/NTFS

Partition table entries are not in disk order.

Prior to getting these values I actually changed the 10 GB partition I had setup in Vista from NTFS to Ext3 (after reading some posts about this type) with DiskDirector.

Now when I run the Install, step 4 (Who are you?) of 6 (from a doc I saw on installing) does not show. 

The next step, Select a disk, now shows two options:
   Guided - use entire disk
       SCSI1(0.0.0)(sda) - 250.1 GB ATA FUJITSU MHY2250B
   Manual

If I click on Manual, i get screen Prepare Partiion
/dva/sda

If I click on Guided, then it shows me the screen Who are you?

At this point I stopped the installation because I didn't want to delete my Vista partition.

By the way, I looked at Mikephi's doc link and noticed that the install showed a dual-boot option with a Guided slider, but as I mentioned above, the Guided option only showed for the entire disk.

Thanks

---

### Post by dstew on 2008-01-29
Use Manual, and install Ubuntu to /dev/sda5

---

### Post by sheki1 on 2008-01-29
I've now gone back to Windows Vista and reran DiskDirector and deleted the 10GB partition. Now when I go to the Live CD and run the install, I get the Guided slider option - 

resize SCSI (0.0.0), partition @3 (sda) and use freed space

New partition size: 58% (97.9GB).

Not sure why it says 97.9GB since there are no partitions of that size...

---

### Post by bumanie on 2008-01-29
The partitioner is going to change the partition configuration you have set up. If you don't want it to do this you restart the live cd and choose manual, once you get to the partitioning stage. Then you can direct /root to what should be an unallocated 10g partition. Be aware you also need to make a /swap partition during partitioning. There is no exact size you should set, but most people set it at double the amount of their actual physical ram ie if you have 1g of ram, set swap size to 2g.

---

### Post by sheki1 on 2008-01-29
After many trials and tribulations I have conquered the Ubuntu Installation process.

However, I couldn't have done it without all YOUR help.

So, MANY THANKS TO YOU ALL!!!


now I've got other issues to resolve/figure out, but for now, am signing off...

[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)
:guitar:

---

