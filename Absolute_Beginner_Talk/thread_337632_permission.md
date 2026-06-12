---
title: "permission"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by violin on 2007-01-13
Can you help me pls in here.. I think i made some mistake on the somewhere.

PHP Code:
kemanci@kemanci-laptop:~$ sudo fdisk -l | grep NTFS


/dev/sdb1 1 30401 244196001 7 HPFS/NTFS
PHP Code:
kemanci@kemanci-laptop:~$ sudo modprobe fuse
Password:
kemanci@kemanci-laptop:~$ sudo umount -a
umount: /dev: device is busy
umount: /proc/bus/usb: device is busy
umount: /var/run: device is busy
umount: /sys: device is busy
umount: /: device is busy
kemanci@kemanci-laptop:~$ sudo mount -a
Error opening partition device: Read-only file system
Failed to startup volume: Read-only file system
Failed to mount '/dev/hdc': Read-only file system
mount: mount point /usbdrive does not exist
kemanci@kemanci-laptop:~$ sudo mount /dev/hda1
mount: /dev/disk/by-uuid/73aa80e0-ce7d-4d2a-adc6-9d4e1750d119 already mounted or / busy
mount: according to mtab, /dev/hda1 is already mounted on /
kemanci@kemanci-laptop:~$
kemanci@kemanci-laptop:~$


my fstab
PHP Code:
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda1
UUID=73aa80e0-ce7d-4d2a-adc6-9d4e1750d119 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5
UUID=051e560d-a4d5-4794-8f11-658acaea0df0 none swap sw 0 0
/dev/hdc /media/cdrom-1 ntfs-3g silent,umask=0,locale=en_US.utf8 0 0


Now i cant open my hardisk. It is says UNABLE THE MOUNT THE VOLUME. I am not using windows xp no more so how can i fix this pls pls help.
Second i just bought new hardisk toshiba one that one opens but again it is read only. But it is wierd because the icon shows like it is a CD as it shows in the picture.

