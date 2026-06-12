---
title: "Install - partition problem"
date: 2008-03-30
forum: Apple Intel Users
---

### Post by Ubentu on 2008-03-30
During the partition phase of install (7.10) from a LiveCD, I got the following warning:
"The FATs don't match. If you don't know what this means, then select cancel, run scandisk on the file system, and then come back. Not sure what scandisk is - the help app shows no results for "scandisk." 

When I select "Cancel" I get this message: "The test of the file system with type fat32 in partition #1 of SCSI3 (0,1,0) (sda) found uncorrected errors. If you do not go back to the partitioning menu and correct these errors, the partition will be used as is."

Partition info:
/dev/sda1 (fat32) mount: /media/EFI System Partition (209 MB)
/dev/sda2 (this has Mac OS X 10.4, recently updated (63082 MB)
/dev/sda3 (this is an eDrive partition set up by TechTool Pro (7516 MB)
/dev/sda4 (ext3) mount: / (this is a partition I edited in the partitioner for Ubuntu)
(plus various free spaces of 134 MB)

Suggestions? Need more info? Any help is appreciated.
Thanks,
BR

---

### Post by cyberdork33 on 2008-04-01
Tell it not to mount the EFI partition and ignore the error.

---

### Post by Ubentu on 2008-04-05
Thanks for the assistance. Your wiki entry for Intel Macs [https://help.ubuntu.com/community/Intel_iMac]("https://help.ubuntu.com/community/Intel_iMac") was just what I was looking for (i.e., how to skip the partition editing in the installer). I'm up and running now!

Ben

---

