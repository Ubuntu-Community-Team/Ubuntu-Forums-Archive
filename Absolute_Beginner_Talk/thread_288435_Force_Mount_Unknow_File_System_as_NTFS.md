---
title: "Force Mount Unknow File System as NTFS"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by coolhands_99 on 2006-10-29
I have a laptop with an 80GB HD. I have two NTFS partitions one is 15GB and holds windows the other is the rest of the space and is where I keep all of my files. I put windows into hibernate and tried to resize the larger partition and install Xubuntu. Well after a little of trouble and the install trying to format my NTFS partition I gave up for the night.

When I booted back to windows (remember it was hibernating) everything was working fine. So I messed around for a while and looked up more info in installing Ubuntu and went to bed agian put windows into hibernate. The next night I booted back to windows and did some work and was able to use the larger partition without any problems. I watched some movies from the larger partition and decided to shut windows down when I went to bed.

The next day when I tried to boot windows I got HAL.DLL is missing or corrupt (I'm not worried about this). So I used the windows repair to replace the file with no avail. I discovered that my larger partition was now showing up as unknown FS in every  partition manager I tried to use. I tried windows, Ubuntu, and Knopixx CDs to try and read access the partition. When I try to mount the partition using -t NTFS it tells me that the FS is unknown and will not mount the partition.

Now down to my question. I backed up my critical files but I have realized there were a few files that are not critical but I would like to retrieve it at all possible. Is there a way to force a partition to be mounted using NTFS.

Thanks for the help.

---

### Post by Boelcke on 2006-10-29
You might get some better replies than mine, as I'm not up on the current state-of-affairs with linux and NTFS.  I think some improvements have been made lately on how Linux handles NTFS.  Historically, however, Linux hasn't played well with it.  

I just don't trust it.  I've only mounted NTFS volumes ReadOnly, if at all.  Currently, I don't mount any of 'em.  My almost-never used Windows partition is NTFS, and I used to have a FAT32 area setup for sharing files between OSs.

---

### Post by coolhands_99 on 2006-10-30
The problem isn't that I can't get Ubuntu to read NTFS. I was messing with resizing my larger prtition now it shows up as unfomated. I know that data is still there as NTFS partition. Windows was able to see it for two days when it woke up from hibernating. Once I shut down windows I was no longer able to access the partition. 

I was just wanting to know if there was a way to force Ubuntu to mount the partition as NTFS no mater what it thinks the file system is.

---

### Post by steve.horsley on 2006-10-30
I wonder what type the partition is now marked as. Can you post the output of **sudo fdisk -l** - I believe that ntfs is type 7. If it shows as some other type, you can fix it with **sudo cfdisk**, but be careful with that program.

---

### Post by coolhands_99 on 2006-10-30
Ok I used the fdisk command and the cfdisk command. The partition was listed as type 83 and I changed to 07. Now fdisk shows it as an NTFS patition but ubuntu still shows it as unformated. When I try to mount the partition I get the following error.

mount: wrong fs type, bad option, bad superblock on /dev/hdc2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by Sef on 2006-10-31
Use [GParted]("http://gparted.sourceforge.net/") to reformat the larger partition.  It is a graphical partitioner.

---

### Post by rccharles on 2006-10-31
> **coolhands_99 said:**
> 

Now down to my question. I backed up my critical files but I have realized there were a few files that are not critical but I would like to retrieve it at all possible. Is there a way to force a partition to be mounted using NTFS.


You need to look for data recovery software which will try to recover your lost data.  Do a google search on data recovery software. 


The O'Reilly book Knoppix Hacks by Kyle Rankin includes a chapter on data recovery and the Knoppix Live CD. Knoppix is a Linux distribution designed to run off of a CD.  The cd includes lots of utilities.
[http://www.amazon.com/Knoppix-Hacks-Kyle-Rankin/dp/0596007876/sr=8-1/qid=1162271615/ref=pd_bbs_sr_1/102-5274284-1344129?ie=UTF8&s=books](http://www.amazon.com/Knoppix-Hacks-Kyle-Rankin/dp/0596007876/sr=8-1/qid=1162271615/ref=pd_bbs_sr_1/102-5274284-1344129?ie=UTF8&s=books)

Here is the Knoppix site:
[http://www.knoppix.net/](http://www.knoppix.net/)

Here is a post to the Knoppix forum on recovering a Windows partition:
[http://www.knoppix.net/forum/viewtopic.php?t=25729](http://www.knoppix.net/forum/viewtopic.php?t=25729)

----

You need to shutdown windows before booting into Linux.


Robert

---

### Post by steve.horsley on 2006-10-31
According to cfdisk, type 87 is "NTFS Volume set". Was Windows doing some fancy volume management?

---

