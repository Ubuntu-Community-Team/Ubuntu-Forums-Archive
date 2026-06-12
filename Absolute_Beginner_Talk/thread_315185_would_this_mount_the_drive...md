---
title: "would this mount the drive.."
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by Captain Kirk76 on 2006-12-08
would this command mount the drive i ask.
```

sudo mount dev/hdd4

```

Because it doesn't :(

Also, at start up, Ubuntu mounts four partitions, but 2 it doesnt, why is this? (I am trying to mount one now, but it won't let me)

---

### Post by riven0 on 2006-12-08
> **Captain Kirk76 said:**
> would this command mount the drive i ask.
```

sudo mount dev/hdd4

```

Because it doesn't :(

Also, at start up, Ubuntu mounts four partitions, but 2 it doesnt, why is this? (I am trying to mount one now, but it won't let me)

Captain Kirk, try this: sudo mount dev/hdd4 /media

then check the /media folder and see if it's there.

---

### Post by Captain Kirk76 on 2006-12-08
Thanks for the reply, when i type
```
sudo mount dev/hdd4 /media
```
i get this error
> mount: you must specify the filesystem type

---

### Post by taurus on 2006-12-08
```
sudo mkdir /media/share
sudo  mount  /dev/hdd4  /media/share
```
If two partitions don't mount, then there is something wrong with /etc/fstab so paste it here...

```
cat /etc/fstab
```
p.s.  Make sure you have the mount points too...

---

### Post by Captain Kirk76 on 2006-12-08
Hi, here is the fstab info. I have just re-checked, there is 1 partition that doesnt mount, the other 3 is CD/DVD drives, and a FLoppy drive.


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdd2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc1       /media/hdc1     ntfs    defaults,nls=utf8,umask=007,gid=46 0                                                                     1
/dev/hdc5       /media/hdc5     ntfs    defaults,nls=utf8,umask=007,gid=46 0                                                                     1
/dev/hdd4       /www            vfat    defaults,utf8,umask=007,gid=46,automount                                                              ,autofs 0       1
/dev/hdd5       /media/hdd5     ntfs    defaults,nls=utf8,umask=007,gid=46 0                                                                     1
/dev/hdd6       /media/hdd6     ntfs    defaults,nls=utf8,umask=007,gid=46 0                                                                     1
/dev/hdd3       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by riven0 on 2006-12-08
Hmmm, perhaps he should install ivman? When I started using e17 I had problems mounting my external hard drive, but ivman took care of all that.

---

### Post by taurus on 2006-12-08
Can you at least give us a hint which one doesn't mount but I bet it is the /dev/hdd4???

Otherwise, what is the output of this command then?

```
df -h
```

---

### Post by Captain Kirk76 on 2006-12-08
> **taurus said:**
> ```
sudo mkdir /media/share
sudo  mount  /dev/hdd4  /media/share
```


I now get this error when accessing it.
You do not have the permissions necessary to view the contents of "share".

EDIT: yes its hdd4 that doesnt automount

---

### Post by Captain Kirk76 on 2006-12-08
results of df -h

Filesystem            Size Used Avail Use% Mounted on
/dev/hdd2              39G  5.3G   32G  15% /
varrun                252M   88K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  144K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M  9.3M  243M   4% /lib/modules/2.6.15-27-386/volatile
/dev/hdc1              49G   19G   31G  39% /media/hdc1
/dev/hdc5              28G  1.3G   27G   5% /media/hdc5
/dev/hdd5              64G  2.8G   62G   5% /media/hdd5
/dev/hdd6             101G   29G   72G  29% /media/hdd6
/dev/hdd4              27G  601M   26G   3% /media/share

---

### Post by taurus on 2006-12-08
You need to edit /etc/fstab and modify the entry for /dev/hdd4 to look like this!

```

/dev/hdd4       /www         vfat    defaults,utf8,umask=007,gid=46,automount,autofs   0       1

```
You have a bunch of extra spaces between "automount" and ",auofs"...

Then, see if you can mount it now with

```
sudo umount /dev/hdd4
sudo mount -a
df -h
```

---

### Post by Captain Kirk76 on 2006-12-08
I now get

mount: /dev/hdd4 already mounted or /www busy
mount: according to mtab, /dev/hdd4 is mounted on /media/share

---

### Post by taurus on 2006-12-08
Did you unmount it first before you run the second command?

```
sudo umount /dev/hdd4
sudo mount -a
```
Otherwise, what is the output of this command then?

```
df -h
```

---

### Post by Captain Kirk76 on 2006-12-08
> **taurus said:**
> Did you unmount it first before you run the second command?

```
sudo umount /dev/hdd4
sudo mount -a
```


After typing that i get

adam@Adams-Computer:~$ sudo umount /dev/hdd4
adam@Adams-Computer:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hdd4,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

After running that, i get this for df -h

Filesystem            Size Used Avail Use% Mounted on
/dev/hdd2              39G  5.3G   32G  15% /
varrun                252M   88K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  144K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M  9.3M  243M   4% /lib/modules/2.6.15-27-386/volatile
/dev/hdc1              49G   19G   31G  39% /media/hdc1
/dev/hdc5              28G  1.3G   27G   5% /media/hdc5
/dev/hdd5              64G  2.8G   62G   5% /media/hdd5
/dev/hdd6             101G   29G   72G  29% /media/hdd6

---

### Post by taurus on 2006-12-08
Are you sure /dev/hdd4 is fat32 since everything else is ntfs???  What's the output of this command then?

```
sudo fdisk -l
```

---

### Post by Captain Kirk76 on 2006-12-08
HDD4 is NTFS like everything else, except the linux drives, i am merely wanting to mount it to retrieve audio files, and several other files from it.

also the results of  sudo fdisk-|
Disk /dev/hdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/hdc2            6375        9964    28836675    f  W95 Ext'd (LBA)
/dev/hdc5            6375        9964    28836643+   7  HPFS/NTFS

Disk /dev/hdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               2       21488   172594327+   f  W95 Ext'd (LBA)
/dev/hdd2           21489       26690    41785065   83  Linux
/dev/hdd3           26691       26951     2096482+  82  Linux swap / Solaris
/dev/hdd4           26952       30401    27712125    7  HPFS/NTFS
/dev/hdd5               2        8355    67103473+   7  HPFS/NTFS
/dev/hdd6            8356       21488   105490791    7  HPFS/NTFS

---

### Post by taurus on 2006-12-08
Real funny!!!  Your /dev/hdd4 is ntfs, not fat32/vfat!!!

```
/dev/hdd4 26952 30401 27712125 7 HPFS/NTFS
```

Therefore, you need to modify your /etc/fstab and change vfat to ntfs for the /dev/hdd4's entry...

---

### Post by Captain Kirk76 on 2006-12-08
I have never edited that file previous to this, that is the file Ubuntu configured itself at install, why would it make such a mistake?

---

### Post by Captain Kirk76 on 2006-12-08
oh, and how do i mount the drive now i fixed that?

---

### Post by taurus on 2006-12-08
Who knows.  Now that we know what filesystem /dev/hdd4 is, just make the change and you shouldn't see any error message about wrong filesystem...

```
gksudo  gedit  /etc/fstab
```

p.s.  Try
```
sudo mount -a
df -h
```

---

### Post by Captain Kirk76 on 2006-12-08
sudo mount -a
df -h 

==

adam@Adams-Computer:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hdd4,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

adam@Adams-Computer:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/hdd2              39G  5.3G   32G  15% /
varrun                252M   88K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  144K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M  9.3M  243M   4% /lib/modules/2.6.15-27-386/volatile
/dev/hdc1              49G   19G   31G  39% /media/hdc1
/dev/hdc5              28G  1.3G   27G   5% /media/hdc5
/dev/hdd5              64G  2.8G   62G   5% /media/hdd5
/dev/hdd6             101G   29G   72G  29% /media/hdd6

---

### Post by taurus on 2006-12-08
Can I have a look at your /etc/fstab again?

```
cat /etc/fstab
```
Otherwise, mount it by hand with

```
sudo  mount   -t  ntfs  /dev/hdd4  /media/share  -o  umask=0222
df -h
```

---

### Post by Captain Kirk76 on 2006-12-08
etc/fstab =

Filesystem            Size Used Avail Use% Mounted on
/dev/hdd2              39G  5.3G   32G  15% /
varrun                252M   88K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  144K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M  9.3M  243M   4% /lib/modules/2.6.15-27-386/volatile
/dev/hdc1              49G   19G   31G  39% /media/hdc1
/dev/hdc5              28G  1.3G   27G   5% /media/hdc5
/dev/hdd5              64G  2.8G   62G   5% /media/hdd5
/dev/hdd6             101G   29G   72G  29% /media/hdd6
adam@Adams-Computer:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdd2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc1       /media/hdc1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdc5       /media/hdc5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdd4       /www         ntfs    defaults,utf8,umask=007,gid=46,automount,autofs   0       1
/dev/hdd5       /media/hdd5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdd6       /media/hdd6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdd3       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
adam@Adams-Computer:~$

---

### Post by taurus on 2006-12-08
Try to make the entry for /dev/hdd4 to look like this then!

```

/dev/hdd4  /media/hdd4  ntfs   defaults,nls=utf8,umask=007,gid=46  0  1

```
Then, run

```
sudo mkdir /media/hdd4
sudo mount -a
df -h
```

---

### Post by Captain Kirk76 on 2006-12-08
sudo mkdir /media/hdd4
sudo mount -a
df -h

===========


adam@Adams-Computer:~$ sudo mkdir /media/hdd4
mkdir: cannot create directory `/media/hdd4': File exists
adam@Adams-Computer:~$ sudo mount -a
adam@Adams-Computer:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/hdd2              39G  5.3G   32G  15% /
varrun                252M   88K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  144K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M  9.3M  243M   4% /lib/modules/2.6.15-27-386/volatile
/dev/hdc1              49G   19G   31G  39% /media/hdc1
/dev/hdc5              28G  1.3G   27G   5% /media/hdc5
/dev/hdd5              64G  2.8G   62G   5% /media/hdd5
/dev/hdd6             101G   29G   72G  29% /media/hdd6
/dev/hdd4              27G  601M   26G   3% /media/hdd4

---

### Post by taurus on 2006-12-08
```
/dev/hdd4  27G 601M  26G  3%  /media/hdd4
```
You've got your /media/hdd4!!!  \\:D/

---

### Post by Captain Kirk76 on 2006-12-08
Awesome, Thanks alot!

---

