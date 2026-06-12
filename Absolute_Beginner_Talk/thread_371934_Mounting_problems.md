---
title: "Mounting problems"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by rabid9797 on 2007-02-27
im having trouble mounting all my drives(another ext3 and two ntfs drives) into ubuntu.
ive had this problem before, and it was temporarily fixed, but ive added a hardrive since then and im not sure what to do anymore.

here was my original thread: [http://ubuntuforums.org/showthread.php?t=353494](http://ubuntuforums.org/showthread.php?t=353494)


sudo fdisk -l gives me this:

```
Disk /dev/hda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3648    29302528+   7  HPFS/NTFS

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       27403   220114566   83  Linux
/dev/hdb2           27404       30251    22876560   83  Linux
/dev/hdb3           30252       30401     1204875   82  Linux swap / Solaris

Disk /dev/hdd: 61.4 GB, 61475807232 bytes
255 heads, 63 sectors/track, 7474 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        7191    57761676   83  Linux
/dev/hdd2            7192        7474     2273197+   5  Extended
/dev/hdd5            7192        7474     2273166   82  Linux swap / Solaris

```


I am trying to mount hda1, hdb1(which is ntfs, im not sure why it shows up as Linux), and hdd2.

when i try a simple mount command i get this:
```

$ sudo mount /dev/hdb1
mount: can't find /dev/hdb1 in /etc/fstab or /etc/mtab

```

i get the same error for hda1 and hdd2.

can someone(taurus helped me last time) help me with this?

---

### Post by taurus on 2007-02-27
Try this first from a terminal.

```
sudo mkdir /media/hdb1
sudo mount -t ntfs /dev/hdb1 /media/hdb1 -o nls=utf8,umask=0222
df -h
```

Does it work?

p.s.  You cannot mount /dev/hdd2 since it's an extended partition.  In other words, you don't mount extended partition.

---

### Post by annda on 2007-02-27
hmm, what does you /etc/fstab look like at the moment?

---

### Post by rabid9797 on 2007-02-27
> **taurus said:**
> Try this first from a terminal.

```
sudo mkdir /media/hdb1
sudo mount -t ntfs /dev/hdb1 /media/hdb1 -o nls=utf8,umask=0222
df -h
```

Does it work?

p.s.  You cannot mount /dev/hdd2 since it's an extended partition.  In other words, you don't mount extended partition.

that worked! im not sure why i have to go through this proccess everytime i do a clean install tho... =/ i'll keep this page bookmarked for future reference.

about, hdd2, i meant hdb2, i got a little confused there(hdd2 is my root partition :oops: )

[quote=annda]
hmm, what does you /etc/fstab look like at the moment?
[/quote]

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd1
UUID=ac85ec4c-906c-4b08-9ed0-2dfd0c8e5e0b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd5
UUID=24ba2e0d-4099-4ca9-9acf-607f951e4d34 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

thats after doing the commands taurus gave me.

---

### Post by taurus on 2007-02-27
In that case, edit /etc/fstab

```
sudo cp /etc/fstab  /etc/fstab.bak
gksudo gedit /etc/fstab
```
and add these lines to the end of it.

```
/dev/hdb1   /media/hdb1   ntfs   nls=utf8,umask=0222   0   0
/dev/hdb2   /media/hdb2   ext3   defaults   0   1
```
Save it.  Now, create a new mount point for /dev/hdb2.

```
sudo mkdir /media/hdb2
```
Then, reboot.  Your /dev/hdb1 should show up as /media/hdb1 and /dev/hdb2 should be on /media/hdb2 when you run this command after you log back in.

```
df -h
```

---

### Post by rabid9797 on 2007-02-27
that got hdb1 working :)  , but hdb2 still isn't showing up.

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/hdd1              55G  2.4G   50G   5% /
varrun                379M   80K  379M   1% /var/run
varlock               379M     0  379M   0% /var/lock
procbususb             10M  168K  9.9M   2% /proc/bus/usb
udev                   10M  168K  9.9M   2% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   18M  362M   5% /lib/modules/2.6.17-11-generic/volatile
/dev/hdb1             210G  176G   35G  84% /media/hdb1

```

(thanks for the help so far btw)

---

### Post by taurus on 2007-02-27
My bad.  I was in a hurry since I had to go to work.  It should have been /media/hdb2 in /etc/fstab.

```

/dev/hdb2   /media/hdb2   ext3   defaults   0   1

```

---

### Post by annda on 2007-02-27
i believe there was a typo in taurus's (excellent) instructions: he told you to mount (in fstab) hdb2 to hdb3, but the mountpoint was hdb2.

if you followed the instruction step-by-step you might have missed that.

ckech you fstab and correct it if needed.

---

