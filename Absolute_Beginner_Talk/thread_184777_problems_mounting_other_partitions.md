---
title: "problems mounting other partitions"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by Perfex on 2006-05-30
Trouble mounting other partitions on my windows drive, I did get the windows drive up and running using

```
sudo mkdir /media/windows
sudo mount /dev/sda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```

this is what I have tryed below

```

robert@24-179-176-119:~$ sudo fdisk -l

Disk /dev/hdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3497    28089621   83  Linux
/dev/hdb2            3498        3649     1220940    5  Extended
/dev/hdb5            3498        3649     1220908+  82  Linux swap / Solaris

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3306    26555413+   7  HPFS/NTFS
/dev/sda2            3307       14593    90662827+   f  W95 Ext'd (LBA)
/dev/sda5            3307        7130    30716248+   7  HPFS/NTFS
/dev/sda6            7131        8170     8353768+   7  HPFS/NTFS
/dev/sda7            8171       14593    51592716    7  HPFS/NTFS

Disk /dev/sdb: 2047 MB, 2047868928 bytes
255 heads, 63 sectors/track, 248 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          10       80293+   0  Empty
/dev/sdb2              11         248     1911732    b  W95 FAT32
robert@24-179-176-119:~$ sudo mount /dev/sda5 /archive/ -t vfat -o iocharset=utf8,umask=000
mount: mount point /archive/ does not exist
robert@24-179-176-119:~$ sudo mkdir /archive
robert@24-179-176-119:~$  sudo mount /dev/sda5 /archive/ -t vfat -o iocharset=utf8,umask=000
mount: /dev/sda5 already mounted or /archive/ busy
mount: according to mtab, /dev/sda5 is mounted on /
robert@24-179-176-119:~$ sudo mount /dev/sda5 /archive -t ntfs -o nls=utf8,umask=0222
mount: /dev/sda5 already mounted or /archive busy
mount: according to mtab, /dev/sda5 is mounted on /
robert@24-179-176-119:~$
```

any help would be very appreciated :)

---

### Post by patrick295767 on 2006-05-30
Can be easier maybe with /etc/fstab: Could you post your /etc/fstab ?
 
We can check/modify it to mount easily your partitions ...

---

### Post by Perfex on 2006-05-30
[QUOTE=patrick295767]Can be easier maybe with /etc/fstab: Could you post your /etc/fstab ?
 
We can check/modify it to mount easily your partitions ...[/QUOTE]

hmm

```
robert@24-179-176-119:~$ /etc/fstab
bash: /etc/fstab: Permission denied
```\

just learning the command line :|

---

### Post by Jagot on 2006-05-30
Do:

```
cat /etc/fstab
```

---

### Post by Noelinho on 2006-05-30
```
sudo gedit /etc/fstab
```

Do that and it'll open it in the text editor - you need to be logged in as root :)

---

### Post by Perfex on 2006-05-30
[QUOTE=Jagot]Do:

```
cat /etc/fstab
```[/QUOTE]


ok heres the etc/fstab

I have ide cdrw, a ipod nano, 1 ide drive (30 gig) and 1 sata drive (120 gig) with 3 partitions on it installed in the sata, and just ubuntu on the 30 gig

```
robert@24-179-176-119:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

```

---

### Post by aysiu on 2006-05-30
```
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
``` This line should be ```
/dev/sda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
``` I'm not sure what this line is for: ```
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
``` Once you've made changes to your /etc/fstab, type ```
sudo umount /dev/sda1
sudo mount -a
``` From now on your /dev/sda1 should automount at boot time.

---

### Post by Perfex on 2006-05-30
[QUOTE=aysiu]```
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
``` This line should be ```
/dev/sda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
``` I'm not sure what this line is for: ```
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
``` Once you've made changes to your /etc/fstab, type ```
sudo umount /dev/sda1
sudo mount -a
``` From now on your /dev/sda1 should automount at boot time.[/QUOTE]

Yes I was able to get the main windows partition to mount previously using the code changed to sda from a guide, but I am not sure how to get the 2 other partitions on that drive mounted, in windows I labled them archive & games

hmm the usb sais in my computer though I am not able to access it (unable to mount it said)

type: folder
contents: nothing
location: computer:///
Volume: root volume (3)
free space: 22.9gb

---

### Post by aysiu on 2006-05-30
[QUOTE=Perfex]Yes I was able to get the main windows partition to mount previously using the code changed to sda from a guide, but I am not sure how to get the 2 other partitions on that drive mounted, in windows I labled them archive & games

hmm the usb sais in my computer though I am not able to access it (unable to mount it said)

type: folder
contents: nothing
location: computer:///
Volume: root volume (3)
free space: 22.9gb[/QUOTE] It's the same deal--add in the appropriate lines. For example... ```
/dev/sda5            /archive        ntfs    nls=utf8,umask=0222   0  0
/dev/sda6            /games        ntfs     nls=utf8,umask=0222   0  0
``` I'm guess which partitions are which, but you get the point. Of course, you have to create those directories first: ```
sudo mkdir /archive
sudo mkdir /games
```

---

### Post by Perfex on 2006-05-30
[QUOTE=aysiu]It's the same deal--add in the appropriate lines. For example... ```
/dev/sda5            /archive        ntfs    nls=utf8,umask=0222   0  0
/dev/sda6            /games        ntfs     nls=utf8,umask=0222   0  0
``` I'm guess which partitions are which, but you get the point. Of course, you have to create those directories first: ```
sudo mkdir /archive
sudo mkdir /games
```[/QUOTE]


Hmm I cant see them.. looks like this now :-k 
```

