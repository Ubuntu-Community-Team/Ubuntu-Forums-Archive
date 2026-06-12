---
title: "Feisty dosen't detect my NTFS partition!"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by eoghanmurray on 2007-05-28
I have two hard disks; one internal (NTFS) which is detected, and one external:

sdb1: Linux EXT3 (my Ubuntu installation)
sdb2: Linux swap
sdb3: NTFS **<<This one is not detected!**

Please help! I've got about 200GB of important files on that partition and I really would like to access them via Ubuntu.

Thanks in advance for all your help.

---

### Post by eapache on 2007-05-28
In what way is it not detected? Is it just not on your desktop/places menu, or is it not even in Places > Computer? Try the following three comands:

```

cd /media
sudo mkdir sdb3
sudo mount sdb3 sdb3

```

---

### Post by taurus on 2007-05-28
Can you post

```
sudo fdisk -l
```

---

### Post by eoghanmurray on 2007-05-28
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9518    76453303+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12158    97659103+  83  Linux
/dev/sdb2           12159       12462     2441880   82  Linux swap / Solaris
/dev/sdb3           12463       60801   388283017+   7  HPFS/NTFS

---

### Post by taurus on 2007-05-28
Try

```
sudo mkdir /media/sdb3
sudo mount -t ntfs /dev/sdb3 /media/sdb3 -o nls=utf8,umask=0222
df -h
```

---

### Post by eoghanmurray on 2007-05-28
What I got:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              92G  5.0G   83G   6% /
varrun                379M  104K  378M   1% /var/run
varlock               379M     0  379M   0% /var/lock
procbususb            379M  128K  378M   1% /proc/bus/usb
udev                  379M  128K  378M   1% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   33M  346M   9% /lib/modules/2.6.20-16-generic/volatile
/dev/disk/by-uuid/76C86826C867E2BB
                       73G   30G   44G  41% /media/sda1

---

### Post by taurus on 2007-05-28
Any error message when you try to mount /dev/sdb3?

```
sudo mount -t ntfs /dev/sdb3 /media/sdb3 -o nls=utf8,umask=0222
```

---

### Post by eoghanmurray on 2007-05-28
sudo mount -t ntfs /dev/sdb3 /media/sdb3 -o nls=utf8,umask=0222

---

### Post by taurus on 2007-05-28
> **eoghanmurray said:**
> sudo mount -t ntfs /dev/sdb3 /media/sdb3 -o nls=utf8,umask=0222

Yes.  Type that whole thing in from a terminal and see if you get any error message.

---

### Post by eoghanmurray on 2007-05-28
Sorry, pasted wrong thing.

Result:
```
mount: /dev/sdb3 already mounted or /media/sdb3 busy
mount: according to mtab, /dev/sdb3 is already mounted on /media/sdb3

```

---

### Post by taurus on 2007-05-28
What's the output of this command then?

```
df -h
```

---

### Post by eoghanmurray on 2007-05-28
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              92G  5.0G   83G   6% /
varrun                379M  104K  378M   1% /var/run
varlock               379M     0  379M   0% /var/lock
procbususb            379M  128K  378M   1% /proc/bus/usb
udev                  379M  128K  378M   1% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   33M  346M   9% /lib/modules/2.6.20-16-generic/volatile
/dev/disk/by-uuid/76C86826C867E2BB
                       73G   30G   44G  41% /media/sda1

---

### Post by eoghanmurray on 2007-05-29
I thought I had it working there are a while, but alas, nothing.

---

### Post by Inxsible on 2007-05-29
Since its an external drive, you should use pmount
First remove the folder that you created earlier
```
 sudo rmdir /media/sdb3
```
You will have to remove the drive to do that
 
after that
```
 sudo pmount /dev/sdb3 MyNTFSDrive 
```
 
You can of course give any name you like. The drive will be mounted under /media/<name that you gave>

---

### Post by eoghanmurray on 2007-06-14
for that first command I got:

```
rmdir: /media/sdb3: Device or resource busy
```

For the second command i got

```
Warning: device /dev/sdb3 is already handled by /etc/fstab, supplied label is ignored
fusermount: failed to access mountpoint /media/disk-o: No such file or directory
FUSE mount point creation failed
Unmounting /dev/sdb3 (eoghan500gb)

```

---

