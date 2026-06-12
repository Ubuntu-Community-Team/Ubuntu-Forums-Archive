---
title: "File permissions problems"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by serendipity576 on 2007-03-18
Ok I've searched for the answer for a while now to no avail.  I'm confused on why, after logging into Ubuntu, I can't change anything I want.  2 issues:

1.  Some parts of my /root  folder have a red symbol above the folders and when I try to open them it says *You do not have the permissions necessary to view the contents of ".Trash".*   How do I set it permanently to where I can change anything I want and view anything I want.  

2.  I have a mounted partition named /media/sda5 which is in FAT32 accesible by both Windows and Linux.  However if I try to add new files to the contents of this folder it says I do not have write permissions and the boxes to check under properties are greyed out, not avaliable.  :confused: 

My aim is to permanently change all this so I can always have access to read and write, view these two things.  Thanks for any help with this.

Clay

---

### Post by taurus on 2007-03-18
1.  You need to be root to view anything in /root. So, use sudo/gksudo from a terminal.

Applications -> Accessories -> Terminal
```
gksudo nautilus
```
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

2.  It depends how you mount it.  Did you mount it by hand or did you mount it through /etc/fstab?  What does your /etc/fstab look like?

```
cat /etc/fstab
```

---

### Post by serendipity576 on 2007-03-18
Ok,
   When I used nautilus this is the output:

[I](nautilus:9721): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
[/I]
It DID open up the /root window however only the "Desktop" folder was showing.

2.  Here is the output from the fstab:
[I]clay@Clay:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1/dev/sda5       /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/sda2       /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/sda6       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
clay@Clay:~$[/I]


Thanks for any further help!

---

### Post by taurus on 2007-03-18
Navigate around in nautilus.

Are you sure /dev/sda5 is vfat because you have mounted it as ntfs?  What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by annda on 2007-03-18
1) all parts of /root should have those red symbols. for security reasons users have full access only to their own files (/home/username directory) - this comes from the unix/linux tradition before *nix desktop computers where lots of users has access to one machine. why do you even use the root folder/account? you can do anything using sudo. BUT you can change all permissions using this guide:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) (BAD idea for root, it's similar to leaving all windows and doors open at your house, since root can do anything).

2) sudo chmod -R 777 /media/sda5
if you read the guide i linked above (highly recommended, do some tests on your files and directories to become comfortable with permissions), this means: grant read+write+execute priviledges to anyone who wants to access that drive and all subdirectories.

EDIT: sooo slooow again today...

---

### Post by serendipity576 on 2007-03-18
Hmm...ok here's the output from fdisk -l   

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8        2557    20482875    7  HPFS/NTFS
/dev/sda3            2558        3590     8297572+  83  Linux
/dev/sda4            3591        9565    47994187+   f  W95 Ext'd (LBA)
/dev/sda5            3591        9434    46941898+   7  HPFS/NTFS
/dev/sda6            9435        9565     1052226   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    c  W95 FAT32 (LBA)
clay@Clay:~$

---

### Post by taurus on 2007-03-18
Are you talking about /dev/sdb1?

Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdb1   /media/sdb1   vfat   iocharset=utf8,umask=000   0   0
```
Save it.  Then, create a mount point and mount it.

```
sudo mkdir /media/sdb1
sudo mount -a
df -h
```

---

### Post by serendipity576 on 2007-03-18
If I do all of that, then what exactly will that change?

---

