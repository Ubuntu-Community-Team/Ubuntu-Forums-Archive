---
title: "[SOLVED] Cant install ubuntu"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by nathan1936 on 2007-12-22
Ok, I have the live cd running fine, but the gparted app wont start, and when I click install on the desktop, it freezes on searching hardware. AGAIN
Im on a compaq evo n600c
1.2ghz pentium M III
1024 mb ram

I formatted my hd and deleted all the partitions because it wouldnt work before either, but it still wont go onto my hd. Is it compatible with NTFS file system? Or should I change it to fat32 or something...
A little help? 
Like I said the live cd works fine, its just my stupid harddrive...
Any ideas?

---

### Post by taurus on 2007-12-22
Yes, format it to fat32 if you can.  Also, you can try and use the alternate CD to install Ubuntu on your machine if you wish.  That's another option for you to try.

---

### Post by nathan1936 on 2007-12-22
I looked in Computer
and my hd is gone now!!!
WTF
I deleted vista and the partition, and now my hd isnt seen my ubuntu

---

### Post by t0p on 2007-12-22
> **nathan1936 said:**
> 
I formatted my hd and deleted all the partitions because it wouldnt work before either, but it still wont go onto my hd. Is it compatible with NTFS file system? Or should I change it to fat32 or something...
A little help? 
Like I said the live cd works fine, its just my stupid harddrive...
Any ideas?

You can't install Linux onto NTFS.  You'll have to reformat the partition.  I like ext3.

---

### Post by StGeorge on 2007-12-22
Do Not Bother with new cd's.
If u want ubuntu use 6.06 live

---

### Post by jken146 on 2007-12-22
It will format the appropriate parts of the hard drive after the partitioning stage of the installer.  Unfortunately for you, it's getting stuck just before that part.  What I suggest is: (1) check the md5sum of the iso you downloaded and (2) check the CD for defects using the tool on the CD.  If either of these shows a problem, re-download or re-burn the CD (4x or less) as necessary.

---

### Post by jken146 on 2007-12-22
> **StGeorge said:**
> Do Not Bother with new cd's.
If u want ubuntu use 6.06 live

I disagree.  I have used Edgy, Fiesty and Gutsy live CDs with great success on many different machines.  Telling people to get Dapper Drake more than a year and a half after its release isn't a good way to introduce them to the latest and greatest desktop linux distro.

---

### Post by jken146 on 2007-12-22
> **nathan1936 said:**
> I looked in Computer
and my hd is gone now!!!
WTF
I deleted vista and the partition, and now my hd isnt seen my ubuntu

If you deleted all the partitions then there's nothing to display in Computer.  Gparted should show the disk though.

---

### Post by lgambett on 2007-12-22
Just to add that many people on the forum report successful installation on compaq evo n600c and recent Ubuntu versions. I disagree with the indications to use Ubuntu 6.06 and use FAT32. FAT32 would give you in the future a lot of problems due to lack of full permission support.

---

### Post by Majorix on 2007-12-22
> **StGeorge said:**
> Do Not Bother with new cd's.
If u want ubuntu use 6.06 live

I disagree too.

Don't do what I did and upgrade to Hardy just yet, but Gutsy should do just fine. 6.06 is just too old.

---

### Post by nathan1936 on 2007-12-22
It found an error in 1 file on the disk so I'm going to re-download the torrent, and burn slower.
I see this at the beginning before the boot screen when I start the cd:

[   177.784000] Buffer I/O error on device fd0. logical block 0
[   211.728000] Buffer I/O error on device fd0. logical block 0

Any constelation?

Thanks for putting up with my problems everyone. Once I get started, I will be able to figure it out, but I need to at least get it up and running. but still thanks! ):P

---

