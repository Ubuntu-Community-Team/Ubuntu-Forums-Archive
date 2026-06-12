---
title: "Mounting Extended FAT32 Partition"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Kemik88 on 2007-01-24
Hello all,

I have dual booted my computer with Windows XP & Ubuntu. In the process I created an extended FAT32 drive. It shows up in Windows XP but not in Ubuntu.

> Disk /dev/sda: 200.0 GB, 200048565760 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15198   122077903+   7  HPFS/NTFS
/dev/sda2           15199       21771    52797622+  83  Linux
/dev/sda3           21772       24321    20482875    5  Extended
/dev/sda5           21772       22536     6144831   82  Linux swap / Solaris
/dev/sda6           22537       24321    14337981    b  W95 FAT32

Disk /dev/sdb: 200.0 GB, 200048565760 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401    7  HPFS/NTFS

**Contents of /etc/fstab:**

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=846e325f-e80e-4bf7-9ba8-fdb1c1b63f51 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=42E00FF5E00FEDCB /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=C4B47F0BB47EFF6C /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=45B2-36DF  /osshare        vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=49d36bac-ebcc-4c99-b94f-64c7958c09f6 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0


What do I need to edit for the FAT32 parition to show in Ubuntu? Also, can I rename some of the desktop links to the drives? So, instead of it saying sda1 it says "Windows Drive".

Thanks for your help.

---

### Post by dannyboy79 on 2007-01-24
if you're talking about renaming /media/sda1 that for example, NO, you can't. that's basically the mount point (folder more or less) for that particular partition. You need to add an entry for your fat32 partition so that ubuntu knows where to mount it! what partition is it? is it the sda6? if so than it should already be mounted to the osshare folder! did you create that folder on your system yet? what does the terminal return if you type in 
dmesg | grep sda
paste the all the results after you enter this into the terminal. I can help from there.

---

### Post by Nightmist on 2007-01-24
Try this when you're dealing with mounting:
[http://pysdm.sourceforge.net/](http://pysdm.sourceforge.net/)

---

### Post by dannyboy79 on 2007-01-24
you could do this but if you want to LEARN linux, some manual editing of system files is a great lesson. you'll get some exposure to sudo, the fstab file and how it looks and works. 
helpful places and things to read include using the man pages.
man mount
man fstab

are both a must for beginers to read if they want to UNDERSTAND what they are doing and not just take someones word for it. I just started linux back in March of 2006 and I have learned so much it's insane!

---

### Post by Kemik88 on 2007-01-24
[17179569.184000] Kernel command line: root=/dev/sda2 ro quiet splash
[17179574.856000] SCSI device sda: 390719855 512-byte hdwr sectors (200049 MB)
[17179574.856000] sda: Write Protect is off
[17179574.856000] sda: Mode Sense: 00 3a 00 00
[17179574.856000] SCSI device sda: drive cache: write back
[17179574.856000] SCSI device sda: 390719855 512-byte hdwr sectors (200049 MB)
[17179574.856000] sda: Write Protect is off
[17179574.856000] sda: Mode Sense: 00 3a 00 00
[17179574.856000] SCSI device sda: drive cache: write back
[17179574.856000]  sda: sda1 sda2 sda3 < sda5 sda6 >
[17179574.896000] sd 0:0:0:0: Attached scsi disk sda
[17179587.440000] EXT3 FS on sda2, internal journal

---

### Post by dannyboy79 on 2007-01-24
you should have also answered my question; did you create that folder on your system yet? (/osshare) your dmesg output looks ok. what is the output of df -h also. oh, i see now, you want to rename the desktop link, that I am not sure about since the system puts them there when your system boots correct? one thing you could try is to first do
sudo umount /dev/sda6, and see if it unmounts. if it does, then do sudo gedit /etc/fstab
then comment out the line that reads: UUID=45B2-36DF /osshare vfat defaults,utf8,umask=007,gid=46 0 1

and make it this:
/dev/sda6 /osshare vfat defaults,utf8,umask=007,gid=46 0 1


so you would have now
#UUID=45B2-36DF /osshare vfat defaults,utf8,umask=007,gid=46 0 1
/dev/sda6 /osshare vfat defaults,utf8,umask=007,gid=46 0 1

this is just a thought, maybe the UUID got mixed up somehow.

---

### Post by Kemik88 on 2007-01-24
df -h gives:

> 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              50G  3.5G   44G   8% /
varrun               1014M   80K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
procbususb             10M  172K  9.9M   2% /proc/bus/usb
udev                   10M  172K  9.9M   2% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   18M  997M   2% /lib/modules/2.6.17-10-generic/volatile
/dev/sda1             112G   62G   51G  56% /media/sda1
/dev/sdb1             187G   82G  105G  44% /media/sdb1
/dev/hda              7.6G  7.6G     0 100% /media/cdrom0


I used [this]("http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/") tutorial to do the dual boot. It told me to:

> 
Start by making a mount point for the OS Share partition:
mkdir /mnt/osshare
Then, mount the partition:
mount -t msdos /dev/hda6 /mnt/osshare
If you're not sure which device (e.g., /dev/hda6) your OS Share partition is, you can use QTParted to see the device number. Finally, we'll create a file that Windows can use to boot Linux:
dd if=/dev/hda2 of=/mnt/osshare/ubuntu.bin bs=512 count=1 

I followed the tutorial all the way through so I'm pretty sure I done what it said.

I hope that helps you to help me :P

I tried umount /dev/sda6 but it was still showung up on the list for fdisk -l. Do you want me to go ahead and edit that fstab and replace the line?

Sean.

---

### Post by dannyboy79 on 2007-01-25
sudo fdisk -l shows all your hard drives whether they are mounted or not! i see your problem, you put /osshare in your fstab but hte instructions told you to create /mnt/osshare. so which folder did you create???? do you have a folder in /mnt/ named osshare or is the osshare in the / folder? basically you need to update your fstab if you create a folder in /mnt/ or you have to create the folder /osshare if you want to leave your fstab alone. Get it? if not let me know what you need help with.

post the results of ls -l /
and then ls -l /mnt/

i think this is the code, if that doesn't work than first "cd" to the / directory, then do ls -l
and then "cd" to the /mnt/ directory, then do ls -l.
this will tell us what foldfers you have in each of the locations. or you could just use nautlius I suppose. i just like using the command line so I can learn.

---

### Post by Kemik88 on 2007-01-27
Ahh, sorry I've been stupid. As I'm coming from a Windows background I presumed that the FAT32 drive would be shown as a seperate drive in Ubuntu, but I see the osshare folder with the files I put on the FAT32 drive under "File System".

I apologise.

---

### Post by dannyboy79 on 2007-01-27
i don't know what you are saying but yes, linux doesn't have drive letters! so what you have a partition, this is where the "data" is. then you simply tell linux "where" to put the data. these are called mount points. mount points are simply folders.

---

