---
title: "[SOLVED] File system check failed.  ubuntu 7.04"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by _user1_ on 2007-08-08
failed fsck--must repair manually. 

 Part of error message I get when booting ubuntu 7.04.  The partition is an ext3 file system.  I get the impression that fsck is for the ext2 file system because it tells me that I have a corrupted ext2 when i run fsck on the only hard drive i have installed.  This started after I installed ubuntu stutio to another partition so I could boot it.  I did not partition for another swap file partition--should I have? Both Ubuntu 7.04 and Ubuntu Studio use the same swap file--could this be a problem?

 Any help out there?  thanks

This is the output of the log file:

Log of fsck -C -R -A -a 
Wed Aug  8 01:30:42 2007

fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: Unable to resolve 'UUID=cca0712a-0f0e-4fc8-a749-1d2eda84a0cf'
/dev/hda4: clean, 5902/1949696 files, 337629/3893754 blocks (check in 4 mounts)
fsck died with exit status 8

Wed Aug  8 01:30:42 2007
----------------

---

### Post by AlexenderReez on 2007-08-08
> **_user1_ said:**
> failed fsck--must repair manually. 

 Part of error message I get when booting ubuntu 7.04.  The partition is an ext3 file system.  I get the impression that fsck is for the ext2 file system because it tells me that I have a corrupted ext2 when i run fsck on the only hard drive i have installed.  This started after I installed ubuntu stutio to another partition so I could boot it.  I did not partition for another swap file partition--should I have? Both Ubuntu 7.04 and Ubuntu Studio use the same swap file--could this be a problem?

 Any help out there?  thanks

This is the output of the log file:

Log of fsck -C -R -A -a 
Wed Aug  8 01:30:42 2007

fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: Unable to resolve 'UUID=cca0712a-0f0e-4fc8-a749-1d2eda84a0cf'
/dev/hda4: clean, 5902/1949696 files, 337629/3893754 blocks (check in 4 mounts)
fsck died with exit status 8

Wed Aug  8 01:30:42 2007
----------------

hm....as far as i know newer linux distribution replace usage of ext2 with ext3 and.....for linux swap....it suppose not necessary as it is just support for your RAM(random access memory)..but it may bring problem if you didn't make it ...just spend about 512mb for it....

---

### Post by _user1_ on 2007-08-08
Thanks for your response, Al.  I partitioned before i installed and qtparted used ex2 as default and I changed it to ex3.  I've been reading about the swap partition.

Still have not solved my problem, so any input is welcomed.  thanks

---

### Post by mcduck on 2007-08-08
Ext3 is just Ext2 with the addition of journalling. IF you remove the journalling or it breaks the file system becomes Ext2, and after adding journalling it's Ext3 again. So Ext2 and 3 can be pretty much handled with the same tools.

You can share swap partitions between different Linux distros. Only possible problem is if you use suspend-to-disk, and then boot another distro, as the suspend data is written to swap partition and booting another distro overwrites it.

Anyway, thereal problem here seems to be with changing partitions and not replacing the UUID's in /etc/fstab with new ones.

So, could you post here outputs of "blkid" and "cat /etc/fstab".

---

### Post by _user1_ on 2007-08-08
ubuntu@LinuxDesktop:~$ blkid
/dev/hda1: UUID="34649399-ac06-4d20-a4b7-30c1cb02f1fb" SEC_TYPE="ext2" TYPE="ext3"
/dev/hda3: UUID="407c3a3c-d4a0-48f5-99a4-c5e6ce70b822" SEC_TYPE="ext2" TYPE="ext3"
/dev/hda4: UUID="41f49f62-980d-4f74-b6c1-be51990af1f8" SEC_TYPE="ext2" YPE="ext3"
/dev/hda5: TYPE="swap" UUID="66ead936-2fd2-464f-9044-3b83b06daf2a"