[http://img157.imageshack.us/img157/4...eenshotbv6.png](http://img157.imageshack.us/img157/4...eenshotbv6.png)

---

### Post by taurus on 2007-01-13
Do you want to mount /dev/sdb1?  Open a terminal and type

```
gksudo gedit /etc/fstab
```
Then, add this line to the end of it.

```
/dev/sdb1   /media/sdb1   ntfs   nls=utf8,umask=0222   0   0
```
Save it and create a new mount point and mount it.

```
sudo mkdir /media/sdb1
sudo mount -a
df -h
```

---

### Post by violin on 2007-01-13
it gives me this and it is still read only 
[PHP]emanci@kemanci-laptop:~$ sudo mkdir /media/sdb1
mkdir: cannot create directory `/media/sdb1': File exists
kemanci@kemanci-laptop:~$ sudo mount -a
Error opening partition device: No medium found
Failed to startup volume: No medium found
Failed to mount '/dev/hdc': No medium found
mount: special device /dev/sdb1 does not exist
kemanci@kemanci-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              36G  9.3G   25G  28% /
varrun                125M   68K  125M   1% /var/run
procbususb             10M  152K  9.9M   2% /proc/bus/usb
udev                   10M  152K  9.9M   2% /dev
/dev/mmcblk0p1        123M   71M   52M  58% /media/mmcdisk
/dev/scd0              20M   20M     0 100% /media/cdrom0
kemanci@kemanci-laptop:~$ 

[/PHP]

---

### Post by taurus on 2007-01-13
What's the output of this command from a terminal then?

```
sudo fdisk -l
```

p.s.  NTFS is still a read-only in Linux.  If you want to write to it, you need to install ntfs-3g...

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by violin on 2007-01-13
[PHP]kemanci@kemanci-laptop:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4771    38323026   83  Linux
/dev/hda2            4772        4864      747022+   5  Extended
/dev/hda5            4772        4864      746991   82  Linux swap / Solaris

Disk /dev/mmcblk0: 128 MB, 128450560 bytes
8 heads, 32 sectors/track, 980 cylinders
Units = cylinders of 256 * 512 = 131072 bytes

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         980      125424    6  FAT16

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS
kemanci@kemanci-laptop:~$ [/PHP]

i was tryting to install ntfs-3g after i ended up like this, Also it doesnt show my other external hardisk do you know why. 

thanx in advance

---

### Post by taurus on 2007-01-13
What does your /etc/fstab look like again?

```
cat /etc/fstab
```

---

### Post by violin on 2007-01-13
kemanci@kemanci-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=73aa80e0-ce7d-4d2a-adc6-9d4e1750d119 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=051e560d-a4d5-4794-8f11-658acaea0df0 none            swap    sw              0       0
/dev/hdc    /media/cdrom-1    ntfs-3g     silent,umask=0,locale=en_US.utf8 0 0

/dev/sdb1   /media/sdb1   ntfs   nls=utf8,umask=0222   0   0
kemanci@kemanci-laptop:~$ 

like this

---

### Post by taurus on 2007-01-13
And you do have /media/sdb1, right?

```
sudo mkdir /media/sdb1
```
Try to mount it again/

```
sudo mount -a
```
By the way, the entry for your CD-ROM in /etc/fstab looks real funny to me!!!

```
/dev/hdc /media/cdrom-1 ntfs-3g silent,umask=0,locale=en_US.utf8 0 0]
```

---

### Post by violin on 2007-01-13
kemanci@kemanci-laptop:~$ sudo mount -a
Error opening partition device: No medium found
Failed to startup volume: No medium found
Failed to mount '/dev/hdc': No medium found
kemanci@kemanci-laptop:~$ 


it gives me this and what you mean it s look funny im confused :-k normally how it should be, i was trying to install ntfs-3g, Also why is my second hardisk looks like cd icon

---

### Post by taurus on 2007-01-13
An entry for a CD-ROM in /etc/fstab should look something like this!

```
/dev/hdc   /media/cdrom0   udf,iso9660   user,noauto   0   0
```
Therefore, you need to modify it since the error message is for /dev/hdc...

---

### Post by violin on 2007-01-13
kemanci@kemanci-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=73aa80e0-ce7d-4d2a-adc6-9d4e1750d119 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=051e560d-a4d5-4794-8f11-658acaea0df0 none            swap    sw              0       0

/dev/hdc   /media/cdrom0   udf,iso9660   user,noauto   0   0
/dev/sdb1   /media/sdb1   ntfs   nls=utf8,umask=0222   0   0
kemanci@kemanci-laptop:~$ 

i changed it. my old external hardisk works but the new one still shows like it is a cd or something

---

### Post by violin on 2007-01-13
Now i restart the computer i tried to open my old hardisk it gives me this error UNABLE TO MOUNT THE VOLUME.. 

ok fix it 

sudo mount -a 

it worked but i still see the cd on the new one im gonna lose my mind

---

### Post by taurus on 2007-01-13
Are you talking about the /dev/mmcblk0p1?

---

### Post by violin on 2007-01-13
no, I think ubuntu doesnt see my new hardisk because this /dev/mmcblk0p1 is my mms card not the hardisk.


[http://img157.imageshack.us/img157/4269/screenshotbv6.png](http://img157.imageshack.us/img157/4269/screenshotbv6.png)

old hard disk is BJK 
new one says PASSWORD

---

### Post by taurus on 2007-01-13
You just have to add an entry in /etc/fstab to mount it, like you would with /dev/sdb1.

---

### Post by violin on 2007-01-13
kemanci@kemanci-laptop:~$ sudo mkdir /media/sdb2
kemanci@kemanci-laptop:~$ sudo mount -a
mount: special device /dev/sdb2 does not exist


it say this 

etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=73aa80e0-ce7d-4d2a-adc6-9d4e1750d119 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=051e560d-a4d5-4794-8f11-658acaea0df0 none            swap    sw              0       0

/dev/hdc   /media/cdrom0   udf,iso9660   user,noauto   0   0
/dev/sdb1   /media/sdb1   ntfs   nls=utf8,umask=0222   0   0
/**dev/sdb2   /media/sdb2   ntfs   nls=utf8,umask=0222   0   0**
i add it like that

and new harddisk like this /media/cdrom-1 calls like that

---

### Post by taurus on 2007-01-13
According to your "sudo fdisk -l", there is no /dev/sdb2.  Instead, it's called /dev/mmcblk0p1 and it has a fat32/vfat filesystem.  Therefore, an entry for it in /etc/fstab should be (remove the /dev/sdb2 from it first)

```
/dev/mmcblk0p1   /media/sdb2   vfat   iocharset=utf8,umask=000   0   0
```
Save it.  To make sure you have /media/sdb2, create it.

```
sudo mkdir /media/sdb2
sudo mount -a
df -h
```
Or reboot if you wish.

---

### Post by violin on 2007-01-13
kemanci@kemanci-laptop:~$ sudo mount -a
Password:
mount: special device /dev/sdb1 does not exist
mount: special device /dev/mmcblk0p1 does not exis

fstab 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=73aa80e0-ce7d-4d2a-adc6-9d4e1750d119 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=051e560d-a4d5-4794-8f11-658acaea0df0 none            swap    sw              0       0

/dev/hdc   /media/cdrom0   udf,iso9660   user,noauto   0   0
/dev/sdb1   /media/sdb1   ntfs   nls=utf8,umask=0222   0   0
/dev/mmcblk0p1   /media/sdb2   vfat   iocharset=utf8,umask=000   0   0


After restating now i can not open my old hardisk and toshiba one still look like it is CD. ](*,) But mms card work fine. I m really sorry man bothering you like this but this is killing me.

---

### Post by taurus on 2007-01-13
What's the output of this command from a terminal again?

```
sudo fdisk -l
```

---

### Post by violin on 2007-01-13
kemanci@kemanci-laptop:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4771    38323026   83  Linux
/dev/hda2            4772        4864      747022+   5  Extended
/dev/hda5            4772        4864      746991   82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    7  HPFS/NTFS
kemanci@kemanci-laptop:~$

---

### Post by taurus on 2007-01-13
Somehow your /dev/sdb1 changed to /dev/sda1 and /dev/mmcblk0p1 completely disappeared!  Therefore, you need to change /dev/sdb1 to /dev/sda1 in /etc/fstab and remove the /dev/mmcblk0p1 entry completely.  Now, see if you can mount it, /dev/sda1, again.

---

### Post by violin on 2007-01-13
kemanci@kemanci-laptop:~$ sudo mount -a
mount: mount point /media/sda1 does not exist
kemanci@kemanci-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              36G  9.0G   26G  27% /
varrun                125M   68K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
procbususb             10M  148K  9.9M   2% /proc/bus/usb
udev                   10M  148K  9.9M   2% /dev
devshm                125M     0  125M   0% /dev/shm
lrm                   125M   18M  108M  14% /lib/modules/2.6.17-10-generic/volatile
**/dev/scd0              20M   20M     0 100% /media/cdrom-1** interesting that is the new harddisk
kemanci@kemanci-laptop:~$


kemanci@kemanci-laptop:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4771    38323026   83  Linux
/dev/hda2            4772        4864      747022+   5  Extended
/dev/hda5            4772        4864      746991   82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    7  HPFS/NTFS
kemanci@kemanci-laptop:~$ 


kemanci@kemanci-laptop:~$ sudo fdisk -l | grep NTFS
/dev/sda1               1       30401   244196001    7  HPFS/NTFS
kemanci@kemanci-laptop:~$

---

### Post by violin on 2007-01-13
any help??

---

### Post by taurus on 2007-01-13
Try this!

```
sudo mkdir /media/sda1
sudo mount -t ntfs /dev/sda1 /media/sda1 -o nls=utf8,umask=0222
df -h
```

---

### Post by violin on 2007-01-13
thanks this one works fine...

but other harddisk i still dont understand why it is look like CD icon it is external hardisk and it is 400 GB.

kemanci@kemanci-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              36G  9.4G   25G  28% /
varrun                125M   68K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
procbususb             10M  148K  9.9M   2% /proc/bus/usb
udev                   10M  148K  9.9M   2% /dev
devshm                125M     0  125M   0% /dev/shm
lrm                   125M   18M  108M  14% /lib/modules/2.6.17-10-generic/volatile
/dev/sdb1             233G  158G   76G  68% /media/sdb1
**/dev/scd0              20M   20M     0 100% /media/cdrom-1** 


/dev/sda1 changed /dev/sdb1  but i manage to mount it. the problem is the other one.

---

### Post by taurus on 2007-01-13
Beats me!

---

### Post by violin on 2007-01-13
:D  i have no idea either. I think i gonna uninstall ubuntu because everything is in my harddisk. I tried to the to the read write thing that did not worked either. I dunno what to do?

but thanks for everything.

---

