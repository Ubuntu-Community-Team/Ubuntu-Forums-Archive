---
title: "Second HDD can not mount not removeable!!??"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by jgrabham on 2007-03-13
When I try to access my slave drive (a 20gb maxtor HDD) It says it is not removeabble so it can not mount it.  I have no Idea what mounting a drive means and of course its not removable its a hard drive!  How can I access it?  I can access the Master (a 3.5GB Maxtor drive) fine.

I am using ubuntu 6.06 dapper Drake

---

### Post by taurus on 2007-03-13
Can you post the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by jgrabham on 2007-03-13
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK    Change Partition table
          fdisk -l [-b SSZ] [-u] Disk   List Partition Table(s)
          fdisk -s PARTITION          Give Partition size(s) in blocks
          fdisk -v                           Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in Sector (instead of cylender) units
-b 2048: (for certain MO disks) use 2048-byte sectors


---------------------------------------------------------------------------------------------------------------------------------------

Hope that helps

---

### Post by taurus on 2007-03-13
That is a lower case letter l as in **l**arry.

```
sudo fdisk -l
```

---

### Post by jgrabham on 2007-03-13
ok says a load about the drive that works, then


Disk /dev/hdb: 20.4GB, 20480237568 bytes
255 heads, 63 sectors/track, 2489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

 Device boot     Start        End          Blocks       ID      System
/dev/hdb1            1           2489   19992861   83       Linux

---

### Post by taurus on 2007-03-13
So you want to mount /dev/hdb1 then.

Open a terminal and edit /etc/fstab

```
gksudo gedit /etc/fstab
```
Add this line to the end of it.

```
/dev/hdb1   /media/hdb1   ext3   defaults   0   1
```
Save it.  Then, create a new mount point and mount it.

```
sudo mkdir /media/hdb1
sudo mount -a
df -h
```
Now, if you want to write to it as a regular user, then I need to see the output of this command so I can show you how to change the ownership of /media/hdb1 from root to your login name.

---

### Post by jgrabham on 2007-03-13
What Do You Mean Create A New Mount Point?

---

### Post by taurus on 2007-03-13
If you want to mount a partition, you need to create a mount point for it.  Since you want to mount /dev/hdb1 to /media/hdb1, you need to create /media/hdb1 first or you won't be able to mount /dev/hdb1.  Therefore, /media/hdb1 is known as a mount point for /dev/hdb1 (or you can mount /dev/hdb1 to anywhere you want).  So, if you want to access /dev/hdb1, you have to access the mount point of it, /media/hdb1.

---

### Post by jgrabham on 2007-03-13
so how do I create a mount point

---

### Post by taurus on 2007-03-13
Run this from a terminal.

```
sudo mkdir /media/hdb1
```

---

### Post by jgrabham on 2007-03-13
OK done it


Thanks a lot

---

### Post by taurus on 2007-03-13
You can either mount /dev/hdb1 with this command or reboot.

```
sudo mount -a
```

---

### Post by jgrabham on 2007-03-13
OK how do I get permision to write to "this folder"

---

### Post by taurus on 2007-03-13
What is your login name then?  Post the output of this command here if you want.

```
id
```

---

### Post by bks on 2007-03-13
> **jgrabham said:**
> OK how do I get permision to write to "this folder"

Is your slave formatted to ext3?

---

### Post by jgrabham on 2007-03-13
uid=1000(james) gid=1000(james) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),106(lpadmin),110(scanner),112(admin),1000(james)

---

### Post by taurus on 2007-03-13
From a terminal, run

```
sudo chown -R james:james /media/hdb1
```
Now, you are the proud owner of /media/hdb1 so you can read, write, or delete whatever you want.

---

### Post by Danilo Leon on 2007-04-11
will this work if i have a windows os previously installed?

---

