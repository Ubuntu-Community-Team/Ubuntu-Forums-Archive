---
title: "mounting a parttion"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by klein de usa on 2007-04-16
hi
i have used gparted to create 6 parttions now i would like to mount one of them and not sure how to go about it , is there a flag in gparted i can set to have edgy mount /dev/hda5 ? i want to use hda5 for storage and have formated it ext3 

/dev/hda1     ntfs
/dev/hda2     ext3 ubuntu edgy
/dev/hda3     swp
/dev/hda4     extended
         /dev/hda5     ext3  
         /dev/hda6     fat32

---

### Post by taurus on 2007-04-16
Here's a link for you.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by klein de usa on 2007-04-16
hi
it is telling me :

mount: special device /dev/disk/by-uuid/E0DCCBFADCCBC94C does not exist

i went by [http://www.psychocats.net/ubuntu/mountlinux]("http://www.psychocats.net/ubuntu/mountlinux")
i can't pick out what i did wrong?

klein@ubuntu3000:~$ sudo fdisk -l
Password:

Disk /dev/hda: 200.0 GB, 200000000000 bytes
255 heads, 63 sectors/track, 24315 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        5099    40957686    7  HPFS/NTFS
/dev/hda2   *        5100       11178    48829567+  83  Linux
/dev/hda3           11179       11300      979965   82  Linux swap / Solaris
/dev/hda4           11301       24315   104542987+   5  Extended
/dev/hda5           11301       17807    52267446   83  Linux
/dev/hda6           17808       24315    52275478+   b  W95 FAT32
klein@ubuntu3000:~$ sudo nano /etc/fstab
klein@ubuntu3000:~$ sudo mount -a
mount: special device /dev/disk/by-uuid/E0DCCBFADCCBC94C does not exist
klein@ubuntu3000:~$ 




# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=7b8fe13b-4868-43dd-a771-7e431e6fa251 /               ext3    defaults,erro$
# /dev/hda1
UUID=E0DCCBFADCCBC94C /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=4$
# /dev/hda3
UUID=762e1162-20ae-4d8d-8d68-6ce4398f18c6 none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/hda5 /storage ext3 defaults 0 0

---

### Post by taurus on 2007-04-16
Replace

```
UUID=E0DCCBFADCCBC94C
```
with

```
/dev/hda1
```
in /etc/fstab.

p.s.  Otherwise, try the lower case letters.

---

### Post by klein de usa on 2007-04-16
ok
i'm confused i'm trying to mount /dev/hda5 in ubuntu , why would i change the ntfs/xp partion witch is /dev/hda1 ?
i'm trying to understand, psychocats tells me to find the parttion i want to mount witch is /dev/hda5.
then: sudo mkdir /storage
then it tells me to edit fstab witch i did ,by adding:
 /dev/hda5 /storage ext3 defaults 0 0
to the end of fstab and saved it then run this:
sudo mount -a
witch i do then it gives me this :
mount: special device /dev/disk/by-uuid/E0DCCBFADCCBC94C does not exist
like i said confused where does the uuid come from ?

---

### Post by brennydoogles on 2007-04-16
> **klein de usa said:**
> hi
it is telling me :

mount: special device /dev/disk/by-uuid/E0DCCBFADCCBC94C does not exist

i went by [http://www.psychocats.net/ubuntu/mountlinux]("http://www.psychocats.net/ubuntu/mountlinux")
i can't pick out what i did wrong?

klein@ubuntu3000:~$ sudo fdisk -l
Password:

Disk /dev/hda: 200.0 GB, 200000000000 bytes
255 heads, 63 sectors/track, 24315 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        5099    40957686    7  HPFS/NTFS
/dev/hda2   *        5100       11178    48829567+  83  Linux
/dev/hda3           11179       11300      979965   82  Linux swap / Solaris
/dev/hda4           11301       24315   104542987+   5  Extended
/dev/hda5           11301       17807    52267446   83  Linux
/dev/hda6           17808       24315    52275478+   b  W95 FAT32
klein@ubuntu3000:~$ sudo nano /etc/fstab
klein@ubuntu3000:~$ sudo mount -a
mount: special device /dev/disk/by-uuid/E0DCCBFADCCBC94C does not exist
klein@ubuntu3000:~$ 




# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=7b8fe13b-4868-43dd-a771-7e431e6fa251 /               ext3    defaults,erro$
# /dev/hda1
UUID=E0DCCBFADCCBC94C /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=4$
# /dev/hda3
UUID=762e1162-20ae-4d8d-8d68-6ce4398f18c6 none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/hda5 /storage ext3 defaults 0 0

It looks like you have hda5 mounted in the folder /storage ... am I correct?? If that is true, you most likely do not have permission to access that folder for write or execute purposes. There are two ways you can handle this. The first is to open up a terminal and type 
```
sudo chown YOURUSERNAME /storage
```
replacing the all caps with your username. This would change the ownership of that directory to you. A better solution I would think, would be to create a directory in your home folder called storage, and change your fstab to read 
```
/dev/hda5 /home/YOURUSERNAME/storage ext3 defaults 0 0
```

once again changing the YOURUSERNAME to be your actual username. restart X (Ctrl+Alt+Backspace), and then your storage partition will be mounted in your home directory as a folder called storage.

---

### Post by klein de usa on 2007-04-16
ok
i created a file /home/klein/storage and replaced the last line of my fstab file with :
/dev/hda5 /home/klein:klein/storage ext3 defaults 0 0
and in Nautilus the file is there but it is locked, permission is root how can i change permission so it is unlocked ?

---

### Post by klein de usa on 2007-04-16
ok
i have it now , 
sudo chown -R klein:klein  /home/klein/storage
sudo chmod -R 755 /home/klein/storage

now that worked, thanks for all the help

---

