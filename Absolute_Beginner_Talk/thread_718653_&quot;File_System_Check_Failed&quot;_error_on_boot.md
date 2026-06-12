---
title: "&quot;File System Check Failed&quot; error on boot up"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by toomuchcomputertime on 2008-03-08
At boot up, I get the message 'File System Check Failed'. It then goes on and says that it is opening a shell to fix it in, and gives me the log path /var/log/fsck/checkfs. 

the log is:

Log of fsck -C -R -A -a 
Sat Mar  8 09:50:16 2008

fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Unable to resolve 'LABEL=/boot'

fsck.ext3: Unable to resolve 'LABEL=/home'

fsck died with exit status 8

Sat Mar  8 09:50:16 2008
----------------

How can I fix this? I have just been typing 'reboot', to skip fixing the file system. Thanks

---

### Post by glennric on 2008-03-08
This is most likely a problem with your fstab.  Have you changed anything with your hard drives recently?  Like added a new one or removed an old one, or modified partitions?  Post the output of 
```
cat /etc/fstab
```
and
```
sudo fdisk -l
```

---

### Post by toomuchcomputertime on 2008-03-08
I recently repartitioned the hard drive when I wiped windows ME. I have also been messing with the mount docs to try and mount  a network through samba on boot (unsuccessful). Thanks for the reply.

---

### Post by toomuchcomputertime on 2008-03-08
Also,
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e24bb7f5-5c45-4797-ae69-3fce6249579a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=67f60d4e-b147-4155-9a95-bb351ba974c9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


LABEL=/ / ext3 defaults 1 1
LABEL=/boot /boot ext3 defaults 1 2
none /dev/pts devpts gid=5,mode=620 0 0
LABEL=/home /home ext3 defaults 1 2
none /proc proc defaults 0 0
none /dev/shm tmpfs defaults 0 0
/dev/hda3 swap swap defaults 0 0
/dev/cdrom /mnt/cdrom iso9660 noauto,owner,kudzu,ro 0 0
/dev/hdd4 /mnt/zip100.0 auto noauto,owner,kudzu 0 0
/dev/fd0 /mnt/floppy auto noauto,owner,kudzu 0 0
smb://192.168.1.2/My%20Documents /home/mnt smbfs 

#credentials=/home/matthew/.smbpasswd,uid=user,gid=user,dmask=700,fmask=700 0 0

smb://192.168.1.2/F /home/mnt cifs credentials=/home/#matthew/.smbpasswd,_netdev,uid=a_user_name,gid=users 0 0


and sudo fdisk-l

Disk /dev/sda: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001d13a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2373    19061091   83  Linux
/dev/sda2            2374        2482      875542+   5  Extended
/dev/sda5            2374

---

### Post by toomuchcomputertime on 2008-03-08
Could someone help?

---

