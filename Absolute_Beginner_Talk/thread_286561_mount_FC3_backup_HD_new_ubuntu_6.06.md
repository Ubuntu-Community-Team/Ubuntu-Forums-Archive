---
title: "mount FC3 backup HD new ubuntu 6.06"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by padeco on 2006-10-27
hi there,
i have recently installed ubuntu 6.06. no major complications so far. i was able to mount the ntfs windows partition with no worries. however, i used fc3 and had a HD (120G) which was used solely for the purpose of back up drive.

the ubuntu system does "see" the dirve, however, it is inaccessible. i tried to enable it, no luck. i tried to use gparted, it also determined the presence of the HD (/dev/hdb1/   ext3) but, no access. tried to mount it (sudo mount -t ext3 /dev/hdb1 /mnt/disk2) so, if any one could share any light on this issue it would be great! i seriously need to access these files.

thanks,
padeco

---

### Post by ReaderRat on 2006-10-27
Don't know if this will help:
[**Mount Ubuntu Partition**](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by padeco on 2006-10-27
thanks for the link, i tried and this is the output i got.
from the gparted-> /dev/hdb1 <!> ext3 --- --- boot

$ sudo cp /etc/fstab /etc/fstab_backup
:/$ sudo nano /etc/fstab
:/$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
any ideas?
thanks,
padeco

---

### Post by padeco on 2006-10-28
this is some more infor i got:

/$ dmesg | tail
[17252498.096000] hdb: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
[17252498.096000] hdb: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=79, high=0, low=79, sector=79
[17252498.096000] ide: failed opcode was: unknown
[17252498.096000] end_request: I/O error, dev hdb, sector 79
[17252498.096000] EXT3-fs: can't read group descriptor 1
[17254351.832000] hdb: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
[17254351.832000] hdb: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=79, high=0, low=79, sector=79
[17254351.832000] ide: failed opcode was: unknown
[17254351.832000] end_request: I/O error, dev hdb, sector 79
[17254351.832000] EXT3-fs: can't read group descriptor 1
:/$

---

### Post by handy on 2006-10-28
> **padeco said:**
> hi there,
i have recently installed ubuntu 6.06. no major complications so far. i was able to mount the ntfs windows partition with no worries. however, i used fc3 and had a HD (120G) which was used solely for the purpose of back up drive.

the ubuntu system does "see" the dirve, however, it is inaccessible. i tried to enable it, no luck. i tried to use gparted, it also determined the presence of the HD (/dev/hdb1/   ext3) but, no access. tried to mount it (sudo mount -t ext3 /dev/hdb1 /mnt/disk2) so, if any one could share any light on this issue it would be great! i seriously need to access these files.

thanks,
padeco

Ubuntu uses **/media** where you have used **/mnt**.

If you haven't already, create a directory:

**sudo mkdir /media/disk2** 

Then:

**sudo mount -t ext3 /dev/hdb1 /media/disk2**

That should mount your drive.

If so then modify  your **/etc/fstab** remembering that Ubuntu is a bit different.

**/dev/hdb1 /media/disk2 ext3 defaults 0 2**

I certainly hope that the above is some help to you?

All the best... :)

**[Edit:]** *If you can mount your drive & not access the files, then that's a permissions problem.*

---

### Post by padeco on 2006-10-28
> **handy said:**
> Ubuntu uses **/media** where you have used **/mnt**.

If you haven't already, create a directory:

**sudo mkdir /media/disk2** 

Then:

**sudo mount -t ext3 /dev/hdb1 /media/disk2**

That should mount your drive.

If so then modify  your **/etc/fstab** remembering that Ubuntu is a bit different.

**/dev/hdb1 /media/disk2 ext3 defaults 0 2**

I certainly hope that the above is some help to you?

All the best... :)

**[Edit:]** *If you can mount your drive & not access the files, then that's a permissions problem.*

tried that, and this is what happened. any idea?

/$ sudo mount -t ext3 /dev/hdb1 /media/disk2
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by padeco on 2006-10-28
could the fact that my hda2 (linux partition) has ext3 as file type, affect the mounting of the dev/hdb1 since it also has ext3, id 83 linux?

---

### Post by handy on 2006-10-28
I've been reading up on the **mount** command:

**man 8 mount**

Are you sure that the troublesome drive is in fact **ext3** & not **ext2**?

---

### Post by handy on 2006-10-28
> **padeco said:**
> could the fact that my hda2 (linux partition) has ext3 as file type, affect the mounting of the dev/hdb1 since it also has ext3, id 83 linux?

No, that won't happen.

---

### Post by handy on 2006-10-28
Have a look at:  **man  e2fsck 8**

If you enter the following in the **Terminal**, it works on both **ext2** & **ext3** file systems, repairing all that is safe to do without human intervention. The drive should **NOT** be mounted before running the command:


**e2fsck -p /dev/hdb1**

---

### Post by padeco on 2006-10-28
> **handy said:**
> Have a look at:  **man  e2fsck 8**

If you enter the following in the **Terminal**, it works on both **ext2** & **ext3** file systems, repairing all that is safe to do without human intervention. The drive should **NOT** be mounted before running the command:


**e2fsck -p /dev/hdb1**


this is the outcome! does it  make any sense.

/$ sudo e2fsck -p /dev/hdb1
e2fsck 1.38 (30-Jun-2005)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/hdb1
Could this be a zero-length partition?

---

### Post by handy on 2006-10-28
I must ask was this drive ever a boot drive?  

Did it ever have a **boot-manager** like **Grub** or the like on it?

---

### Post by padeco on 2006-10-28
hi handy,

i am not sure with regards to the boot drive. i do not think so, since i had the fc3 booting from the windows partition drive. this drive was only used for back up. or an extended drive since i needed more space.

i'll continue trying since i a most worried about recovering what is in that hd. 

thanks,
padeco

---

### Post by handy on 2006-10-29
I think finding the correct parameters to use with **e2fsck** would be an advantage.  

I would like to see some help from a linux guru about now? :)

---

### Post by padeco on 2006-10-30
hi there,
this is just an update to let you guys know that the problem was fixed. it was an error related to damaged superblock on the hdb1. so, i had to follow the steps from [http://www.brunolinux.com/04-The_File_System/Damaged_Superblock.html](http://www.brunolinux.com/04-The_File_System/Damaged_Superblock.html) (very nice site for beginners on linux).

after a long and tortuous many long hours and late nights the issue is solved. now ubuntu loads in no time, access to hdb1 is done in a flash. once again, thank you all for the time and information given, every one was of assistance and helped in some way.

thanks,
padeco

---

