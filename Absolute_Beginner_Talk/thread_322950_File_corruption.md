---
title: "File corruption"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by jhhoward on 2006-12-21
I have a copy of Ubuntu 6.10 Edgy eft installed on my laptop with a dual boot to Windows XP. For this reason, I store my documents on a seperate FAT32 partition which can be accessed by both operating systems. I booted Ubuntu today which informed me that my FAT drive had been mounted 30 times without checking and then started checking for errors. It had almost finished checking when it told me that I had 5 errors on the drive which were being fixed. I then went to access my documents on the FAT drive and found them missing. In their place are several rec files (fsck00??.rec) which appear to be my missing files but I cannot be too certain. Is there a utility to fix this problem or have I lost my documents for good?

Thanks,
James

---

### Post by taurus on 2006-12-21
You do not need to run check disk for FAT32.  You need to modify your /etc/fstab and change the last value from 1 to 0 for your "vfat" entry!!!

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```

---

### Post by jhhoward on 2006-12-21
Sorry, maybe I wasn't clear the first time around

I don't have any problem mounting the drive, or viewing any of the files. It is the content itself that has become corrupt. I made symbolic links from my home directory to certain directories on my FAT drive named "Projects" and "Work". The links are now broken as the folders no longer exist. There are however a bunch of .rec files at the top level. Some are zipped files, and others are incomprehendable

James

---

### Post by steve.horsley on 2006-12-21
I believe the .rec files are the results of fsck's best efforts to recover damaged files. You will have to examine them by hand to decide what they were and if they are still of any use or value.

As taurus said, it is probably worth changing your fstab so that it won't run fsck on that partition again. It may be that fsck has done more damage than good. It may be that the files were already badly corrupted by earlier problems - I don't know how to tell the difference.

---

### Post by rykel on 2007-02-13
Hey guys,

I faced the same frustrating problem too... it also happened on a FAT32 partition after one reboot, which ended up with "truncating filename XXX" and other cryptic messages.

Now, the drive is in a mess, and hundreds of fsck00XX.rec files litter the place.

I would like to be informed if there is a Linux program that can restore the files to their original state, instead of going through them one by one.

btw, the files were NOT corrupted beforehand.

---

### Post by dannyboy79 on 2007-02-13
well, according to here, [http://www.linuxquestions.org/questions//showthread.php?t=515691](http://www.linuxquestions.org/questions//showthread.php?t=515691)
if you know what the files are, you can attempt to rename with there correct extension (.zip or .xls or .jpg) but if you have a mix of files it sounds like you may be out of luck. it's a shame that you didn't have your fat32 fstab entry on 0 when you created it as this is how I have seen it in every tut for mounting fat32 drives. do you know why or how you had a 1 or 2 for your fat32 drive?

the other thing I would suggest is look for a fsck log, this may give you info regarding what files it renamed and to what!!!!!!

---

### Post by rykel on 2007-02-14
> **dannyboy79 said:**
> well, according to here, [http://www.linuxquestions.org/questions//showthread.php?t=515691](http://www.linuxquestions.org/questions//showthread.php?t=515691)
if you know what the files are, you can attempt to rename with there correct extension (.zip or .xls or .jpg) but if you have a mix of files it sounds like you may be out of luck. it's a shame that you didn't have your fat32 fstab entry on 0 when you created it as this is how I have seen it in every tut for mounting fat32 drives. do you know why or how you had a 1 or 2 for your fat32 drive?

the other thing I would suggest is look for a fsck log, this may give you info regarding what files it renamed and to what!!!!!!

Hi,

It was set up as a "0" by Ubuntu default installation, I believe. (Dapper)

Anyway, I changed it to "0" a while ago, the the FAT32 drive became Read-Only, so now I have set it back to "1".

However, this means that the fsck00XXX.rec problem will potentially come back anytime again, right?

Finally, where can I find a fsck log? I cannot get it through the Search For Files function. (Find: "*fsck*" - no log files found, only binaries and other stuff...)

---

### Post by dannyboy79 on 2007-02-14
NO, you want it to be 0, this means that fsck will never force a check on the partition. you can read all about it by reading the man pages. type man fsck and man fstab within a terminal. according to man fstab, any filesystem other than your root partition should contain a 2 or a 0.

per this:
 The  sixth  field,  (fs_passno), is used by the fsck(8) program to determine the order in which filesystem checks are
       done at reboot time.  The root filesystem should be specified with a fs_passno of 1,  and  other  filesystems  should
       have  a fs_passno of 2.  Filesystems within a drive will be checked sequentially, but filesystems on different drives
       will be checked at the same time to utilize parallelism available in the hardware.  If the sixth field is not present
       or zero, a value of zero is returned and fsck will assume that the filesystem does not need to be checked.

it states that other partitions should contain a 2 but that's if you want fsck to check it once in awhile. but I would only trust it to fix ext3 since we're trusting it to fix our root partition, than why not trust it with other partitions but it does state that other partitions shall have a 2. otherwise, any partition you don't want checked every 30 boots, you need to make it a 0, zero! also I can't seem to find that the fsck program creates any log file which sucks cause it would be nice to know what fsck does if it does encounter fs errors.

---

### Post by rykel on 2007-03-24
Hi, I got another bunch of those irritating "rec" files again a while ago today, and in frustration, I set the option in fstab to "0", expecting a Read Only FAT32 partition.

However, miracles of all miracles, the FAT32 partition is now Read and Write, and no problem has arisen so far.

Then again... good things move on... I plan to format the partition into ext3, since it is primarily a data partition.

Will you recommend AGAINST using ext3 for my data storage partition?

---

### Post by dannyboy79 on 2007-03-26
you obviously misunderstand what the option is for, 0, 1 or 2 does not make it read only or writeable! that is merely for whether or not FSCK is going to check it every 30 days or not. glad you're good to go now!

---

### Post by rykel on 2007-03-26
> **dannyboy79 said:**
> you obviously misunderstand what the option is for, 0, 1 or 2 does not make it read only or writeable! that is merely for whether or not FSCK is going to check it every 30 days or not. glad you're good to go now!

Just a clarification... I know that 0 and 1 refers to DISABLE and ENABLE dosfsck checking respectively... however, the last time I disabled it, my FAT32 partition became Read Only.

btw, what does 2 do?

Thanks for a great response!!   :guitar:

---

