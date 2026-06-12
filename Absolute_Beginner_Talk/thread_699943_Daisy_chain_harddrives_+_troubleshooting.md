---
title: "Daisy chain harddrives + troubleshooting"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by TURNER on 2008-02-17
Hi all, 

I was hoping that someone may be able to answer a question I have regarding troubleshooting hard drives which are daisy chained...

I currently have 5 scsi drives daisy chained, one or perhaps 2 of the drives are intermittently failing and I am trying discover which drives are causing the problem....at the moment if I insert the drives and enter the fdisk -l command I can see that only 3 disks successfully mount... sda1 to 3 however iam unsure how Linux actually mounts these disks....is this the first 3 physical disks in the daisy chain...or could it be disk 1 3 and 5 for example (in other words Linux isn't identifying the disks as per thier physical formation in the daisy chain but simply mounting and labeling the disks as it sees the disks become available)

Aside from attempting to mount each disk individually is there a way which I can identify which hard drive in the daisy chain is failing??

---

### Post by MasterJS on 2008-02-17
Well I'm guessing that the ones failing are the first hard drive that is booted and the last, since numbering starts with 0 and if you have five, it would end with 4.

---

### Post by TURNER on 2008-02-17
doesn't the number identify the partition?

For example Sda1 and sda2 are the same hard drive, partition 1 and partition 2....?

5 separate hard drives should be displayed as follows:

sda
sdb
sdc
sdd
sde

correct??

If indeed Linux identified the hard drives position in the chain, then it should display something like:

sdb
sdc
sdd

If indeed the first and last drives were to be defect....

Or......considering that the first and last drives are defect..would it simply display:

sda
sdb
sdc

(considering that 2 or the hard drives are defect, therefore simply only mounting 3 of the available 5)

---

