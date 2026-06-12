---
title: "Uninstalling UBUNTU/erasing partitions"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by doctorproteus on 2007-06-04
I am simply not computer savvy enough for UBUNTU yet, and don't know how to uninstall.  Can anyone help, or tell me at least how to undo it's partition?

---

### Post by daimaru on 2007-06-04
all i can tell you is that you can delete it anyway you want... partition magic or something, but once you get rid of ubuntu  (assuming here u had a dual boot setup : win/ubuntu) you wont be able to boot into windows either, because your master boot record does not exist anymore. so make sure you have your windows cd handy and know your admin password to your windows installation. 
all you have to do from here is instert ur win cd start the setup, when u get to the install win stuff choose recovery console or recover windows or something. this should get you to a command prompt where you have to login to your win installation and then in order to get your mbr back you type in 
```
fixmbr
```
meaning fix master boot record.. thats it you back in windows land. 
too bad we're going to loose you to that OS.

---

### Post by starcraft.man on 2007-06-04
> **doctorproteus said:**
> I am simply not computer savvy enough for UBUNTU yet, and don't know how to uninstall.  Can anyone help, or tell me at least how to undo it's partition?

[Gparted Live CD ]("http://gparted.sourceforge.net/livecd.php")will help ya delete the old partitions, just download burn and boot into it. Then delete what you don't need. To get your old MBR back, this is the guide I think microsoft recommends, its really just the fixmbr command in the console. [Read this page, section on replacing MBR from console]("http://www.microsoft.com/technet/prodtechnol/windows2000serv/reskit/prork/prcb_dis_dgya.mspx"). That should be it.

At least ya gave it a shot, maybe next time around :) Have a nice day.

Edit: hehe, GParted daimaru, keep a copy handy its a good partitioner. :)

---

### Post by bettyhills on 2007-06-04
If you use Partition Magic method described below, boot into Windows and restore your MBR to its original Windows setup as described in an earlier post, BEFORE repartitioning and removing Ubuntu. You will be doing all of your corrections from Windows.

Before starting, it is critical to create a boot disk for Windows.  Install Partition Magic 8 as instructed.  Make a 2-disk recovery set as directed by Partition Magic 8.  You could be needing both.  Backup anything important.

That said, Partition Magic 8 (about $20 retail box on eBay) is so clear that the process is easy and straightforward.  We will use Partition Magic 8 in Windows to remove the partitions and delete Ubuntu.  PM8 can't delete the Ext3 partitions as they are so we format them out of existence.  

You must carefully select each of the _Ubuntu_ partitions in turn and ask PM8 to format them as FAT32 until all are done.  That "uninstalls" (destroys)  Ubuntu.  Then in turn delete each former Ubuntu partition in PM8.  (Be careful to leave the NTFS Windows partition, and one or two small other original PC partitions alone.  They are part of the original Windows installation.  In PM8, you will see that each of them is identifiable as a PRIMARY partition.)  

All of the space freed by deleting the partitions will now be "unallocated".  Have PM8 format again all the unallocated space as one big partition to match the file system of your Windows partition (NTFS, FAT32, or FAT).  Once that is done, tell PM8 to merge the two (Windows and newly formatted) partitions together, and you will be back to Windows only on one hard drive in a single partition.  

If you have restored the MBR before starting, your system should boot.

P.S. Anyone wanting to remove Ubuntu partitions in order to _REINSTALL Ubuntu _in a different partitioning scheme should do everything outlined above EXCEPT there is no need to edit the MBR.  Use the Ubuntu FF 7.04 live CD in the CD-ROM drive, restarting from Windows after the partitioning, and Ubuntu will overwrite the MBR during the new installation.

---

