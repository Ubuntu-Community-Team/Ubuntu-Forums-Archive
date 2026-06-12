---
title: "Dapper Back Up Image"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by Gerry Atric on 2006-08-12
I have two hard disks, I have Ubuntu Dapper installed on one and Windows XP on the other with a Grub.
My disks
74.53gig part 1=/dev/hda1 24.50 ntfs,,part 5=/dev/hda5 24.42 ntfs,,part 6=/dev/hda6 15.83 vfat,,part 7=/dev/hda7 9.78 vfat

9.54gig part 1=/dev/hdb1 9.12 Ext3,,Swap part=/dev/hdb5=431.40mg

I am using part 6&7 of the 80gig disk for Ubuntu and the Ubuntu installation is installed on the 9.54gig hard disk.

I have a Rescue Disk with Partimage on same.I want to back up and restore the entire Ubuntu Image from the hard disk it is on /dev/hdb1 to the second hard disk partition /dev/hda7

I would also like to back up the Master Boot Record and the Partition Table as well.
I have manged to work out that I need to mount the partition that I am copying the image to with Partimage as
#mount /dev/hda7 /mnt/temp1
and then make a directory
#mkdir /mnt/temp1/Ubuntu_Backup and then
#cd /mnt/temp1/Ubuntu_Backup
Then I found this online
#dd if=/dev/hda of=Ubuntu_Backup.hda.mbr count=1 bs=512
for the Master Boot Record
and #sfdisk -d /dev/hda > Ubuntu_Backup.hda.pt
and to actually save the Dapper installation as an image to hda7
#partimage -b -z1 -V700 save /dev/hdb1 Ubuntu_Backup.hdb1.partimg.gz

That all worked and I have two images backed up into the hda7 partition.

Next trick is how to I restore it if I crunch my Ubuntu instalation again.

I believe that I would have to #mount the hdb1 partition to be able to install the back up image is that correct. I think the below would be the routine but would appreciate any help I can get :-

#mount /dev/hdb1 /mnt/temp1
# cd /mnt/temp1/Ubuntu_Backup

Restore the Master Boot Record
# dd if=Ubuntu_Backup.hda.mbr of=/dev/hda
Restore the Partition Table
# sfdisk /dev/hda < Ubuntu_Backup.hda.pt

#partimage -e restore /dev/hdb1 Ubuntu_Backup.hdb1.partimg.gz.000
I think I have made some serious blunders in the above code and don't know that my methods and procedures are correct and as I have learnt the above from snippets of code found on the net. Would appreciate someone with knowledge checking same and advising me of my mistakes or better methods etc.
Apologies for the long winded request.:mrgreen:

---

