---
title: "Intel Mac question about install"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by MN Noob on 2007-11-05
I am on the last part of the install prep. I have three partitions setup. One is MacOS 10.4. One is for Ubuntu. The other is swap for Ubuntu.
I am on the last screen for installation and I get the following prompt. I need to make sure that this will not mess up my ability to boot into MAC OS. I have looked online for an answer but all I have come up with is that it will not destroy the Mac partition. That is fine, but what I need to know is will I still be able to boot into Mac OS?
======
If you continue, the changes listed below will be written to the disks. 
Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.

The partition tables of the following devices are changed: 
 SCSI3 (0,1,0) (sda)

The following partitions are going to be formatted:
 partition #4 of SCSI3 (0,1,0) (sda) as swap
 partition #3 of SCSI3 (0,1,0) (sda) as ext3
=======

---

### Post by Perpetual on 2007-11-06
I am assuming that the partition #3 of SCSI3 (0,1,0) (sda) as ext3 is your / (root).  partition #4 of SCSI3 (0,1,0) (sda) as swap is obviously your swap partition.  I see no problem with what is being done as long as you do not format the partition containing your mac install, which from what you posted is not the case.

Since this is 21 hours later, you may have already made the leap.  Let us know the results!

---

### Post by MN Noob on 2007-11-06
Thanks Perpetual. I have not done it yet. I am currently working on a video project for brother-in-laws bday on my Mac so I have not had much time to do anything else.
I think for good measure I am going to pick up a external HDD.(need one anyways)
And you are correct about the partition formatting of #3 and #4.
I'll post once I get it done.

---

