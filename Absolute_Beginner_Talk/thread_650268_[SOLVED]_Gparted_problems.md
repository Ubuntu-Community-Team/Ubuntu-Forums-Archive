---
title: "[SOLVED] Gparted problems"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by dreadh3ad on 2007-12-26
I have a 250 gig hard drive with 3 primary partitions.  
Ubuntu
Swap Space
Ext 3
115 gigs left unpartitioned

Gparted is not recognizing any of the partitions.  However i can still access my data through the mount point.  This all stems from my tinkering.

Gparted would not let me create a 4th ext3 partition.  I attempted to create a logical partition and then an ext 3 under the logical.  This did not work.  Gparted said it did not have full access to the partition tables .  I then unmounted sdb using the umount command.  After a reboot gparted does not recognize any of my partitions.  It seems the entire disk as unallocated space.  
I have over 100 gigs of information i cannot lose.  Transferring it to another disk would be painful.  What can i do without losing my data?

---

### Post by JillSwift on 2007-12-26
1st, take the pain. If you can not lose that data, you must back it up!

---

### Post by wormser on 2007-12-26
I believe you can only have 3 logical partitions.  Inside a logical partition you can have multiple extended partitions.  That is a computer thing and not an Ubuntu thing.  Gparted needs to be on an unmounted drive.  Boot into the Ubuntu live CD and run Gparted or download the Gparted Cd.

---

### Post by dreadh3ad on 2007-12-26
What can i do in this situation and why isnt gparted recognizing any of my existing partitions?

---

### Post by lgambett on 2007-12-26
It seems like you have no root (administrator) access. Try to launch Gparted from a terminal with the command gksu gparted.

---

### Post by dreadh3ad on 2007-12-26
No difference

---

### Post by erginemr on 2007-12-26
> **wormser said:**
> I believe you can only have 3 logical partitions.  Inside a logical partition you can have multiple extended partitions.  That is a computer thing and not an Ubuntu thing.  Gparted needs to be on an unmounted drive.  Boot into the Ubuntu live CD and run Gparted or download the Gparted Cd.

+1 to that. You should work with GParted on unmounted partitions, and use either Ubuntu Live CD or the GParted Live CD specifically designed for this job:

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by dreadh3ad on 2007-12-26
Well that would be the problem.  The hard drive was mounted when i launched gparted.  In an attempt to fix this i used umount /dev/sdb and rebooted.

Now gparted will not recognize any of the partitions already on my drive.  However the entries are still within fstab.

---

### Post by crunchfighter on 2007-12-26
I am confused by the term mount.  What is a monted drive?

I am having a similar problem partitioning for install.  My 160GB drive has 40 GB of windows set as NTFS.  gparted shows the entire drive as unallocated.  I've tried from the SystemRescueCD LiveCD and the Partition option when using the Ubuntu LiveCD during install.  

Windows shows the partition, but I can obviously not change it while booted into windows.

It shows the entire drive as unallocated so I can not partition it with any degree of certainty that my drive will not be formatted.  (Yes it is backed up, but I don't want to intentionally shoot a drive if I don't have to.)

Any thoughts?  Anyone seen this before?

Craig

---

### Post by crunchfighter on 2007-12-26
What is fstab?

---

### Post by dstew on 2007-12-26
> Now gparted will not recognize any of the partitions already on my drive. However the entries are still within fstab.In order to manipulate the partition table of a drive, the drive cannot be in use by the system. It is unclear from your posts if you are running a LiveCD system, or an installed system.

In order to partition a hard drive, you cannot use the Ubuntu system on that same drive. Umounting the drive and booting again will not help, since the drive will be mounted again when you boot. Since you mention fstab, this indicates that you may be using the installed system. The LiveCD should not have an fstab, since it does not retain any permanent files. Make sure you are using a LiveCD system, or you can also get a gparted Live CD as recommended by erginemr.

---

### Post by dreadh3ad on 2007-12-26
I downloaded and ran the live cd with the same results.  Gparted does not recognize any of my partitions, but i can still access the data via the mount points.  

Im guessing i might as well reformat?

---

### Post by psusi on 2007-12-26
Crunch:  Mounted means that the kernel is actively recognizing and accessing a filesystem there.  When you mount a new filesystem, you have to place it somewhere in the filesystem hierarchy.  When the kernel boots up, it mounts one filesystem as the root ( / directory ), and after that, you can mount new filesystems to subdirectories of the root.  For instance, some people like to set up a dedicated partition for their /home directory so they can easily wipe out the root and reinstall, without loosing their personal files.  

fstab refers to the file /etc/fstab, which tells the system which filesystems it should mount when it boots, where they should be mounted, and any additional options to apply to them.  

dr: please post the output of sudo fdisk -lu

---

### Post by dreadh3ad on 2007-12-26
How could my partitions be mounted and accessible but gparted is not able to detect them?  Gparted sees the disk as unallocated, but there are three partitions and 115 gigs of unused space.  This problem essentially this leaves me with 115 gigs of unpartitioned space i cannot access.

---

### Post by wormser on 2007-12-26
> **dreadh3ad said:**
> Well that would be the problem.  The hard drive was mounted when i launched gparted.  In an attempt to fix this i used umount /dev/sdb and rebooted.

Now gparted will not recognize any of the partitions already on my drive.  However the entries are still within fstab.

You need to use Gparted from the live CD or download the [Gparted CD]("http://gparted.sourceforge.net/download.php").  The recognizing of the partitions might be solved with the live CD.  Make sure you back up all your data first.  I do not think there is any way around this.  You are going to have to destroy one of your logical partitions, recreate it and put extended partition(s) in it.

Update:  Some how I missed your other post.  I do not think you need to start completely over.  Download [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") and it should fix your disk problems.  Then follow the directions above.

```
sudo apt-get install testdisk
```

---

### Post by crunchfighter on 2007-12-26
I just had success.  I have a Gparted LiveCD.  I shut the laptop all the way off and then turned it on with LiveCD in the drive (not restart, but shutdown-wait-turn on).  This time, it showed me the windows partition as allocating the entire disk like it should have.  Someone earlier posted this, it worked.

---