ubuntu@LinuxDesktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=34649399-ac06-4d20-a4b7-30c1cb02f1fb /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=cca0712a-0f0e-4fc8-a749-1d2eda84a0cf /media/hda3     ext3    defaults        0       2
# /dev/hda4
UUID=41f49f62-980d-4f74-b6c1-be51990af1f8 /media/hda4     ext3    defaults        0       2
# /dev/hda5
UUID=66ead936-2fd2-464f-9044-3b83b06daf2a none            swap    sw              0       0/dev/hdc        

/media/cdrom0   udf,iso9660 user,noauto     0       0


ubuntu@LinuxDesktop:~$ 
ubuntu@LinuxDesktop:~$

---

### Post by _user1_ on 2007-08-08
Hi, McDuck.  I hope you're still up.  I posted the info you asked for above.  Also, I don't know if it matters or not but I created a new partition for Ubuntu Studio and it boots ok.  The original Ubuntu 7.04 is still installed and it is the one that gives me the error message.  I can do a ctrl D and it boots and appears to work ok.  thanks for your help.  I'll wait and see what you read from the info.

---

### Post by mcduck on 2007-08-08
> **_user1_ said:**
> ubuntu@LinuxDesktop:~$ blkid
/dev/hda1: UUID="34649399-ac06-4d20-a4b7-30c1cb02f1fb" SEC_TYPE="ext2" TYPE="ext3"
/dev/hda3: UUID="407c3a3c-d4a0-48f5-99a4-c5e6ce70b822" SEC_TYPE="ext2" TYPE="ext3"
/dev/hda4: UUID="41f49f62-980d-4f74-b6c1-be51990af1f8" SEC_TYPE="ext2" YPE="ext3"
/dev/hda5: TYPE="swap" UUID="66ead936-2fd2-464f-9044-3b83b06daf2a"

ubuntu@LinuxDesktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=34649399-ac06-4d20-a4b7-30c1cb02f1fb /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=cca0712a-0f0e-4fc8-a749-1d2eda84a0cf /media/hda3     ext3    defaults        0       2
# /dev/hda4
UUID=41f49f62-980d-4f74-b6c1-be51990af1f8 /media/hda4     ext3    defaults        0       2
# /dev/hda5
UUID=66ead936-2fd2-464f-9044-3b83b06daf2a none            swap    sw              0       0/dev/hdc        

/media/cdrom0   udf,iso9660 user,noauto     0       0


ubuntu@LinuxDesktop:~$ 
ubuntu@LinuxDesktop:~$
This could be your problem. The correct UUID for hda3 is here:
```
/dev/hda3: UUID="407c3a3c-d4a0-48f5-99a4-c5e6ce70b822" SEC_TYPE="ext2" TYPE="ext3"
```
..while this is what you have in your fstab:
```
# /dev/hda3
UUID=cca0712a-0f0e-4fc8-a749-1d2eda84a0cf /media/hda3     ext3    defaults        0       2
```

Run 'gksudo gedit /etc/fstab' and replace that UUID with the correct one. That should fic your problem.

Changing or formatting partitions change their UUID so afterwards fstab must be edited to use the new UUID.

edit: The new UbuntuStudio install of course works fine, as it was installed _after_ the UUID changed and so it already has the correct UUID.

---

### Post by _user1_ on 2007-08-09
Hey, Mr. mcduck!  THANKS!!!  You were right on.  I'll bet others will benefit from your generosity.  I should tell them not to use the quote marks, though.  By the way, what does the "42" mean?

thanks, again.

---

### Post by mcduck on 2007-08-09
Great that the problem was that easy to solve.

