---
title: "Corrupt external HD, need help to recover photos"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by emband on 2007-05-01
Hello I have a external HD with my photos on it, and now I my disk will not auto mount.
I'm think that my disk has crashed, but if there are some posiblities to recover at least some of my files that would be great.

The disk has the ext3 filesystem and i find it at /dev/sdb1

I'm using feisty

I tried to run the fsck

 sudo fsck -t ext3 /dev/sdb1
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: No such file or directory while trying to open /dev/sdb1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


I'm I able to recover some of my files? Or can I just  throw the disk out the window

---

### Post by oilchangeguy on 2007-05-01
do you have another computer you can test the drive with?

---

### Post by taurus on 2007-05-01
Turn on that external harddrive and plug it in to your machine.  Then, open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by emband on 2007-05-01
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2   *          11        1922    15358140    7  HPFS/NTFS
/dev/sda3            6937        7295     2883667+  db  CP/M / CTOS / ...
/dev/sda4            1923        6936    40274955    5  Extended
/dev/sda5            1923        6665    38098116   83  Linux
/dev/sda6            6666        6936     2176776   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux

---

### Post by taurus on 2007-05-01
Try

```
sudo mkdir /media/sdb1
sudo mount -t ext3 /dev/sdb1 /media/sdb1
df -h
```

---

### Post by emband on 2007-05-01
I have tried it it on Windows XP with that fs driver thing and i got a message it was corrupted.

---

### Post by emband on 2007-05-01
anders@anders-dell:~$ sudo mount -t ext3 /dev/sdb1 /media/sdb1
mount: special device /dev/sdb1 does not exist

---

### Post by taurus on 2007-05-01
```
sudo fsck /dev/sdb1
```

---

### Post by emband on 2007-05-01
anders@anders-dell:~$ sudo fsck /dev/sdb1
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
fsck.ext2: No such file or directory while trying to open /dev/sdb1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

---

### Post by smario on 2007-05-01
have you tried gnu ddrescue? It worked for me. I had a notebook hdd in an external enclosure that went all haywire and used ddrescue to recover the data. Beware though. It didnt work when I tried to use it while in an external enclosure for some reason. I hooked it up to the an IDE cable with a converter and ran ddrescue. It got most of the data I was looking for back.

try it and let me know.

Mario

---

### Post by oilchangeguy on 2007-05-01
can't help with the drive problem. but i do suggest if you can recover the pics that you create an account with aol's x-drive. you'll get 5gb of free storage.

---

### Post by emband on 2007-05-01
> **smario said:**
> have you tried gnu ddrescue? It worked for me. I had a notebook hdd in an external enclosure that went all haywire and used ddrescue to recover the data. Beware though. It didnt work when I tried to use it while in an external enclosure for some reason. I hooked it up to the an IDE cable with a converter and ran ddrescue. It got most of the data I was looking for back.

try it and let me know.

Mario

just to be sure is this something you used? 
[http://www.dansdata.com/rdriver.htm](http://www.dansdata.com/rdriver.htm)

---

### Post by BHelts on 2007-05-01
as an aside.  the more you try to mount the drive, the more the drive spins, the less likely it will be to recover your pictures in the event that the hard drive is going bad, or is bad.  But it may just be the hard drive controller in the enclosure.  try an IDE to USB conversion cable without the enclosure and see if that works by bypassing the enclosure controller.

---

### Post by Josey on 2007-05-01
> **emband said:**
> just to be sure is this something you used? 
[http://www.dansdata.com/rdriver.htm](http://www.dansdata.com/rdriver.htm)

I think what he did was take the drive out the the usb enclosure and hook it up normally.
If you have no room on your motherboard just use the cdrom IDE cable temporarily.

Your hard drive is likely just an IDE drive.  The usb enclosure does IDE to USB.

Assuming we arent talking about a flash drive...

---

### Post by emband on 2007-05-01
no we are not talking about a flash drive but a 3,5 HD and i have a dell inspiron 9200 laptop. So  I have to use somthing like a ide to usb cable or something, never used that before so it is quite new to me.

---

### Post by oilchangeguy on 2007-05-01
> **emband said:**
> no we are not talking about a flash drive but a 3,5 HD and i have a dell inspiron 9200 laptop. So  I have to use somthing like a ide to usb cable or something, never used that before so it is quite new to me.
there are adapter cables available to use a laptop drive in a desktop.(you can try this to test it) they're available on ebay, [http://cgi.ebay.com/2-5-to-3-5-IDE-Hard-Drive-Cable-Adapter-Laptop-to-PC_W0QQitemZ160004897765QQihZ006QQcategoryZ32825QQrdZ1QQssPageNameZWD1VQQcmdZViewItem](http://cgi.ebay.com/2-5-to-3-5-IDE-Hard-Drive-Cable-Adapter-Laptop-to-PC_W0QQitemZ160004897765QQihZ006QQcategoryZ32825QQrdZ1QQssPageNameZWD1VQQcmdZViewItem)
ah, i see the drive is 3.5 (it helps to read carefully before you post) do you have a desktop computer you can install it in as a slave drive to test it?

---

