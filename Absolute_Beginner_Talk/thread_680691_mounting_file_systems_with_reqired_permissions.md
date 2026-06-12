---
title: "mounting file systems with reqired permissions"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by arjayes on 2008-01-28
so when i partitioned my hard drive .  I kept one partition exclusively to backup data on .
how do i alter my fstab file to automount that partition  on start up with read write permissions for my user account .

---

### Post by The Cog on 2008-01-28
Need more info. Can you post the output of the two commands
```
sudo fdisk -l
df -h
```
and perhaps tell us which partition is the backup one.
Also, what version of Ubuntu are you using?

---

### Post by arjayes on 2008-01-28
here r the outputs 
sudo fdisk -l :
> 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b530b52

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3825    30724281    7  HPFS/NTFS
/dev/sda2            3826        6951    25109595   83  Linux
/dev/sda3            6952       10076    25101562+  83  Linux
/dev/sda4           10077       19457    75352882+   5  Extended
/dev/sda5           10077       19364    74605797   83  Linux
/dev/sda6           19365       19457      746991   82  Linux swap / Solaris



df -h :

> 

08:23 PM:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              24G   23G   18M 100% /
varrun                501M  100K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M   72K  501M   1% /dev
devshm                501M     0  501M   0% /dev/shm
lrm                   501M   34M  468M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sda3              24G  1.8G   21G   8% /media/debian
/dev/sda1              30G   22G  8.2G  73% /media/windows
/dev/sda5              71G   14G   53G  21% /home/arjayes/storage




the storage partition is quite obviously /dev/sda5

---

### Post by Furat on 2008-01-28
what about the other users , do u want them to just read from the partition ??? or they can't have any access on it ??

---

### Post by arjayes on 2008-01-28
i'm the only one who uses this comp. so i have only one user a/c so yeah read write permissions only for me ..

---

### Post by Furat on 2008-01-28
I didn't get it , if you are the only user that mean you can mount the partion like any other one  , and from the output of the "df -h " I can tell  it is already mounted, where is the problem ????

---

### Post by arjayes on 2008-01-28
its mounted but ... only root has read write permissions .. and its a real pain running every program that uses that data as root .. so it would be very convenient if i could mount that partition with read write permissions for my user account ...

---

### Post by Furat on 2008-01-28
simply you can create a directory owned by your  user and backup every thing on it 
```
sudo mkdir -m yourusername /home/arjayes/storage/storages
``` 
But if you insist on make it using fstab you need to add users option to the line which mount your partition , please backup your fstab before you do any changes

---

### Post by arjayes on 2008-01-28
Thanks ur way was much simpler ... i still haven't got a full understanding of user permissions .. and as i have a "personal" computer it hadn't been an isue earlier ... this put things in perspective ..

---

