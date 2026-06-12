---
title: "Data Recovery"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by dlehman on 2006-09-22
I have 2 hard drives hda has and ntfs for xp a fat just for storing files and another ntfs for storing files 
hdb had 4 partitions  an ext3 or reiserfs (don't remember) ext2 for /boot a swap and a fat for sharing files between windows and Linux.  this was all under Gentoo, then I deiced to switch to Ubuntu so I started moving everything from my home directory to the fat partitions.  when I installed Ubuntu I chose to use the entire disk for hdb and forgot that I had that fat on the end so now hdb has 2 partitions ext3 for / and swap.  I have used a few windows data recovery programs and my files are corrupt. the most of it I could care less about but there are a few thing I really want such as my quicken file.  

are there any data recovery applications for Linux that will recover files from a fat 

thanks

---

### Post by az on 2006-09-22
See here:

[http://foremost.sourceforge.net/](http://foremost.sourceforge.net/)

Run the live cd, install build-essential and then download and compile foremost.  YOu will find that easier than using the older versino which is in the repositories.

---

### Post by UniRecovery on 2006-09-23
Were you prompted to format the hard disk or no?

---

### Post by dlehman on 2006-09-23
I used the text mode install and I had three options use entire disk, use entire disk with lvm, manulay partition.  I chose to use the entire disk, I forgot I had that fat partition at the end of the disk.  I asked me to confirm change to the partition table so yes it did format the drive.

and I not really sure how to use foremost maybe I didn't give it enough time, I was not gettning any status indicator though

I am running another windows recovery program right now

any sugestion are great
Thanks

---

