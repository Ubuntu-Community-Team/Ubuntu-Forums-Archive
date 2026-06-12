---
title: "help mounting harddrive"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by williehfc on 2006-11-23
when i try to mount my second harddrive i get
 Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9964    80035798+   5  Extended
then if i sudo nano /etc/fstab i get

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0 $/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,g$/dev/hda5       /media/hda5     vfat    defaults,utf8,umask=007,gid=4$/dev/hda6       none            swap    sw              0       0
/dev/hdb        /media/hdb      vfat    defaults,unmask= 000 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
 then when i sudo mount -a i get 
mount: /dev/hdb already mounted or /media/hdb busy
 how do i mount this drive and also get permmision to write to it

---

### Post by taurus on 2006-11-23
It needs to look like this...

```

/dev/hdb1  /media/hdb  vfat  defaults,umask=000  0  0

```

---

### Post by williehfc on 2006-11-23
still when i sudo mount -a
 i get mount: /dev/hdb already mounted or /media/hdb busy
 but its not mounted or i dont have permission to write to it

---

### Post by taurus on 2006-11-23
```
sudo umount /media/hdb
sudo mount -a
df -h
```

---

### Post by williehfc on 2006-11-23
when i sudo unmount /media/hdb it tells me hdb not mounted
when i sudo mount -a i get 
/dev/hdb already mounted or /media/hdb busy
when i df -h i get 
Filesystem            Size Used Avail Use% Mounted on
/dev/hda7              14G   11G  2.3G  83% /
varrun                379M   92K  379M   1% /var/run
varlock               379M  4.0K  379M   1% /var/lock
udev                  379M  108K  379M   1% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   19M  361M   5% /lib/modules/2.6.15-27-386/volatile
/dev/hda1              11G  6.7G  4.0G  64% /media/hda1
/dev/hda5              49G   27G   23G  54% /media/hda5

---

### Post by taurus on 2006-11-23
Show me the output of these three commands then!

```
ls -la /media
sudo fdisk -l
cat /etc/fstab
```
p.s.  It's umount, not u**[SIZE="3"]n[/SIZE]**mount...

---

### Post by williehfc on 2006-11-23
ls -la /media
total 56
drwxr-xr-x  6 root root     4096 2006-11-08 23:38 .
drwxr-xr-x 25 root root     4096 2006-11-23 17:38 ..
lrwxrwxrwx  1 root root        6 2006-10-27 15:05 cdrom -> cdrom0
drwxr-xr-x  2 root root     4096 2006-10-27 15:05 cdrom0
dr-xr-x---  1 root plugdev  8192 2006-11-19 19:15 hda1
drwxrwx--- 12 root plugdev 32768 1970-01-01 01:00 hda5
drwxr-xr-x  2 root root     4096 2006-11-08 23:38 hdb

sudo fdisk -l
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1382    11100883+   7  HPFS/NTFS
/dev/hda2            1383        9729    67047277+   f  W95 Ext'd (LBA)
/dev/hda5            1383        7757    51207156    b  W95 FAT32
/dev/hda6            9542        9729     1510078+  82  Linux swap / Solaris
/dev/hda7            7758        9541    14329948+  83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9964    80035798+   5  Extended

cat /etc/fstab# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0  1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0      1
/dev/hda6       none            swap    sw              0       0
/dev/hdb        /media/hdb      vfat    defaults,unmask=000 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       

cheers taurus for helping me out

---

### Post by taurus on 2006-11-23
I see your problem here.  You need to convert your /dev/hdb1 to primary so it would be like /dev/hdb1.  And if you plan to make it as an extended partition, then you need to create logical partition, /dev/hdb5, first before you can use it...

---

### Post by williehfc on 2006-11-23
any chance you could tell me how my mate normally helps me but hes gone on holiday

---

### Post by taurus on 2006-11-23
The good news is that you can manipulate the second harddrive, /dev/hdb, with Ubuntu.  You first need to install gparted and then use it to create a primary partition for /dev/hdb, /dev/hdb1, and format it as fat32/vfat.  Then, modify your /etc/fstab again to mount it...

```
sudo aptitude update
sudo aptitude install gparted
```

---

### Post by williehfc on 2006-11-23
got to go out just now will try laTER and let you know how i get on cheers

---

### Post by williehfc on 2006-11-24
taurus it wont let me make a primary partition only a logical partition any idea

---

### Post by taurus on 2006-11-24
> **williehfc said:**
> taurus it wont let me make a primary partition only a logical partition any idea
Then go ahead and create a logical partition but I believe it would be /dev/hdb5...  Do you do this in XP or in Ubuntu?

---

### Post by williehfc on 2006-11-24
when ive done that what do i do next

---

### Post by taurus on 2006-11-24
Already formatted and everything for /dev/hdb5?  Need to see the output of "sudo fdisk -l" again!

---

### Post by williehfc on 2006-11-24
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1382    11100883+   7  HPFS/NTFS
/dev/hda2            1383        9729    67047277+   f  W95 Ext'd (LBA)
/dev/hda5            1383        7757    51207156    b  W95 FAT32
/dev/hda6            9542        9729     1510078+  82  Linux swap / Solaris
/dev/hda7            7758        9541    14329948+  83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9964    80035798+   5  Extended
/dev/hdb5              21        9964    79875180    b  W95 FAT32

---

### Post by taurus on 2006-11-24
Okay.  Now, you want to edit your /etc/fstab to add an entry in there for /dev/hdb5.  From a terminal, run

```
gksudo gedit /etc/fstab
```
Then, add the following line to the end of it.  If you have a line for /dev/hdb1 or /dev/hdb previous added, remove that line...

```

/dev/hdb5  /media/hdb  vfat  defaults,umask=000  0  0

```
Since you aleady have /media/hdb that you have created before, just mount the whole thing with

```
sudo mount -a
```
Enjoy.

---

### Post by williehfc on 2006-11-24
cheers mate added you to my buddy list incase i need your help again hope thats ok

---

### Post by taurus on 2006-11-24
> **williehfc said:**
> cheers mate added you to my buddy list incase i need your help again hope thats ok
I assume if I made it to your buddy list, it means that everything is working fine with /dev/hdb5!  ;)  That's fine with me.

I see that you are from Scotland!  Where in Scotland anyway if you don't mind I'm asking?

---

### Post by pavel_kbc on 2006-11-25
i got those drives. 
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

can you make code for those.. when i install ubuntu . i selete resize .. and its make 15 dev :S

---

### Post by taurus on 2006-11-25
> **pavel_kbc said:**
> i got those drives. 
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

can you make code for those.. when i install ubuntu . i selete resize .. and its make 15 dev :S
What exactly do you have in mind?  Looks to me like you have two versions of Linux running on your harddrive!

---

