---
title: "messed up"
date: 2005-10-31
forum: Absolute Beginner Talk
---

### Post by bmarilena on 2005-10-31
Hi, I have a problem with ubuntu...
Had a crush, and after rebooting... the mounting points aremessed up. And the gnome is not working.
I can reinstall Breezy, but... I have some things on the HDD and don't have any clue how to access the, and save on a windows fat32 existing partition.
Can anybody help with this?

---

### Post by codejunkie on 2005-10-31
[quote=bmarilena]Hi, I have a problem with ubuntu...
Had a crush, and after rebooting... the mounting points aremessed up. And the gnome is not working.
I can reinstall Breezy, but... I have some things on the HDD and don't have any clue how to access the, and save on a windows fat32 existing partition.
Can anybody help with this?[/quote] 
if you have an ubuntu live cd handy, you can boot using the livecd then mount the harddrives and copy the data over. here's some steps that will help you do that once you have the live cd booted up open a terminal type 
```
sudo fdisk -l
```this will list your partitions, for example mine looks like this 
```
Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        4982    40017883+   c  W95 FAT32 (LBA)
/dev/hda2   *        4983        9758    38363220   83  Linux
/dev/hda3            9759        9964     1654695    5  Extended
/dev/hda5            9759        9964     1654663+  82  Linux swap / Solaris

``` first im going to mount my widows partition, the first step is create a mount point like this
```
sudo mkdir /media/windows
```then```
sudo chmod 777 /media/windows -R
```this allows all users readwrite access to the drive.

now mount the partition like this
```
sudo mount /dev/hda1 /media/windows
``` now the linux partition 
```
sudo mkdir /media/linux
``` ```
sudo chmod 777 /media/linux -R
``` ```
sudo mount /dev/hda2 /media/linux
``` now both drives are mounted. you'll need to change your drive settings accordingly for your drives but this should work just fine for you hope it helps.

---

### Post by bmarilena on 2005-10-31
:) thanks a lot.
I did this, is working, but I cannot copy the files from linux to windows dir created as you adviced.
What can I do next?

---

### Post by Mustard on 2005-10-31
your windows drive is ntfs?

-edit-

Hmm just reread the first post where you say you have a fat32 partition.  Perhaps you could paste the error message you are receiving while trying to copy the files over?

---

### Post by kalin on 2005-10-31
Another way to mount the partitions would be to use the "Disks" utility in the Administration menu.

---

### Post by bmarilena on 2005-10-31
I cannot post the message, becau se I'm running now live cd, and I have to redo everithing again... but the ideea is that I don't have the permission to write to that partition. Why... have no clue...
Thanks.... I'm looking forward to have some new ideeas how to recover the data I have there.

---

### Post by bmarilena on 2005-10-31
Here it is the error message:
Error while copying to "/media/windows".
You do not have permissions to write to this folder.

And I have only one oprion: ok.

Thanks again.

---

### Post by codejunkie on 2005-10-31
[quote=bmarilena]Here it is the error message:
Error while copying to "/media/windows".
You do not have permissions to write to this folder.

And I have only one oprion: ok.

Thanks again.[/quote]
first make sure that the drive is fat32 not ntfs then press alt+F2 and enter 
```
gksudo nautilus
``` this will open nautilus and give you root permissions this should let you copy the files over.

---

### Post by bmarilena on 2005-10-31
Tanks... seems like is working.
Thanks a lot.

---

### Post by bmarilena on 2005-10-31
I have a new problem with permissions
I had to reinstall breezy. I have the fat 21 partition mounted... and read acces, but no write.
How can I solve this problem?
Tahnks

---

### Post by paddyg on 2005-10-31
[QUOTE=bmarilena]I have a new problem with permissions
I had to reinstall breezy. I have the fat 21 partition mounted... and read acces, but no write.
How can I solve this problem?
Tahnks[/QUOTE]

have you tried adding umask=000 to the fat32 line in /ect/fstab?

---

### Post by Mustard on 2005-10-31
You could try the script at this link to automatically mount your windows drives and make the entries in fstab.

[https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions]("https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions")

---

### Post by bmarilena on 2005-11-01
[quote=paddyg]have you tried adding umask=000 to the fat32 line in /ect/fstab?[/quote]

OK< I can try but... have no ideea hot the line has to look like.
Right now is: 
/dev/hda5       /               reiserfs notail,noatime  0       1
/dev/hda2       /boot           ext2    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda6       /media/hda6     vfat    defaults        0       0
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by bmarilena on 2005-11-01
[quote=Mustard]You could try the script at this link to automatically mount your windows drives and make the entries in fstab.

[https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions]("https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions")[/quote]

I have the partition mounted... but I'll chack to see if there is any command line for permissions there.
Thanks.

---

### Post by paddyg on 2005-11-01
[QUOTE=bmarilena]OK< I can try but... have no ideea hot the line has to look like.
Right now is: 
/dev/hda5       /               reiserfs notail,noatime  0       1
/dev/hda2       /boot           ext2    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda6       /media/hda6     vfat    defaults        0       0
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0[/QUOTE]

if you want a read/write fat partition on boot-up, just have a look here:
[http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat)

otherwise (on request, i mean) you can try changing your vfat line to something like
```
/dev/hda6   /media/hda6   vfat   noauto,users,umask=000     0       0
```

---

### Post by bmarilena on 2005-11-02
[quote=paddyg]if you want a read/write fat partition on boot-up, just have a look here:
[http://ubuntuguide.org/#automountfat]("http://ubuntuguide.org/#automountfat")

otherwise (on request, i mean) you can try changing your vfat line to something like
```
/dev/hda6   /media/hda6   vfat   noauto,users,umask=000     0       0
```[/quote]

Thanks a lot!

---

