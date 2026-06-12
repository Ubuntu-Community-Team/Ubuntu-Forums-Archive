---
title: "mount -a"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by pavel_kbc on 2006-11-27
Hello pplz, i got problem with mount . 
root@r00t-server:/home/r00t# mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hda10,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: mount point /mnt/song does not exist
root@r00t-server:/home/r00t# 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda14
UUID=165c6ec4-2a6c-4ced-ae21-4a0ef113465b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda15
UUID=344f204a-e953-40d5-b5ca-d97cc853cbae none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/hda1 /media/windows ntfs umask=0222 0 0
/dev/hda10 /mnt/Other vfat auto,r00t,rw 0 0
/dev/hda11 /mnt/song vfat auto,r00t,rw 0 0
```


sudo mount -t vfat -o rw,uid=r00t,umask=000 /dev/hda11 /mnt/songs

i use this one to mount it every restart . please help me 

:(

---

### Post by konst88 on 2006-11-27
The error says it is a problem on /dev/hda10 and not on /dev/hda11.
Maybe check the line about /dev/hda10.
Maybe after an error, it stops reading the fstab file, so you nay also try too put the /dev/hda11 before /dev/hda10.
Good luck.

---

### Post by taurus on 2006-11-27
From a terminal, Applications -> Accessories -> Terminal, paste the output of this command here!

```
sudo fdisk -l
```
On the other hand, I recommand you modify your /etc/fstab to make the last two lines to look like these!

```

/dev/hda10  /mnt/Other vfat iocharset=utf8,umask=000  0  0
/dev/hda11  /mnt/song  vfat iocharset=utf8,umask=000  0  0

```

---

### Post by pavel_kbc on 2006-11-27
ok i add your code taurus. now lamme restart my pc and see whatz happened :)

can you help me to mount those drives 

 Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1584    12723448+   7  HPFS/NTFS
/dev/hda2            1585        9732    65448810    f  W95 Ext'd (LBA)
/dev/hda5            1585        2232     5205028+  83  Linux
/dev/hda6            2233        2359     1020096   83  Linux
/dev/hda7            2360        2486     1020096   82  Linux swap / Solaris
/dev/hda8            2487        3114     5044378+   7  HPFS/NTFS
/dev/hda9            3115        4232     8980303+   b  W95 FAT32
/dev/hda10           4645        6174    12289693+   b  W95 FAT32
/dev/hda11           6175        7704    12289693+   b  W95 FAT32
/dev/hda12           7705        9285    12699351    b  W95 FAT32
/dev/hda13           9286        9732     3590496    b  W95 FAT32
/dev/hda14           4233        4622     3132643+  83  Linux
/dev/hda15           4623        4644      176683+  82  Linux swap / Solaris 

Thanks

---

### Post by pavel_kbc on 2006-11-27
i restarted but isnt working

---

### Post by taurus on 2006-11-27
What isn't working?  Any error message?  What is the output of this command from a terminal?

```
ls -la /mnt
```

---

### Post by darrenm on 2006-11-27
```
/dev/hda10 /mnt/Other vfat auto,r00t,rw 0 0
```

Where it says r00t in the fstab entry - I don't understand what that is there for?

---

### Post by pavel_kbc on 2006-11-27
taurus,

root@r00t-server:/home/r00t# ls -la /mnt
total 40
drwxr-xr-x  6 root root  4096 2006-11-26 06:00 .
drwxr-xr-x 22 root root  4096 2006-11-27 01:50 ..
drwxrwxrwx 23 root root  8192 1970-01-01 06:00 Other
drwxr-xr-x  2 root root  4096 2006-11-25 16:34 shared
drwxrwxrwx 38 r00t root 16384 1970-01-01 06:00 songs
drwxr-xr-x  2 root root  4096 2006-11-26 05:59 test


---------xx-x-x----------
darrenm, i saw it on this forum .. i am really newbie on linux . i am using it since friday.
 its was 
/dev/hda10 /mnt/Other vfat auto,users,rw 0 0 not r00t

can you please give me your msn id or others IM id

---

### Post by taurus on 2006-11-27
D'OH!!!  You mount it to a wrong mount point!!!  Change this 

```
/dev/hda11  /mnt/song  vfat iocharset=utf8,umask=000  0  0
```
to

```
/dev/hda11  /mnt/songs  vfat iocharset=utf8,umask=000  0  0
```
in /etc/fstab...

---

### Post by pavel_kbc on 2006-11-27
oops :) Thank you so much :)
can you help me to mount with other drive ? i cant mount them .. its showing me some error 

Device Boot Start End Blocks Id System
/dev/hda1 * 1 1584 12723448+ 7 HPFS/NTFS
/dev/hda2 1585 9732 65448810 f W95 Ext'd (LBA)
/dev/hda5 1585 2232 5205028+ 83 Linux
/dev/hda6 2233 2359 1020096 83 Linux
/dev/hda7 2360 2486 1020096 82 Linux swap / Solaris
/dev/hda8 2487 3114 5044378+ 7 HPFS/NTFS
/dev/hda9 3115 4232 8980303+ b W95 FAT32
/dev/hda10 4645 6174 12289693+ b W95 FAT32
/dev/hda11 6175 7704 12289693+ b W95 FAT32
/dev/hda12 7705 9285 12699351 b W95 FAT32
/dev/hda13 9286 9732 3590496 b W95 FAT32
/dev/hda14 4233 4622 3132643+ 83 Linux
/dev/hda15 4623 4644 176683+ 82 Linux swap / Solaris

---

### Post by taurus on 2006-11-27
> **pavel_kbc said:**
> oops :) Thank you so much :)
can you help me to mount with other drive ? i cant mount them .. its showing me some error 

Device Boot Start End Blocks Id System
/dev/hda1 * 1 1584 12723448+ 7 HPFS/NTFS
/dev/hda2 1585 9732 65448810 f W95 Ext'd (LBA)
/dev/hda5 1585 2232 5205028+ 83 Linux
/dev/hda6 2233 2359 1020096 83 Linux
/dev/hda7 2360 2486 1020096 82 Linux swap / Solaris
/dev/hda8 2487 3114 5044378+ 7 HPFS/NTFS
/dev/hda9 3115 4232 8980303+ b W95 FAT32
/dev/hda10 4645 6174 12289693+ b W95 FAT32
/dev/hda11 6175 7704 12289693+ b W95 FAT32
/dev/hda12 7705 9285 12699351 b W95 FAT32
/dev/hda13 9286 9732 3590496 b W95 FAT32
/dev/hda14 4233 4622 3132643+ 83 Linux
/dev/hda15 4623 4644 176683+ 82 Linux swap / Solaris

Which ones?

---

### Post by pavel_kbc on 2006-11-27
all of them

---

### Post by taurus on 2006-11-27
> **pavel_kbc said:**
> all of them
Oh dear.  It's going to be a long one!!!

Okay. you need to edit your /etc/fstab

```
gksudo gedit /etc/fstab
```
and add the following lines to the end of it...

```

