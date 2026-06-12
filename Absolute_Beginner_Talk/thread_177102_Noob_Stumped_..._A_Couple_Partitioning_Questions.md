---
title: "Noob Stumped ... A Couple Partitioning Questions"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by Penq on 2006-05-15
Hello fellow Ubuntu brothers and sisters!  This noob needs your help please.  

I have searched all day trying to solve my partitioning questions. Parts were solved by researching and finding / installing NTFSProg.  But still have a few more... 

How do I use / move unallocated space located at the end of a drive? (Drive does NOT contain any operating systems just media backups. However,  I do use the system to dual boot just not the drive in question ... Not sure if that matters or not?) 

Anyway, I have one partition at the beginning of the drive that I would like to add the unallocated space to. Also, three additional partitions exist in between the first and unallocated space.  

Do I have to create a partition out of the unallocated space first then merge the partitions?  Or is there an easier way?  Is this possible to do in Gparted?

I prefer to use a free program as funds are a little tight right now.  I have GParted with NTFSProg installed.  It seems that this should work but I'm a little stumped as to the "How". 

Thanks in advance for any suggestions and help! :)   

Penq
:cool:

---

### Post by aysiu on 2006-05-15
You can add space to the end of a partition but not the beginning of it.

For example, if you had...

Partition 1
Free space
Partition 2

... you could tack that free space on to Partition 1, but you could not tack it on to Partition 2.

---

### Post by richbarna on 2006-05-15
Hi Penq,
Okay, so, you've got : OS1-OS2-part3-Part4-Media Files ?
And you are trying to ...What? and Why?
Are you dual booting Windows and Linux ?
Do you want to Keep the media files, Delete them, Access from both OS's ?
Are you trying to make a bigger partition for Windows or Linux ?
More specific info would make it easier for us to find you a solution :)

---

### Post by aysiu on 2006-05-15
A screenshot of your partition table or the output of *sudo fdisk -l* would be a good place to start.

---

### Post by Penq on 2006-05-15
[QUOTE=aysiu]A screenshot of your partition table or the output of *sudo fdisk -l* would be a good place to start.[/QUOTE]

Thanks guys and gals!  

Currently, I'm away from the box where I'm having the issue.  As soon as I make it home I'll reply back.  Didn't expect such a quick response!  Wow, thanks!

Penq

---