42 is the Answer to Life, Universe and Everything. I think it pretty much covers everything I could put in my signature ;) [http://en.wikipedia.org/wiki/The_Answer_to_Life%2C_the_Universe%2C_and_Everything]("http://en.wikipedia.org/wiki/The_Answer_to_Life%2C_the_Universe%2C_and_Everything")

---

### Post by _user1_ on 2007-08-09
That's interesting because i started to reply with something like "isn't knowledge wonderful" but decided against it and just thanked you instead.  If you run across a different answer to "why", let me know.  Until next time.

---

### Post by rockballad on 2007-08-10
Thanks, It works for me! Have a nice weekend!

---

### Post by bigcatsfl on 2007-08-15
Hello MCDUCK

Exact same error-  can't FSCK failed and can't find UUID for XFS

AS I understand the problem the UUID in BLKID was one thing, but another one in /etc/fstab.  Y our good solution was to correct the UUID in fstab

I have FIESTY and following MYTHTV guide, I made LVM and formatted XFS  Here is my output

BLKID:
/dev/mapper/storagevg-homeslv: UUID="181367fa-0130-4428-9265-413553bc7b2e" TYPE="xfs" 
/dev/sda1: UUID="421ffd8a-2a79-4fde-85cc-0a164151c153" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: TYPE="swap" UUID="603fb652-685f-4836-b4bb-ceb599206290" 
/dev/sdc1: UUID="813dd8b1-b561-4520-b555-d81d3685ae2c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/mapper/storagevg-recordingslv: UUID="25a0a3e1-1999-416e-888f-024501c5a7ac" TYPE="xfs" 

fstab:
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=421ffd8a-2a79-4fde-85cc-0a164151c153 /               ext3    defaults,errors=remount-ro 0       1
/dev/mapper/storagevg-homeslv /home           xfs     defaults        0       2
# /dev/sdc1
UUID=b578a6fc-53d6-49f0-8b95-9824cb6b4ab7 /media/sdc1     ext3    defaults        0       2
# /dev/sda2
UUID=603fb652-685f-4836-b4bb-ceb599206290 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
# UNCONFIGURED FSTAB FOR BASE SYSTEM
~

Regards,

Bob

---

### Post by bharkins on 2008-04-17
> **mcduck said:**
> This could be your problem. The correct UUID for hda3 is here:
```
/dev/hda3: UUID="407c3a3c-d4a0-48f5-99a4-c5e6ce70b822" SEC_TYPE="ext2" TYPE="ext3"
```
..while this is what you have in your fstab:
```
# /dev/hda3
UUID=cca0712a-0f0e-4fc8-a749-1d2eda84a0cf /media/hda3     ext3    defaults        0       2
```

Run 'gksudo gedit /etc/fstab' and replace that UUID with the correct one. That should fic your problem.

Changing or formatting partitions change their UUID so afterwards fstab must be edited to use the new UUID.

edit: The new UbuntuStudio install of course works fine, as it was installed _after_ the UUID changed and so it already has the correct UUID.

I have the file check  problem also. Here are the "blkid" and "cat /etc/fstab" -

bill@bill-laptop:~$ sudo blkid
/dev/sda1: UUID="DA54B4B054B490AD" LABEL="VISTA HOME PREMIUM" TYPE="ntfs" 
/dev/sda5: UUID="8A4CA43A4CA422C5" LABEL="DNLDSFTWR" TYPE="ntfs" 
/dev/sdb2: UUID="af23674a-98e8-4dd4-ad9d-91778e195478" SEC_TYPE="ext2" TYPE="ext3" LABEL="UBUNTU 8.04" 
/dev/sdb5: UUID="E571A7622F07C258" LABEL="DIGIMAGE" TYPE="ntfs" 
/dev/sdb6: UUID="C7A38B8E3C3418B5" LABEL="BILLDATA" TYPE="ntfs" 
/dev/sdb7: UUID="B74585890CEFF022" LABEL="SOUNDLIB" TYPE="ntfs" 
/dev/sdb8: UUID="0c01c42a-739b-489c-887d-d7fdb0ac5998" SEC_TYPE="ext2" TYPE="ext3" LABEL="UBUNTU 7.10 bare" 
bill@bill-laptop:~$

bill@bill-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=af23674a-98e8-4dd4-ad9d-91778e195478 /               ext3    errors=remount-ro 0       1
# /dev/sda1
UUID=DA54B4B054B490AD /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=8A4CA43A4CA422C5 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=a644ef74-69ca-4ef6-8d45-8ea4bf45c4c5 /media/sda6     ext3    defaults        0       2
# /dev/sdb5
UUID=E571A7622F07C258 /media/sdb5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb6
UUID=C7A38B8E3C3418B5 /media/sdb6     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb7
UUID=B74585890CEFF022 /media/sdb7     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb8
UUID=0c01c42a-739b-489c-887d-d7fdb0ac5998 /media/sdb8     ext3    defaults        0       2
# /dev/sdb9
UUID=690cabd7-f303-35d7-dacd-b3a9eb59ac19 /media/sdb9     ext3    defaults        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
bill@bill-laptop:~$ ) 

