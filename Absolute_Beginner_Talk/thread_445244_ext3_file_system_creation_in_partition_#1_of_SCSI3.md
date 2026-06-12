---
title: "ext3 file system creation in partition #1 of SCSI3 (0,0,0) (sdb) failed."
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by PMatt on 2007-05-15
I had this working yesterday, but I kept getting error 21 so I tried to reinstall. Now I keep getting this message:

The ext3 file system creation in partition #1 of SCSI3 (0,0,0) (sdb) failed.

---

### Post by Hobo Joe on 2007-05-15
This happened to me too. Are you using Gparted to make the partition?

---

### Post by PMatt on 2007-05-15
> **Hobo Joe said:**
> This happened to me too. Are you using Gparted to make the partition?

I used it which probably wasn't very smart of me. I tried to delete everything using gparted and then reinstall with the live cd.

---

### Post by PMatt on 2007-05-15
Is there anyway I can just delete everything on my external hdd or use Gparted to set it up for the ubuntu live cd install?

---

### Post by JoshuaPDavis on 2007-06-27
I bought a new computer and tried to install from the live cd, and I had the same error.  

My problem was that I had mounted the existing partitions on the hard drive while running in live cd mode.  I umounted those partitions and now it is working.  

You could try checking to see if any of your sdb partitions are mounted.  

mount | grep sdb

---

### Post by AlexFoster on 2007-07-22
Here's the situation:

Using PartitionLogic, I completely reformatted my hard drive on my Dell M170 laptop and I receive the 'ext3 file system creation in partition etc etc' message when I try to install Xunbuntu from the CD. 

I'm a total noobie at this, so use small words, please.

---

### Post by wuwongy on 2007-07-23
I had a similar problem and found this link on the forum 
It worked for me

[https://answers.launchpad.net/ubuntu/+question/5296]("https://answers.launchpad.net/ubuntu/+question/5296")

Marc

---

### Post by AlexFoster on 2007-07-23
Thanks, I'll give that a shot!

---

### Post by timolicious on 2008-02-17
> **wuwongy said:**
> I had a similar problem and found this link on the forum 
It worked for me

[https://answers.launchpad.net/ubuntu/+question/5296]("https://answers.launchpad.net/ubuntu/+question/5296")

Marc
do you have the solution for ubuntu?

---

### Post by blemere on 2008-07-20
I had the same problem and followed the above instructions. The only thing I did extra was eject or unmount the drive when I was done changing the settings. I was able to install just fine after that.

---

