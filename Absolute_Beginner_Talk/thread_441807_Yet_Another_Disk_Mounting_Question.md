---
title: "Yet Another Disk Mounting Question"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by Jay_in_TN on 2007-05-12
I installed Edgy on a separate partition on a Windows XP laptop. Upon starting up Edgy there are no disks on the Ubuntu desktop. There are no disks mounted at all other than the Edgy partition.

Would someone please explain to me how to mount individual disks on the desktop? Specifically I would like to mount /dev/hda1 and dev/hda7.

Thanks in advance for any assistance that can be provided.

Here is my information:

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7254    58267723+   7  HPFS/NTFS
/dev/hda2            7777        9733    15719602+   f  W95 Ext'd (LBA)
/dev/hda3            7255        7776     4192965    c  W95 FAT32 (LBA)
/dev/hda5            7777        8928     9253408+  83  Linux
/dev/hda6            8929        9122     1558273+  82  Linux swap / Solaris
/dev/hda7            9123        9733     4907826    b  W95 FAT32


primary@ubuntu-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5 -- converted during upgrade to edgy
UUID=05afd83f-a4e1-4541-9c72-8117891e79e3 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda7 -- converted during upgrade to edgy
UUID=7C74-0CBE /documents vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda3 -- converted during upgrade to edgy
UUID=0BA5-C59D /win_swap vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=DCECE22CECE2011E /windows ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda6 -- converted during upgrade to edgy
UUID=d0bbe0ed-dcbe-4a21-9295-10e76ed310c8 none swap sw 0 0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0



primary@ubuntu-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda5             8.7G  3.2G  5.1G  39% /
varrun                252M   92K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
procbususb             10M  104K  9.9M   2% /proc/bus/usb
udev                   10M  104K  9.9M   2% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   18M  235M   8% /lib/modules/2.6.17-11-386/volatile
/dev/hda7             4.7G  4.0K  4.7G   1% /documents
/dev/hda3             4.0G  3.0G  1.1G  74% /win_swap
/dev/hda1              56G   14G   42G  25% /windows

---

### Post by taurus on 2007-05-12
> **Jay_in_TN said:**
> 
Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7254    58267723+   7  HPFS/NTFS
/dev/hda2            7777        9733    15719602+   f  W95 Ext'd (LBA)
/dev/hda3            7255        7776     4192965    c  W95 FAT32 (LBA)
/dev/hda5            7777        8928     9253408+  83  Linux
/dev/hda6            8929        9122     1558273+  82  Linux swap / Solaris
/dev/hda7            9123        9733     4907826    b  W95 FAT32


primary@ubuntu-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5 -- converted during upgrade to edgy
UUID=05afd83f-a4e1-4541-9c72-8117891e79e3 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda7 -- converted during upgrade to edgy
UUID=7C74-0CBE /documents vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda3 -- converted during upgrade to edgy
UUID=0BA5-C59D /win_swap vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=DCECE22CECE2011E /windows ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda6 -- converted during upgrade to edgy
UUID=d0bbe0ed-dcbe-4a21-9295-10e76ed310c8 none swap sw 0 0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0



primary@ubuntu-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda5             8.7G  3.2G  5.1G  39% /
varrun                252M   92K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
procbususb             10M  104K  9.9M   2% /proc/bus/usb
udev                   10M  104K  9.9M   2% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   18M  235M   8% /lib/modules/2.6.17-11-386/volatile
/dev/hda7             4.7G  4.0K  4.7G   1% /documents
/dev/hda3             4.0G  3.0G  1.1G  74% /win_swap
/dev/hda1              56G   14G   42G  25% /windows

Instead of mounting /dev/hda1 to /windows and /dev/hda7 to /documents, maybe you want to mount /dev/hda1 to /media/windows and /dev/hda7 to /media/documents.  

Therefore, edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add /media in front of /documents and /windows.  Save the changes and create the two new mount points.

```
sudo mkdir /media/documents /media/windows
```
Reboot and you should see two icons on your desktop for those two partitions.

---

### Post by Jay_in_TN on 2007-05-12
I don't have much experience working with terminal and sudo.
Should I type exactly what you wrote, then provide a password, and then type exactly what you wrote in the second text box?
I tried this once and got the following:
primary@ubuntu-laptop:~$ gksudo gedit /etc/fstab

(gedit:5690): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by taurus on 2007-05-12
> **Jay_in_TN said:**
> I don't have much experience working with terminal and sudo.
Should I type exactly what you wrote, then provide a password, and then type exactly what you wrote in the second text box?
I tried this once and got the following:
primary@ubuntu-laptop:~$ gksudo gedit /etc/fstab

(gedit:5690): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

It's just a warning.  Don't worry about it.  You should get a new window with /etc/fstab for you to edit.

---

### Post by Jay_in_TN on 2007-05-13
I followed the directions exactly and it worked perfectly.
When I installed Edgy these drives were already named /media/drive_name
I screwed it up by renaming them and removing the "media" portion of the name. Live and learn, right?

The users in this forum are great. Thanks again for your prompt help.
My disks are mounted on the desktop where I wanted them.

Jay

---

