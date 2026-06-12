---
title: "please help plzz i have lost my dat"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by coolnik6 on 2008-01-17
please help me
i had  windows os
it had  drives C and d: total 60 gb
then i installed ubuntu
i choose   1st option
that resize 
it showed 38 gb  osomething
then
i went ahead with installation
now after installing
when i started my xp
my d rive is empty
i mean it say
its file system is raw
where is my whole data??????????/
C: DRIVE HAS WINDOWS XP
SOO DID UBUNTU USED MY D: DRIVE OR ITS THERE ALONG WITH MY WHOLE 45 GB DATA
?
PLZZ TELL ME WAT TO DO??

---

### Post by camnor on 2008-01-17
I need to know some things first.  When you selected resize, did you tell ubuntu to format the hdb/sda2 drive and also do you still have your ubuntu cd handy so that you can boot it up Or can you boot into Ubuntu?

---

### Post by coolnik6 on 2008-01-17
ubuntu is installed
now
i can see that during booting
it gives option which OS to boot
problem is i just went ahead with ubuntu installation
i tohught that resize thing willl take care of my datawat i remeber is it showes that new resize partition is 38 gb
 i know my D: partition is 33 full
soo i tohught it has backed my 33 gb
n will install ubuntu without formatting it
soo i went ahead n installed
but now that  d: drive is not opeinig
it say
its not formatted do  u want to ormat it now??
i said no
i m guessing maay be thats where ubuntu is italled n also i feel there is my data

plzz help me

---

### Post by camnor on 2008-01-17
so how big was your D:/ partition in the beginning, when you had just windows on your computer?

---

### Post by zipperback on 2008-01-17
If you are trying to dual boot your system, you will probably find the following link helpful.

[http://ubuntuforums.org/showthread.php?t=642627#6](http://ubuntuforums.org/showthread.php?t=642627#6)

- zipperback
:popcorn:

---

### Post by Sef on 2008-01-17
With your Live CD, open the terminal (Applications > Accessories > Terminal) and type in this code:  ```
sudo fdisk -l
``` (Small L.)   Then paste the results here.

If you think you might have written over your data, then don't use the hard drive.  There are ways of recovering some or all of it.  However, if you use your hard drive, you may overwrite the data you want to recover.

---

### Post by coolnik6 on 2008-01-17
Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       23655    11922088+   c  W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/hda2           23668      104375    40676580+   f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/hda3          104375      119149     7446127+  83  Linux
Partition 3 does not end on cylinder boundary.
/dev/hda5           23668      103674    40323150    7  HPFS/NTFS
/dev/hda6          103674      104375      353398+  82  Linux swap / Solaris
nik@nik-desktop:~$

---

### Post by coolnik6 on 2008-01-17
i have posted the outcome of command fdisk -l above
plzz help me

---

### Post by Sef on 2008-01-17
Somehow something messed up.  You need to get [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").  It can restore partitions.

---

### Post by coolnik6 on 2008-01-17
hey sef but looking at the results of FDISK -L  coomand i very much optimistic that i can get my  data by mounting hda 5  
wat u think
if i get back my data from ubuntu also its not an issue
plzz do suggest a simpler way
or can i do an uninstallation of ubuntu
soo that things get back to normal???

---

### Post by erginemr on 2008-01-17
Can you also please post your /etc/fstab file?

---

### Post by coolnik6 on 2008-01-17
i have posted the fstab file in etc directory

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=a1b67225-62e5-41f2-a858-46e076380009 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda6
UUID=da3dc3e2-64ce-481f-a4ed-28b3d57460fa none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto

---

### Post by Desperate on 2008-01-17
Hello, reading with you guys, got same kind of problem, downloaded Testdisk.tar, extracted on my memory stick next step ??? Very new to Ubuntu and trying to safe my hard disk data after XPpro crashed with no options to boot, running live cd 7.1 now, to get something done 

Thanks for your time and good luck Coolnix, I know how it feels :)

Richard

---

### Post by Paulmd on 2008-01-17
> **coolnik6 said:**
> please help me
i had  windows os
it had  drives C and d: total 60 gb
then i installed ubuntu
i choose   1st option
that resize 
it showed 38 gb  osomething
then
i went ahead with installation
now after installing
when i started my xp
my d rive is empty
i mean it say
its file system is raw
where is my whole data??????????/
C: DRIVE HAS WINDOWS XP
SOO DID UBUNTU USED MY D: DRIVE OR ITS THERE ALONG WITH MY WHOLE 45 GB DATA
?
PLZZ TELL ME WAT TO DO??

First thing's first. Your data is not irretrievable. But you must be very careful.

Best method:

step one:
remove the hard drive from your computer.

step two: 
call a professional data recovery service. 

step three:
get a part time job to pay for it.


Do it yourself method, not as good results, but cheaper.

Obtain a second hard drive with at least as much capacity as your current drive.

Make a true copy of your old hard drive onto the new one. there are various tools for doing this. one linux tool is called ddrescue. You may need a spare computer with room for two more hard drives.

Once done, there are various data recovery tools you can use on the copy, in an attempt  to recover your data. prepare for much frustration.

---

### Post by camnor on 2008-01-18
I am downloading the .tar file now to see what you need to run in order to get the program functioning.  As well coolnik6, my advice is to go to the pros if that is affordable, and to follow the suggestions that are posted in the post before mine, but if they are a) impossible to achieve due to cost or B) you aren't quite sure what he/she wants you to do, then I would give this program a try because, most of the time, when  a computer makes a drive formatted, all they do is mark the sectors as over writable, so your data is still physically there, just not accessible yet.  So what you want to do is open the terminal once you have extracted the tarball.  Then you want to change your directory to whereever the tarballs linux folder is located("cd /media/(the memory stick)/testdisk-6.8/linux/" without the quotes and with the name that your memory stick mounted with replacing (the memory stick) ) then you want to type in, and this is a command that is going to execute their script and it might be harmful, I am not sure I ran the program tried all of it features and it caused me no problems BUT it might hurt your system so be careful, "sudo ./testdisk_static" without the quotes.  It will open.  Then you want to read the documentation that they have stored in the docs folder called running_testdisk then follow the instructions and then follow the instructions for analyze. Best of luck:KS

