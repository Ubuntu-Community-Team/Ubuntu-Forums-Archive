---
title: "partitioning on installation"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by wademunkey on 2007-07-31
I am trying to switch my windows xp dell inspiron 600m to linux.  I try to use the default use entire disk option for formatting,  I go through the entire installation to step 7 it says it is going to be reformat the hard drive as 
The following partitions are going to be formatted:
 partition #1 of SCSI1 (0,0,0) (sda) as ext3
 partition #5 of SCSI1 (0,0,0) (sda) as swap
it starts to go through the installation, and comes up with this error
The ext3 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed.
I have tried to manually partition the hard drive many times with the installer.  I am unable to figure out what is going on. 
Please help me out with this.
Thanks 
Andrew

---

### Post by Kingsley on 2007-07-31
I'm not sure why it goes wrong. Have you tried just totally wiping the drive, rebooting, and then formatting/partitioning to ext3 and swap?

---

### Post by aspen_dv on 2007-07-31
Why does it say SCSI? Do you partition the right disk? Make sure you don't have any USB drive attached...Inspiron 600m should have ATA drive. So instead of sda you should see something like hda...
The error looks like it's trying to create a partition for a device (SDA) that does not exists.

---

### Post by alienexplorers on 2007-07-31
After reading the spec's about this machine I can't even find a sda drive listed.  All the specs shown only a Ultra ATA drive.

---

### Post by az on 2007-07-31
In feisty, everything's scsi.

From the live cd, try running badblocks, to see if the disk is alright

sudo badblocks -s /dev/sda1

another option is to wipe the partition table with cfdisk.

sudo cfdisk

and pick the create blank table option.

---

### Post by wademunkey on 2007-07-31
I am not sure if this actually fixed the problem or not, but i put three partitions on the 60gig hard drive.  one root, one swap, one home.  The only thing I did different was a 10gig root, put the swap at the end of the hard drive and the home in between.
THanks for all the support ubuntu is completely installed and I am about to reboot .
Wish me good luck.
Andrew

---