/dev/hda7   none   swap   sw   0   0
/dev/hda5   /media/linux_1   ext3   defaults   0   2
/dev/hda6   /media/linux_2   ext3   defaults   0   2
/dev/hda8   /media/widows_2  ntfs   defaults,umask=0222   0   0
/dev/hda9   /media/fat32_1   vfat   iocharset=utf8,umask=000    0   0
/dev/hda12  /media/fat32_2   vfat   iocharset=utf8,umask=000    0   0
/dev/hda13  /media/fat32_3   vfat   iocharset=utf8,umask=000    0   0

```
Then, create a bunch of mount points for those partitions.

```

sudo mkdir /media/linux_1  /media/linux_2  /media/windows_2  /media/fat32_1  /media/fat32_2  /memdia/fat32_3

```
Now, just mount the whole thing, including a new swap partition!

```
sudo mount -a
free  <-- see the increase in swap space.
df -h <-- everything should mount according to /etc/fstab
```

---

### Post by pavel_kbc on 2006-11-27
its showing error 
root@r00t-server:/home/r00t# mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/hda6,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: mount point /media/widows_2 does not exist

-----------------------

root@r00t-server:/home/r00t# free
             total       used       free     shared    buffers     cached
Mem:        506232     486784      19448          0       8468     165900
-/+ buffers/cache:     312416     193816
Swap:       176672      17808     158864
root@r00t-server:/home/r00t# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda14            3.0G  2.5G  355M  88% /
varrun                248M  116K  248M   1% /var/run
varlock               248M     0  248M   0% /var/lock
procbususb             10M  136K  9.9M   2% /proc/bus/usb
udev                   10M  136K  9.9M   2% /dev
devshm                248M     0  248M   0% /dev/shm
lrm                   248M   18M  231M   7% /lib/modules/2.6.17-10-generic/volatile
/dev/hda1              13G  8.5G  3.8G  70% /media/windows
/dev/hda11             12G   12G  132M  99% /mnt/songs
/dev/hda10             12G  9.2G  2.6G  78% /mnt/Other
/dev/hda9             8.6G  7.5G  1.1G  88% /media/fat32_1
/dev/hda12             13G  9.2G  3.0G  76% /media/fat32_2
/dev/hda13            3.5G  3.2G  234M  94% /media/fat32_3
root@r00t-server:/home/r00t# 

Thankz :D 

can you please tell me how to remove read only dir from SHH

---

### Post by taurus on 2006-11-27
> **pavel_kbc said:**
> its showing error 
root@r00t-server:/home/r00t# mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/hda6,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: mount point /media/widows_2 does not exist

-----------------------

root@r00t-server:/home/r00t# free
             total       used       free     shared    buffers     cached
Mem:        506232     486784      19448          0       8468     165900
-/+ buffers/cache:     312416     193816
Swap:       176672      17808     158864
root@r00t-server:/home/r00t# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda14            3.0G  2.5G  355M  88% /
varrun                248M  116K  248M   1% /var/run
varlock               248M     0  248M   0% /var/lock
procbususb             10M  136K  9.9M   2% /proc/bus/usb
udev                   10M  136K  9.9M   2% /dev
devshm                248M     0  248M   0% /dev/shm
lrm                   248M   18M  231M   7% /lib/modules/2.6.17-10-generic/volatile
/dev/hda1              13G  8.5G  3.8G  70% /media/windows
/dev/hda11             12G   12G  132M  99% /mnt/songs
/dev/hda10             12G  9.2G  2.6G  78% /mnt/Other
/dev/hda9             8.6G  7.5G  1.1G  88% /media/fat32_1
/dev/hda12             13G  9.2G  3.0G  76% /media/fat32_2
/dev/hda13            3.5G  3.2G  234M  94% /media/fat32_3
root@r00t-server:/home/r00t# 

Thankz :D 

A few problems.  You forgot to create a mount point /media/windows_2 for /dev/hda8!

Do you know what are the filesystems for both /dev/hda5 & /dev/hda6?  They are not ext3 as I thought so perhaps they are ext2!  Replace the ext3 with ext2 in /etc/fstab for both /dev/hda5 & /dev/hda6 and see if you can mount those two partitions now.  Otherwise, paste the output of this command here.

```
dmesg | tail
```

> can you please tell me how to remove reonly dir from SHH
SHH!!!  :confused:

---

### Post by pavel_kbc on 2006-12-07
i mean to say how to remove from terminal

---