---

### Post by camnor on 2008-01-18
desperate, I would have a look through all their documentation about disks that won't boot and such, and it should all be there

---

### Post by erginemr on 2008-01-18
I know that this will not be a direct solution to your problem, or any kind of solution for that matter. But you might at least be able to mount your windows drives from within Ubuntu (also the missing D:\ drive, which is being reported as raw data) and access the files inside. Unfortunately, this will be a looong post but anyway...

As a reminder, here is the output of your "sudo fdisk -l" command:
> **coolnik6 said:**
> Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       23655    11922088+   c  W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/hda2           23668      104375    40676580+   f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/hda3          104375      119149     7446127+  83  Linux
Partition 3 does not end on cylinder boundary.
/dev/hda5           23668      103674    40323150    7  HPFS/NTFS
/dev/hda6          103674      104375      353398+  82  Linux swap / Solaris
nik@nik-desktop:~$

and here is the contents of your "/etc/fstab" file:
> **coolnik6 said:**
> i have posted the fstab file in etc directory

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=a1b67225-62e5-41f2-a858-46e076380009 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda6
UUID=da3dc3e2-64ce-481f-a4ed-28b3d57460fa none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto

As a comparison, here is a standard /etc/fstab file with lines for auto-mounting an ntfs drive and a vfat (fat32) drive:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=2cd4fd47-f5e2-4512-92c9-fb402e3a214e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda8
UUID=c0b2f548-e488-49cf-9f29-2714f455b3a8 /home           ext3    defaults        0       2
# /dev/hda1
UUID=60E0E51CE0E4F8E4 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda5
UUID=D8D3-0820  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda7
UUID=66700d1c-d4e9-4f39-ab0f-a1191794251d none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

Normally, the line mounting ntfs used to be:
```
/dev/hda1 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
```
and the line mounting fat32 used to be:
```
# /dev/hda5
UUID=D8D3-0820  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
```

But as a result of the recent developments in Linux, the use of UUID, a new way to identify hard drives has been gaining more ground in recent distros. So, the parts
```
# /dev/hda1
# /dev/hda5
```
have been commented out by Ubuntu installer and the UUID of the corresponding hard drives have been implemented instead:
```
UUID=60E0E51CE0E4F8E4 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda5
UUID=D8D3-0820  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
```
You can obtain the UUID's for your ntfs and fat32 hard drives with either:
```
sudo blkid
```
or
```
sudo vol_id -u /dev/hda1
sudo vol_id -u /dev/hda2
sudo vol_id -u /dev/hda5
```

From the outcome of "sudo fdisk -l", it appears that your fat32 partitions are located in "dev/hda1" and "/dev/hda2", and your ntfs partition is located in "/dev/hda5". Speaking of which, this also means that you only have one hard drive, though divided into two by Windows as C:\ and D:\.

Hence, in your case, you should add the following lines to your /etc/fstab file:

```

UUID=................ /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
UUID=................ /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1
UUID=................ /media/hda5     ntfs    defaults,umask=007,gid=46 0       1
```

Make sure that /media/hda1, hda2 and hda5 as a directory pre-exist in your file system and use the result of one of the above two commands to insert UUID of /dev/hdaX. Reboot and see if there is any  improvement.

But the error message as a result of "sudo fdisk -l" is ominous enough: "Partition 1 does not end on cylinder boundary."
And as far as I know, points to a problem in your partition table. In this respect, I suggest you to sef's advice first, and use "testdisk" to repair your partition table.

---

### Post by erginemr on 2008-01-18
Also follow this thread:
[http://ubuntuforums.org/showthread.php?t=336900](http://ubuntuforums.org/showthread.php?t=336900)

where the use of GParted Live CD has been suggested as a secondary alternative to testdisk (but I would approach GParted to fix an NTFS drive with caution and use it as a last resort). By the way, testdisk is version independent and you can install and run it from both Ubuntu and Windows.

---

