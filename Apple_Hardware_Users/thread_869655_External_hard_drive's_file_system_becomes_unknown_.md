---
title: "External hard drive's file system becomes unknown in Gparted...please help"
date: 2008-07-25
forum: Apple Hardware Users
---

### Post by amarkitanis on 2008-07-25
I have a Seagate Freeagent pro external hard drive whose filesystem is HFS extended(HFS+) journaled. I  had it assosicated with time machine and was using it as an external hard drive just fine.

I have been able to use that hard disk under Windows, using Macdrive with no problems. Mounting in mac os x after having read/written in windows was not a problem.

After having installed linux, I read several threads/comments that HFS+ works in linux for both reading and writing.

And this is where my problem/question comes along. 

Is it the case that when you use a hard disk in linux, for both reading and writing,  whose filysystem is HFS+ **_JOURNALED_**, that hard disk's filesystem becomes corrupted/damaged under mac os x?

Mounting the same disk in Ubuntu 8.04/Windows Vista works fine, being able to both read and write but when it comes to mac os x leopard 10.5.4, the hard disk does not mount. Disk utility recognises the hard disk but is not able to fix it or mount it. According to disk utility(mac os x), the filesystem shows as  FAT 32, and it's given a default name of smth similar to disk2s. 

According to gparted on Ubuntu 8.04, the filesystem shows as Unknown file system.
As I'm not too sure if what i read is consistent, it appears that reading and writing in linux is successful when journaling is disabled. 
I had no clue about this. Why did it let me write since the hard disk was journaled?
Should I knew about this I would first disable journaling.

is there anyway i could 'bring it back to life' under mac os x
as a 1TB hard disk is hard to back up?

Additionally, if there's no option but to back up everything under Windows/Linux, 
what do i need to do so this does not happen again? Format the hard disk as HFS Extended **_NON-JOURNALED_**?

Any suggestions anyone?

Thanks for your time.

---

### Post by cyberdork33 on 2008-07-25
From other thread:
> **amarkitanis said:**
> if you have an HFS+ journaled external hard disk and you read/write files in Ubuntu, does that hard disk become corrupted under mac os x?
 
 I've been using my external hard disk (HFS+ journaled) both on linux, and windows (using MacDrive) both reading and writing. 
 
 I haven't had used the extenal disk with mac for a while. 
 
 Doing this today, the hard disk does not mount, and under disk utility it says that the file system is fat 32 and it cannot be mounted nor repaired. 
 Linux and Windows Vista can read files and write to the hard disk perfectly fine. 
 
 Gparted recognises the disk and says that its filesystem is  unknown. 
 Well, for one thing, you cannot possibly have journaling turned on, and be able to write from Linux... it isn't possible. As for corruption, it is quite possible (journaling or not). If gparted doesn't even recognize it, then it sounds like there is definitely something wrong... Might be time for a backup and reformat.

In OSX, try running 'fsck -yf /dev/diskXsX' on the partition and see what the output is.

---

### Post by amarkitanis on 2008-07-25
** /dev/rdisk1s2
BAD SUPER BLOCK: MAGIC NUMBER WRONG

LOOK FOR ALTERNATE SUPERBLOCKS? yes

SEARCH FOR ALTERNATE SUPER-BLOCK FAILED. YOU MUST USE THE
-b OPTION TO FSCK TO SPECIFY THE LOCATION OF AN ALTERNATE
SUPER-BLOCK TO SUPPLY NEEDED INFORMATION; SEE fsck(8 ).

---

### Post by cyberdork33 on 2008-07-25
> **amarkitanis said:**
> ** /dev/rdisk1s2
BAD SUPER BLOCK: MAGIC NUMBER WRONG

LOOK FOR ALTERNATE SUPERBLOCKS? yes

SEARCH FOR ALTERNATE SUPER-BLOCK FAILED. YOU MUST USE THE
-b OPTION TO FSCK TO SPECIFY THE LOCATION OF AN ALTERNATE
SUPER-BLOCK TO SUPPLY NEEDED INFORMATION; SEE fsck(8 ).
yea that is bad. I had errors like that on my main OSX partition and could not get it fixed until I used diskwarrior... There may be a way to reapir it, but it is beyond my understanding... Maybe they can help in the Apple support area (it is their filesystem, and they might better know what the error means.)

---

### Post by amarkitanis on 2008-07-25
errm the command is actualy fsck_hfs under mac os x

---

### Post by cyberdork33 on 2008-07-25
> **amarkitanis said:**
> errm the command is actualy fsck_hfs under mac os x
That works too. Boot into safe mode and it tells you the commands to use.

---

