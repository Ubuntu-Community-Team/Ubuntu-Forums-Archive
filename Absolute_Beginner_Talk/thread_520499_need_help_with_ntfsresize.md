---
title: "need help with ntfsresize"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by Hopeless on 2007-08-08
hi,

i have 300gb disk and have just used ntfsresize to resize.... i read 
IMPORTANT: When recreating the partition, make sure that you
  1)  create it at the same disk sector (use sector as the unit!)
  2) [COLOR="Red"] create it with the same partition type (usually 7, HPFS/NTFS)[/COLOR]
  3)  do not make it smaller than the new NTFS filesystem size
  4)  set the bootable flag for the partition if it existed before

so i can't make it ext3? or do i do everything then use Gparted to delete the new partition the make it ext3?

its from [http://www.think-future.de/wiki/index.php?title=NTFS_resize](http://www.think-future.de/wiki/index.php?title=NTFS_resize)

thanks...

---

### Post by skymera on 2007-08-08
what is on the ntfs?
windows?

if so, i reccomend booting windows and resizing from there.

---

### Post by Hopeless on 2007-08-08
nah...

only linux...i have 2 40gb hard drives and one 300gb hard drive... the 2 40's are ext3...and i'm trying to get the 300gb to ext3... 200gb data on it...

i've just resized it and waiting...don't know what to do...

---

### Post by skymera on 2007-08-08
try gparted.
unmount the volume and resize it.
then fiddle about how u want

sudo apt-get install gparted

---

### Post by Hopeless on 2007-08-08
i got gparted...

in the tutorial i'm up to  **Actualization of Disk Layout**

can i quit there and do gparted like you said?

---

### Post by skymera on 2007-08-08
if it not doing anything to the disk.
quit use gparted.

resize it, and fill linux in the space, or whatever you want to do.

good luck

---

### Post by Hopeless on 2007-08-08
are you sure?

because i went into gparted it's all yellow and no white unused spaces like before...

---

### Post by skymera on 2007-08-08
at the top right, you select which drie to choose.
is you have multiple drives

---

### Post by Hopeless on 2007-08-08
ok i tried it and got error...on resize partition....?

---

### Post by skymera on 2007-08-08
is the drive mounted.

i think its best to do from live CD. ;)

---

### Post by Hopeless on 2007-08-08
live cd? i don't have a cd burner i have the original 7.04 install will that do?

here is the output from gparted...

GParted 0.2.5

Resize /dev/sdb1 from 279.46 GiB to 207.36 GiB    ( ERROR )
     	
check filesystem on /dev/sdb1 for errors and (if possible) fix them    ( SUCCES )
     	
