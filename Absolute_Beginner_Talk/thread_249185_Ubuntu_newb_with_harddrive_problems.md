---
title: "Ubuntu newb with harddrive problems"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by nidoo on 2006-09-02
Hi, I just migrated over to ubuntu after trying out the live cd for the last couple of months, find it awesome but there is just one problem I'm having. I have a second ata harddrive (40 gigs) slaved to my primary(10 gigs) which has ubuntu loaded on. I've followed what guides there are and I've gotten it formated and mounted but it won't let do anything with it.](*,) I use this for downloading and storage. Can anyone help me set this up? 
*-disk:0
       description: ATA Disk
       product: WDC WD102BA
       vendor: Western Digital
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: 16.13M16
       serial: WD-WM9471349875
       size: 9779MB
       capacity: 9779MB
       capabilities: ata dma lba iordy smart pm partitioned partitioned:dos
       configuration: mode=udma4 smart=on
     *-volume:0
          description: Linux filesystem partition
          physical id: 1
          bus info: ide@0.0,1
          logical name: /dev/hda1
          capacity: 9342MB
          capabilities: primary bootable
     *-volume:1
          description: Extended partition
          physical id: 2
          bus info: ide@0.0,2
          logical name: /dev/hda2
          capacity: 431MB
          capabilities: extended partitioned partitioned:extended
  *-disk:1
       description: ATA Disk
       product: WDC WD400BB-75CAA0
       vendor: Western Digital
       physical id: 1
       bus info: ide@0.1
       logical name: /dev/hdb
       version: 16.06V16
       serial: WD-WMA8H2104570
       size: 37GB
       capabilities: ata dma lba iordy smart pm partitioned partitioned:dos
       configuration: mode=udma5 smart=on
     *-volume
          description: Linux filesystem partition
          physical id: 1
          bus info: ide@0.1,1
          logical name: /dev/hdb1
          capacity: 37GB
          capabilities: primary

---

### Post by jorn on 2006-09-02
Type or paste in terminal:
> sudo fdisk -l
That will list yuor partitions.
If you want the harddisk mounted on startup it must be listed in /etc/fstab.
To do this open it in terminel. Gedit is a texteditor for Ubuntu:
> sudo gedit /etc/fstab 
Please paste the output.

---

### Post by nidoo on 2006-09-02
Sure thing any help is greatly appreciated :D 
Disk /dev/hda: 10.2 GB, 10254827520 bytes
255 heads, 63 sectors/track, 1246 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1191     9566676   83  Linux
/dev/hda2            1192        1246      441787+   5  Extended
/dev/hda5            1192        1246      441756   82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40000020480 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        4863    39062016   83  Linux

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by steve.horsley on 2006-09-02
I see the slave is a Linux partition. I will assume it's formatted ext3 format. You say you have the slave disk mounted. How did you do that? I don't see it in /etc/fstab.

These instructions should get it mounted (if it's not). I'll assume that you want it mounted on /media/hdb1 - change the name to suit yourself.

Create a directory to mount it on:
**sudo mkdir /media/hdb1**

You can mount it by hand with this command:
**sudo mount -t ext3 /dev/hdb1 /media/hdb1**

And you can arrange to have it mounted every time you boot by adding this line to /etc/fstab:
**/dev/hdb1  /media/hdb1  ext3  defaults   0  2**

Once the drive is mounted, it's just a question of permissions. You may need to change the permissions and ownerships on /media/hdb1 so that anyone can write to it, or that you own it. You can do this by creating a file explorer with full privilege using this command:
**gksudo nautilus**
then find and right-click /media/hdb1 and choose Properties, Permissions. There you can set who owns the folder, and who can read/write it.

---

### Post by nidoo on 2006-09-02
Perfect, working great now. Thanks a lot Jorn and Steve.=D>

---

### Post by anoxan on 2006-09-02
ok, I've got a question. I type sudo nautilus to get root access to my drives, and I try to change the permissions in /media, but it tells me that the disk is read-only. I've been punching in random commands in fstab copied from what mtab puts out and got nothing. I'm not sure what's going on..kubuntu mounted everything first time, so what's ubuntu's deal?

terminal says:
```
anoxan@navi:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/hda1       /media/mandy    ntfs uid=1000,gid=1000,umask=007 0 0
#/dev/hda2       /media/hda2     ntfs defaults,umask=007 0 0
/dev/hda5       /media/meilin   ntfs uid=1000,gid=1000,umask=007 0 0
#/dev/hdb        /media/hdb      ntfs defaults,umask=007 0 0
/dev/hdb1       /media/illya    ntfs uid=1000,gid=1000,umask=007 0 0
#/dev/hdc        /media/hdc      ntfs defaults,umask=007 0 0
#/dev/hdc1       /media/hdc1     ntfs defaults,umask=007 0 0
#/dev/hdc2       /media/hdc2     ntfs defaults,umask=007 0 0
/dev/hdc5       /media/rin      ntfs uid=1000,gid=1000,umask=007 0 0

anoxan@navi:~$ cat /etc/mtab
/dev/hdc3 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-26-386/volatile tmpfs rw 0 0
/dev/hda1 /media/mandy ntfs rw,gid=100,umask=007 0 0
/dev/hda5 /media/meilin ntfs rw,gid=100,umask=007 0 0
/dev/hdb1 /media/illya ntfs rw,gid=100,umask=007 0 0
/dev/hdc5 /media/rin ntfs rw,gid=100,umask=007 0 0
/dev/sda1 /media/saber ntfs rw,nosuid,nodev,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0

anoxan@navi:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdc3             7.6G  2.1G  5.1G  29% /
varrun                506M   80K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  172K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   19M  488M   4% /lib/modules/2.6.15-26-386/volatile
/dev/hda1              19G  7.6G   11G  42% /media/mandy
/dev/hda5              94G   93G  1.2G  99% /media/meilin
/dev/hdb1              34G   19G   15G  57% /media/illya
/dev/hdc5              30G   20G  9.5G  68% /media/rin
/dev/sda1              39G   30G  8.9G  77% /media/saber


```
any help?

---

