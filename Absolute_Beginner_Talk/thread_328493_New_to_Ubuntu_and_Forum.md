---
title: "New to Ubuntu and Forum"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by Ramesses on 2006-12-30
Hi:

I am brand new to this forum and to Ubuntu.  I installed Ubuntu about a week ago and everything is working great – very happy.

What I did was to add a second hard drive to my PC where I installed tthe Linux based OS.  I also purchased an external hard drive (Western Digital - “My Book – essential model” - 250 GB.)  for backing up my two hard drives – I live in fear of a disk crash! The first partition (~150GB) I formated in NTFS to backup my XP.  The second partition (~100GB) is still unformatted)  for my Ubuntu.  Therefore, I have several questions.  

1.What file system should I use for the second partition in my external (backup) HD?  EXT2, EXT3, or VFAT?  Which file system works better for Ubuntu and/or Kubuntu (I have not decided if I will install Kubuntu or not – not enough knowledge at this time.)  That partition has been allocated for backing up the Linux-based system only.
2.When looking at the format program in “Disks Manager”, it prompted me for “Access Path.”  I think it should be either “/root” or “/home”.  Am I right?
3.How do you do a full back up of everything in the the HD dedicated to Ubuntu. 

 As the world is patiently awaiting to migrate to Vista, I have decided to migrate to Linux.  I am not going to contribute one more penny so Billy Boy can get to his 100 billion mark – I've had it with Microsoft, Intel and all of them.  Vista will make sure that people run out and spend thousands in new hardware and compatible software. 

Thank you for your help.  It is a bit more complicated than I thought, but I am a believer and I will migrate – it might take a year or so. 

Thanks and best regards,

Ramesses:confused: :confused:

---

### Post by Sef on 2006-12-30
> 1.What file system should I use for the second partition in my external (backup) HD? EXT2, EXT3, or VFAT?

Use ext3.

> (I have not decided if I will install Kubuntu or not – not enough knowledge at this time.)

If you are new to Linux, then use Ubuntu.  More people here use it, so help is generally faster and more likely.

> 3.How do you do a full back up of everything in the the HD dedicated to Ubuntu. 

Use [Partimage]("http://www.psychocats.net/ubuntu/partimage").

> 2.When looking at the format program in “Disks Manager”, it prompted me for “Access Path.” I think it should be either “/root” or “/home”. Am I right?

Be careful.  If you format, you will overwrite whatever is on that partition.

---

### Post by Ramesses on 2006-12-30
Hi SEF:

Thanks for your help.  I have nothing in the partition.  It is unformatted. 

Best regards,

Ramesses

---

### Post by Sef on 2006-12-31
Ubuntu uses GParted as a partitioner on the cd, so you can partition while you are installing Ubuntu.

---