Note that in fstab, the sdb2 partition (which has the file system failure) has a "errors=remount-ro". How to correct that? Also, note that sdb9 shows an ext3 partition. This does not exist as it has been deleted from the hard drive. What are your suggestions at this point for curing the failure on the Hardy partition?

---

### Post by bharkins on 2008-04-22
> **bharkins said:**
> I have the file check  problem also. Here are the "blkid" and "cat /etc/fstab" -

bill@bill-laptop:~$ sudo blkid
/dev/sda1: UUID="DA54B4B054B490AD" LABEL="VISTA HOME PREMIUM" TYPE="ntfs" 
/dev/sda5: UUID="8A4CA43A4CA422C5" LABEL="DNLDSFTWR" TYPE="ntfs" 
/dev/sdb2: UUID="af23674a-98e8-4dd4-ad9d-91778e195478" SEC_TYPE="ext2" TYPE="ext3" LABEL="UBUNTU 8.04" 
/dev/sdb5: UUID="E571A7622F07C258" LABEL="DIGIMAGE" TYPE="ntfs" 
/dev/sdb6: UUID="C7A38B8E3C3418B5" LABEL="BILLDATA" TYPE="ntfs" 
/dev/sdb7: UUID="B74585890CEFF022" LABEL="SOUNDLIB" TYPE="ntfs" 
/dev/sdb8: UUID="0c01c42a-739b-489c-887d-d7fdb0ac5998" SEC_TYPE="ext2" TYPE="ext3" LABEL="UBUNTU 7.10 bare" 
bill@bill-laptop:~$

bill@bill-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=af23674a-98e8-4dd4-ad9d-91778e195478 /               ext3    errors=remount-ro 0       1
# /dev/sda1
UUID=DA54B4B054B490AD /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=8A4CA43A4CA422C5 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=a644ef74-69ca-4ef6-8d45-8ea4bf45c4c5 /media/sda6     ext3    defaults        0       2
# /dev/sdb5
UUID=E571A7622F07C258 /media/sdb5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb6
UUID=C7A38B8E3C3418B5 /media/sdb6     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb7
UUID=B74585890CEFF022 /media/sdb7     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb8
UUID=0c01c42a-739b-489c-887d-d7fdb0ac5998 /media/sdb8     ext3    defaults        0       2
# /dev/sdb9
UUID=690cabd7-f303-35d7-dacd-b3a9eb59ac19 /media/sdb9     ext3    defaults        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
bill@bill-laptop:~$ ) 

Note that in fstab, the sdb2 partition (which has the file system failure) has a "errors=remount-ro". How to correct that? Also, note that sdb9 shows an ext3 partition. This does not exist as it has been deleted from the hard drive. What are your suggestions at this point for curing the failure on the Hardy partition?

I also solved the file system check fail issue. After a lot of browsing, I found that the "errors remount" didn't have anything to do with the problem. It was due to wrong UUIDs which I was able to cut and paste from _blkid_the correct numbers into _fstab_. Easy once you know how!

---