robert@24-179-176-119:~$  sudo fdisk -l

Disk /dev/hdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3497    28089621   83  Linux
/dev/hdb2            3498        3649     1220940    5  Extended
/dev/hdb5            3498        3649     1220908+  82  Linux swap / Solaris

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3306    26555413+   7  HPFS/NTFS
/dev/sda2            3307       14593    90662827+   f  W95 Ext'd (LBA)
/dev/sda5            3307        7130    30716248+   7  HPFS/NTFS
/dev/sda6            7131        8170     8353768+   7  HPFS/NTFS
/dev/sda7            8171       14593    51592716    7  HPFS/NTFS

Disk /dev/sdb: 2047 MB, 2047868928 bytes
255 heads, 63 sectors/track, 248 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          10       80293+   0  Empty
/dev/sdb2              11         248     1911732    b  W95 FAT32
robert@24-179-176-119:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
/dev/sda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
/dev/sda5            /archive        ntfs    nls=utf8,umask=0222   0  0
/dev/sda6            /games        ntfs     nls=utf8,umask=0222   0  0
robert@24-179-176-119:~$
```

---

### Post by aysiu on 2006-05-30
Have you tried this? ```
sudo mount -a
cd /games
ls
cd /archive
ls
```

---

### Post by Perfex on 2006-05-30
[QUOTE=aysiu]Have you tried this? ```
sudo mount -a
cd /games
ls
cd /archive
ls
```[/QUOTE]

in windows it looks like this

C Local Disk 25933.0
D Games 29,996.3
G Movies 8,158.0
E Archives 50,383.5

I had forgotten there was a small partition made for a few movies, looks like they are showing... though in my computer still shows my ipod, and windows only mounted, im sorry not very familar with ubuntu yet, but im trying :???: 
```
robert@24-179-176-119:~$ sudo mount -a
robert@24-179-176-119:~$ cd /games
robert@24-179-176-119:/games$ ls
Hellboy   Resident Evil Apocalypse  System Volume Information  Van Helsing
I, Robot  Resident Evil.avi         the village.mpg
robert@24-179-176-119:/games$ cd /archive
robert@24-179-176-119:/archive$ ls
AUTOEXEC.BAT  Games   Movies     msdownld.tmp  System Volume Information
CONFIG.SYS    IO.SYS  MSDOS.SYS  RECYCLER      WUTemp
```

---

### Post by Kleist on 2006-06-01
I'd appreciate any help. 

I just installed ubuntu in my computer. I left one partition with my documents and music, and in the free space I installed ubuntu. Now, I want to mount the ntfs partition, but nothing happens. 

My original fstab file looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Then, I insert the last line and I delete the line which starts with /dev/hda6, since this is the partition I want to mount:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda6       /media/windows  ntfs    umask=0222      0       0

After this I boot the computer but the partition is not mounted. 
I tried to do it manually with:

sudo mount /dev/hda6 /media/windows/ -t ntfs -o umask=0222

and I get this:

mount: wrong fs type, bad option, bad superblock on /dev/hda6,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


[4294764.526000] Bluetooth: HCI device and connection manager initialized
[4294764.526000] Bluetooth: HCI socket layer initialized
[4294764.604000] Bluetooth: L2CAP ver 2.7
[4294764.604000] Bluetooth: L2CAP socket layer initialized
[4294764.685000] Bluetooth: RFCOMM ver 1.5
[4294764.685000] Bluetooth: RFCOMM socket layer initialized
[4294764.685000] Bluetooth: RFCOMM TTY layer initialized
[4295274.341000] NTFS-fs error (device hda6): read_ntfs_boot_sector(): Primary boot sector is invalid.
[4295274.341000] NTFS-fs error (device hda6): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[4295274.341000] NTFS-fs error (device hda6): ntfs_fill_super(): Not an NTFS volume.


What am I doing wrong? Any help, I'll appreciated.

---

### Post by hanexar on 2006-06-01
I just check my fstab, and my windows line look like this:
```

/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

```
so try to add the nls=utf8, thing before the umask.  I do the same when I mount it manually.  I hope it will fix your problem.

---

### Post by Boelcke on 2006-06-04
I've been struggling mounting both a FAT32 partition, and some NTFS partitions in Ubuntu. I followed some of the great advice in this thread, but it didn't all work.  I did find a solution in the IRC chatroom, though.

This script is like butter:

[http://www.ubuntulinux.nl/files/diskmounter](http://www.ubuntulinux.nl/files/diskmounter)

It checks out what's available, and updates your fstab file for you! If you're interested, it's a good idea to check out that /etc/fstab file afterwards to see how it did it. Otherwise, it just works.

Notes:

1. Backup your existing fstab file first!
```
sudo cp /etc/fstab /etc/fstab.backup
```
2. If you have any partitions listed in the fstab that are not behaving the way you want them to, DELETE (not comment) them out of the fstab file before running the script.
```
sudo gedit /etc/fstab
```

---

