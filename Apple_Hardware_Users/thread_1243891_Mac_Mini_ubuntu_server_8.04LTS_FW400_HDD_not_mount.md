---
title: "Mac Mini ubuntu server 8.04LTS FW400 HDD not mounting"
date: 2009-08-18
forum: Apple Hardware Users
---

### Post by Ekos on 2009-08-18
How is it going. I did a search and can't seem to find what I need, or don't know what to look for. I am running 8.04 server and formatted a drive ext3 as per [InstallingANewHardDrive]("https://help.ubuntu.com/community/InstallingANewHardDrive"), but when I mount the drive I can't access. I think it might be the physical id, or access. How can I fix this? Any help is appreciated, Thanks

Carlos 

Some info...


******@MacMini:~$ sudo lshw -C disk
  *-cdrom                 
       description: DVD reader
       product: CD-RW  CW-8124
       vendor: MATSHITA
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: DACH
       serial: [MATSHITACD-RW  CW-8124  DACHPP  02/01/06+C
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=open
  *-disk
       description: ATA Disk
       product: Hitachi HTS54168
       vendor: Hitachi
       physical id: 0.1.0
       bus info: scsi@2:0.1.0
       logical name: /dev/sda
       version: SB2A
       serial: SB22F9KGH11EUS
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00084f37
  *-disk
       description: SCSI Disk
       product: Disk
       vendor: Ext Hard
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       logical name: /media/maindisk
       size: 1397GiB (1500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=4 mount.fstype=ext3 mount.options=rw,relatime,data=ordered signature=e2b3d1a5 state=mounted

******@MacMini:~$ ls -l /media
total 8
lrwxrwxrwx 1 root root    6 2009-08-18 01:54 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2009-08-18 01:54 cdrom0
drwxr-xr-x 3 root root 4096 2009-08-18 19:12 maindisk
******@MacMini:~$

---

### Post by hajk on 2009-08-20
It seems that your external HD is mounted OK on /media/maindisk... you seem not to have partitioned that HD since it is recognized as /dev/sdb -- this is a bit unusual, but OK.

You should edit the /etc/fstab file: look for a line starting with /dev/sdb, then add the following mount options (in addition to "rw,relatime"): "users,exec", so the whole line should look something like```

/dev/sdb   /media/maindisk  ext3  rw,relatime,users,exec  0   1
```
You may wish to add the mount option "auto" if the external HD is always connected.

Next, make sure that you (as user) are a member of the "users" group:```

$ sudo adduser <your-ID> users
```and, finally, remount with```

$ sudo mount -a
```
Have fun!

---

### Post by Ekos on 2009-09-18
Still struggling... Any tips? The Mac sees it, but I can't get in it I guess...

@MacMini:~$ sudo lshw -C disk 
  *-cdrom                 
       description: DVD reader
       product: CD-RW  CW-8124
       vendor: MATSHITA
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: DACH
       serial: [MATSHITACD-RW  CW-8124  DACHPP  02/01/06+C
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=open
  *-disk
       description: ATA Disk
       product: Hitachi HTS54168
       vendor: Hitachi
       physical id: 0.1.0
       bus info: scsi@2:0.1.0
       logical name: /dev/sda
       version: SB2A
       serial: SB22F9KGH11EUS
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000449a7
  *-disk
       description: SCSI Disk
       product: Disk
       vendor: Ext Hard
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       size: 1397GiB (1500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=4 signature=7fc8693f

@MacMini:~$ ls -l /media
total 8
lrwxrwxrwx 1 root root    6 2009-08-31 19:20 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2009-08-31 19:20 cdrom0
drwxr-xr-x 3 root root 4096 2009-09-09 22:02 maindisk

---

