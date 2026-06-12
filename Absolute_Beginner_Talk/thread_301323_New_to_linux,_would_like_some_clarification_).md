---
title: "New to linux, would like some clarification :)"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by Miandrital on 2006-11-16
I tried a couple searches, please don't get upset if this information was easily available elsewhere. ;) 

FYI: I am currently trying to install Ubuntu edgy but I am stuck at the partitioning screen because I am confused. I already have windows XP installed on the computer, and it has 50 gb of my 80 gb allocated to it, leaving 30 gb for edgy. I want to have:

/ - 10 gb
swap - 1.5 gb (I have 1 gb RAM)
/shared - a 5gb FAT32 partition that I can use to transfer files between windows and ubuntu.
/home - whatever is left (~14 gb)

Okay, so my questions are:
1) Is the 10gb enough for the / directory?
2) Am I correct in assuming I need a fat32 partition to share between windows and linux? I know there is a program that allows sharing between NTFS and linux, but since it is in beta still I am a little weary.
3) Will the /shared automatically appear in both windows and edgy?
4) Can the /shared directory be linked to on the desktop?

Thank you very very much for your help!

---

### Post by sethmahoney on 2006-11-16
1.  Yes.
2.  Yes and no.  Ubuntu can read, but not write to, NTFS partititions.  With a little extra software, Windows can read EXT3 partitions.  So, a FAT32 partition is only really necessary if you don't want to install EXT3 support on Windows.
3.  Windows yes, Ubuntu maybe.  It depends on how you set it up.  You can make Ubuntu recognize the /shared folder if you decide to use one pretty easily though.
4.  Yes.

---

### Post by Miandrital on 2006-11-16
First off, thanks for your help.

> **sethmahoney said:**
> You can make Ubuntu recognize the /shared folder if you decide to use one pretty easily though.

How do I do that exactly?

---

### Post by mongooseman1128 on 2006-11-16
10 GB should be plenty to use as the root directory (that's the / directory), all though I would personally go as big as 15 by shrinking the windows partition by 3 GB. Second, fat32 will be exactly what you want for the sharing partition (by the way, great foresight I could've saved myself a lot of hassle if I had done that) Windows should automatically recognize the new partitions (except the swap one) and Edgy should as well. The /shared directory can easily be shorcutted to on Edgy, in fact, it should automatically give a shortcut to it on the install.

---

### Post by Buck2348 on 2006-11-17
I've had Ubuntu on my machine for less than three weeks.  I can go both ways--Windows can read and write to my /home partition, and Ubuntu can read and write to all my Windows partitions (including some that were inaccessible before I found Linux).  I found that Ubuntu can recognize and read all my Windows partitions out of the box.  To enable writing to NTFS partitions,look [here]("http://www.ubuntuforums.org/showthread.php?t=217009&highlight=write+ntfs").   To enable mounting your ext3 partition(s)as drives in Windows           look [here]("http://www.fs-driver.org/").

The first one for writing to NTFS worked first time for me with no problems.  Unfortunately I spent the better part of a day trying to disable Ubuntu's "read-only" designation before I learned that Ubuntu couldn't write to NTFS.  They call this method experimental but as I say I've had no problems with it.

The other link is to a small utility that will put an icon into your Control Panel from which you can give a drive letter to any and all Linux partitions on your drives.  It says it's for ext2 but it also works with ext3, as you'll see when you read on in the documentation.

Hope this helps.

Buck

---

### Post by jaboua on 2006-11-17
Just remember that as ext2 doesn't record things to the journal, you might bork an ext3 partition if it's mounted as ext2 before an fsck (at least that's what I've read)

Both ntfs-3g and an "ext2-ifs" or something like that has worked fine for me  though. It is also possible to use a certain "Captive NTFS" in order to access NTFS with microsofts own drivers on linux, but I never got it to work myself. Using fat32 ("vfat") might be the easiest and safest solution.

Myself I have 10GB root-partition (5.1GB used) and 1GB swap (along with 1GB of ram) I can't remember using more than 17MB of swap during normal operation, but I've experienced a couple of memory leaks and I've tested some forkbombs in the past... I also believe that when the computer hibernates (kinda like windows standby, except no power usage at all) everything is dumped to swap.

---

### Post by adamkane on 2006-11-17
New to Ubuntu = Don't start with Edgy. 

Start with Dapper, unless you enjoy dysfunction.

---

### Post by RudolfMDLT on 2006-11-17
Please go the Dapper route! That thing is solid as a rock!

---

### Post by Buck2348 on 2006-11-17
Speaking of disk space, I have Ubuntu installed on my second HD, 75 gig total.  / is in the first partition of only 4 gig because the manufacturer put a backup operating system there, now of no use.  I reduced the partition which took the rest of the drive down to 47 gig, 80%full.  The rest of the drive has my swap (1gig)  and home partitions, 22.5 gig.  My question is, What will happen when my root partition fills up?  I think I thought that the root would just hold the operating system and never grow that much, but now I understand that the system installs apps there too and leaves the /Home for me to fill up.  Will the system put out alarms when it's approaching full, and what then can I do?

BTW, my /home shows the partition containing about 7 gigabyes already.  I know I haven't put that much stuff in there.  Who knows what it is, please?

Thanks,
Buck

---

