---
title: "formatting external hd as ext3"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by ZeroPain on 2007-04-18
```
justin@ubuntu:~$ mkfs.ext3 –L /justinext /dev/sdc1
mke2fs 1.40-WIP (14-Nov-2006)
mkfs.ext3: invalid blocks count - /justinext
justin@ubuntu:~$ 

```

I was trying to reformat my external hard drive by following this guide:
[http://www.yourdevconnection.com/dev-tutorials/partition-format-and-mount-a-secondary-hard-drive-in-linux.html](http://www.yourdevconnection.com/dev-tutorials/partition-format-and-mount-a-secondary-hard-drive-in-linux.html)

Everything was working fine until I got the above error. I don't understand why its saying invalid blocks count when I did not enter anything of the sort.

Thanks in Advance

---

### Post by taurus on 2007-04-18
```
sudo mke2fs -j /dev/sdc1
```

---

### Post by ZeroPain on 2007-04-18
```
Could not stat /dev/sdc1 --- No such file or directory

The device apparently does not exist; did you specify it correctly?

```
...

---

### Post by aktiwers on 2007-04-18
Is there a reason you want to use the Terminal for this?
You could use gparted. If its installed open it by typing: ```
gparted
```

And if not, install by typing:
```
sudo apt-get install gparted
```

Good luck!

---

### Post by bodhi.zazen on 2007-04-18
I think the problem with that command is the / in front of justinext

Try this : ```
mkfs.ext3 –L justinext /dev/sdc1
```

---

### Post by ZeroPain on 2007-04-18
> **aktiwers said:**
> Is there a reason you want to use the Terminal for this?
You could use gparted. If its installed open it by typing: ```
gparted
```

And if not, install by typing:
```
sudo apt-get install gparted
```

Good luck!

I was not aware of gparted...

I now have a new problem...

Whenever I attempt an action the disk remounts...
Thus not allowing me to do the action..

---

### Post by taurus on 2007-04-18
Unmount it first before you can format it.  Assuming it's /dev/sdc1, do

```
sudo umount /dev/sdc1
```

---

### Post by ZeroPain on 2007-04-18
> **taurus said:**
> Unmount it first before you can format it.  Assuming it's /dev/sdc1, do

```
sudo umount /dev/sdc1
```

gparted does not display it as sdc1...

For some reason it remounts when I try and create a new partition.

I have attached the details file...

---

### Post by taurus on 2007-04-18
What's the output of this command then?

```
sudo fdisk -l
```

---

### Post by ZeroPain on 2007-04-18
> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30119   241930836   83  Linux
/dev/sda2           30120       30401     2265165    5  Extended
/dev/sda5           30120       30401     2265133+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux
justin@ubuntu:~$ 


The 80 GB drive is the one I want to format.

---

### Post by taurus on 2007-04-18
It's /dev/sdb1, not /dev/sdc1.

```
sudo mkdir /media/sdb1
sudo mount -t ext3 /dev/sdb1 /media/sdb1
```

---

### Post by ZeroPain on 2007-04-18
```
sudo mkdir /media/sdb1
mkdir: cannot create directory `/media/sdb1': File exists

```

```
sudo mount -t ext3 /dev/sdb1 /media/sdb1
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

:confused:

---

### Post by bodhi.zazen on 2007-04-19
Well, did you format the partition (drive) ?

---

