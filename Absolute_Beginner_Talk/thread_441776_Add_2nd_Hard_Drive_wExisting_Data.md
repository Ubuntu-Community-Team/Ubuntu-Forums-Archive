---
title: "Add 2nd Hard Drive w/Existing Data"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by homerj742 on 2007-05-12
Hey guys, I'm running Dapper on my new server. 

Hard drive 1 - 20GB - Operating System (Ubuntu 6.06 LTS)

Hard drive 2 - 200GB - Data - from another Ubuntu machine. 


How do I mount it, permanently?

---

### Post by taurus on 2007-05-12
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by homerj742 on 2007-05-12
```
Disk /dev/hda: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2385    19157481   83  Linux
/dev/hda2            2386        2491      851445    5  Extended
/dev/hda5            2386        2491      851413+  82  Linux swap / Solaris

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       24180   194225818+  83  Linux
/dev/hdb2           24181       24321     1132582+   5  Extended
/dev/hdb5           24181       24321     1132551   82  Linux swap / Solaris

```

hdb is the one I want to mount. It used to be a full on linux OS, now all I want is the data from it.

---

### Post by taurus on 2007-05-12
Edit /etc/fstab

```
sudo nano -Bw /etc/fstab
```
and add this line to the end of it.

```
/dev/hdb1   /media/hdb1   ext3   defaults   0   1
```
Save the change with <Ctrl>o and exit with <Ctrl>x.  Then, create a new mount point and mount it.

```
sudo mkdir /media/hdb1
sudo mount -a
df -h
```

---

### Post by homerj742 on 2007-05-12
I added this to Fstab

```
/dev/hdb1   /DATA/hdb1   ext3   defaults   0   1
```

however, when I run this:

```
sudo mkdir /DATA/hdb1
sudo mount -a
df -h
```

I get: ```
mkdir: cannot create directory `/data/hdb1': No such file or directory

```

???

Thank yor for your quick responses :)

---

### Post by drowner on 2007-05-12
> **homerj742 said:**
> I added this to Fstab

```
/dev/hdb1   /DATA/hdb1   ext3   defaults   0   1
```

however, when I run this:

```
sudo mkdir /DATA/hdb1
sudo mount -a
df -h
```

I get: ```
mkdir: cannot create directory `/data/hdb1': No such file or directory

```

???

Thank yor for your quick responses :)



Linux is case sensitive, remember!

DATA or data?

---

### Post by taurus on 2007-05-12
Can you post your /etc/fstab and this command here?

```
cat /etc/fstab
ls -la /
```

---

### Post by homerj742 on 2007-05-12
Here ya go!


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


/dev/hdb1   /DATA/hdb1   ext3   defaults   0   1

```

---

### Post by taurus on 2007-05-12
Try this.

```
sudo mkdir /DATA/hdb1
sudo mount -t ext3 /dev/hdb1 /DATA/hdb1
df -h
```

---

### Post by homerj742 on 2007-05-12
Crap, I'm still getting:

```
mkdir: cannot create directory `/DATA/hdb1': No such file or directory

```

---

### Post by taurus on 2007-05-12
Try this then.

```
sudo mkdir /media/hdb1
sudo mount -t ext3 /dev/hdb1 /media/hdb1
df -h
```

---

### Post by homerj742 on 2007-05-12
WELL! That certainly worked! Thank you very much for your help. Ubuntu community is fantastic. :)

---

### Post by taurus on 2007-05-12
I guess you may want to modify /etc/fstab and change /DATA/hdb1 to /media/hdb1 then so it will be mounted automatically to /media/hdb1 each time you boot.

By the way, I know why it didn't work before.  You first need to create /DATA and then you can create hdb1 under it.

```
sudo mkdir /DATA
sudo mkdir /DATA/hdb1
```

---

### Post by homerj742 on 2007-05-12
Oh i see! It's cool, all is well now, i'm going through the media path and things seem to be working great. I just got samba configured. 

Now off to proftp and Gnump3d :)

---