ntfsresize -P -i -f -v /dev/sdb1
     	
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/sdb1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 300066402816 bytes (300067 MB)
Current device size: 300066407424 bytes (300067 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 211946 MB (70.6%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 3228 MB 0
Multi-Record : 211955 MB 4911
$MFTMirr : 150034 MB 1
Compressed : 195821 MB 4876
Ordinary : 211292 MB 5683
You might resize at 211945525248 bytes or 211946 MB (freeing 88121 MB).
Please make a test run using both the -n and -s options before real resizing!
resize the filesystem    ( SUCCES )
     	
run simulation    ( SUCCES )
     	
ntfsresize -P --force --force /dev/sdb1 -s 222641160192 --no-action
     	
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/sdb1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 300066402816 bytes (300067 MB)
Current device size: 300066407424 bytes (300067 MB)
New volume size : 222641156608 bytes (222642 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 211946 MB (70.6%)
Collecting resizing constraints ...
Needed relocations : 0 (0 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Updating $BadClust file ...
Updating $Bitmap file ...
Updating Boot record ...
The read-only test run ended successfully.
resize the filesystem    ( SUCCES )
     	
ntfsresize -P --force --force /dev/sdb1 -s 222641160192
     	
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/sdb1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 300066402816 bytes (300067 MB)
Current device size: 300066407424 bytes (300067 MB)
New volume size : 222641156608 bytes (222642 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 211946 MB (70.6%)
Collecting resizing constraints ...
Needed relocations : 0 (0 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Updating $BadClust file ...
Updating $Bitmap file ...
Updating Boot record ...
Syncing device ...
Successfully resized NTFS on device '/dev/sdb1'.
You can go on to shrink the device for example with Linux fdisk.
IMPORTANT: When recreating the partition, make sure that you
1) create it at the same disk sector (use sector as the unit!)
2) create it with the same partition type (usually 7, HPFS/NTFS)
3) do not make it smaller than the new NTFS filesystem size
4) set the bootable flag for the partition if it existed before
Otherwise you won't be able to access NTFS or can't boot from the disk!
If you make a mistake and don't have a partition table backup then you
can recover the partition table by TestDisk or Parted's rescue mode.
resize partition    ( ERROR )
     	
old start: 63
old end: 586067264
old size: 279.46 GiB
Parted can't resize partitions managed by Windows Dynamic Disk.
check filesystem on /dev/sdb1 for errors and (if possible) fix them    ( SUCCES )
     	
ntfsresize -P -i -f -v /dev/sdb1
     	
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/sdb1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 222641156608 bytes (222642 MB)
Current device size: 300066407424 bytes (300067 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 211944 MB (95.2%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 3228 MB 0
Multi-Record : 211955 MB 4911
$MFTMirr : 150034 MB 1
Compressed : 195821 MB 4876
Ordinary : 211292 MB 5683
You might resize at 211943161856 bytes or 211944 MB (freeing 10698 MB).
Please make a test run using both the -n and -s options before real resizing!
grow filesystem to fill the partition    ( SUCCES )
     	
run simulation    ( SUCCES )
     	
ntfsresize -P --force --force /dev/sdb1 --no-action
     	
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/sdb1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 222641156608 bytes (222642 MB)
Current device size: 300066407424 bytes (300067 MB)
New volume size : 300066402816 bytes (300067 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 211944 MB (95.2%)
Collecting resizing constraints ...
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Updating $BadClust file ...
Updating $Bitmap file ...
Updating Boot record ...
The read-only test run ended successfully.
grow filesystem to fill the partition    ( SUCCES )
     	
ntfsresize -P --force --force /dev/sdb1
     	
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/sdb1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 222641156608 bytes (222642 MB)
Current device size: 300066407424 bytes (300067 MB)
New volume size : 300066402816 bytes (300067 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 211944 MB (95.2%)
Collecting resizing constraints ...
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Updating $BadClust file ...
Updating $Bitmap file ...
Updating Boot record ...
Syncing device ...
Successfully resized NTFS on device '/dev/sdb1'.
check filesystem on /dev/sdb1 for errors and (if possible) fix them    ( SUCCES )
     	
ntfsresize -P -i -f -v /dev/sdb1
     	
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/sdb1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 300066402816 bytes (300067 MB)
Current device size: 300066407424 bytes (300067 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 211946 MB (70.6%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 3228 MB 0
Multi-Record : 211955 MB 4911
$MFTMirr : 150034 MB 1
Compressed : 195821 MB 4876
Ordinary : 211292 MB 5683
You might resize at 211945525248 bytes or 211946 MB (freeing 88121 MB).
Please make a test run using both the -n and -s options before real resizing!

---

### Post by Hopeless on 2007-08-08
i wanna continue with the original tutorial... i'm getting nowhere...

 Actualization of Disk Layout

[http://www.think-future.de/wiki/index.php?title=NTFS_resize](http://www.think-future.de/wiki/index.php?title=NTFS_resize)

when i delete the partition it wont delete my data right?

i'm going to give it a try...

---

### Post by Hopeless on 2007-08-08
man i lost all the resize it reset itself....

i have to start over...from scratch...

---

### Post by Hopeless on 2007-08-08
hi again...

i went to do it again and i get this error:

[COLOR="Red"]ERROR: Volume is scheduled for check.[/COLOR]
Run chkdsk /f and please try again, or see option -f.
root@Darkstar:/home/shane# chkdsk /f
bash: chkdsk: command not found

what do i do?

thanks...

---

### Post by Hopeless on 2007-08-08
do you think i can just pick up from where i left from the tutorial?

---

### Post by Hopeless on 2007-08-09
o.k. how can i mount it to see if i lost any files?

please help me...

thanks...

---

### Post by Hopeless on 2007-08-09
ok i could su to root the access the sdb1

what di i do guys? anyi deas?

---

