---
title: "GRUB error 17"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by mouko on 2007-12-06
Anyone know what to do in this case?  Every boot stops with error "GRUB error 17."

---

### Post by PmDematagoda on 2007-12-06
This error usually comes when GRUB is unable to read the partition you are trying to boot from as it is an unknown format. As said [here.]("http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors")

Try using [Super GRUB]("http://supergrub.forjamari.linex.org/?section=download") to solve your problem.

---

### Post by mouko on 2007-12-06
I tried going through and entering the commands given on the Super Grub site, but "root (hd3, 0)" gives an error about cylinders.  I'm entering "root (hd0, 0)" because I don't have an hd3, so I hope I didn't just hose my drive.

---

### Post by mouko on 2007-12-06
I did an fdisk -l, and it looks like my hard drive is listed as sda.  Should I change hd3 to sda1, my linux partition?

---

### Post by PmDematagoda on 2007-12-06
Yes, if you do that, the problem should be fixed.

---

### Post by mouko on 2007-12-06
It won't take sda1.  It says "Error while parsing number."

---

### Post by PmDematagoda on 2007-12-06
Could you post what you get in the device.map file in the /boot/grub folder?

---

### Post by meierfra on 2007-12-06
Post the output of 

```
sudo fdisk -l
```

---

### Post by mouko on 2007-12-06
ubuntu@ubuntu:/dev$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9355    75144006   83  Linux
/dev/sda2            9356        9729     3004155    5  Extended
/dev/sda5            9356        9729     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 32 MB, 32587776 bytes
2 heads, 32 sectors/track, 994 cylinders
Units = cylinders of 64 * 512 = 32768 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?    12158374    29994462   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(12158373, 1, 5)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(29994461, 1, 3)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?     2635774    32886216   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(2635773, 1, 19)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(32886215, 0, 2)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?    29216898    59467339   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(29216897, 1, 26)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(59467338, 0, 25)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?           1    56831664  1818613248    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(56831663, 1, 32)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

---

### Post by mouko on 2007-12-06
> **PmDematagoda said:**
> Could you post what you get in the device.map file in the /boot/grub folder?

There is no /boot/grub folder.

---

### Post by PmDematagoda on 2007-12-06
Are you sure you looked in the Linux partition?

---

### Post by meierfra on 2007-12-06
Do this

```
sudo mkdir /ubuntu
sudo mount -t ext3  /dev/sda1 /ubuntu
cd /ubuntu/boot/grub
cat menu.lst
cat device.map

```

and post the output

---

### Post by mouko on 2007-12-06
It is probably looking in the CD file structure.  How do I change to my disk?

---

### Post by mouko on 2007-12-06
> **meierfra said:**
> Do this

```
sudo mkdir /ubuntu
sudo mount -t ext3  /dev/sda1 /ubuntu
cd /ubuntu/boot/grub
cat menu.lst
cat device.map

```

and post the output

ubuntu@ubuntu:~/Desktop$ sudo mount -t ext3 /dev/sda1 /ubuntu
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by meierfra on 2007-12-06
Try again, but leave out the "-t ext3"

---

### Post by mouko on 2007-12-06
ubuntu@ubuntu:~/Desktop$ sudo mount /dev/sda1 /ubuntu
mount: you must specify the filesystem type


This is not going to be good.  Man, all of my school data is sitting there, and I can't access it.

---

### Post by meierfra on 2007-12-06
Post the output of

 ```
sudo blkid
```

---

### Post by mouko on 2007-12-06
/dev/sda5: UUID="972aabf5-3c99-414d-aef4-afc23a4a46ba" TYPE="swap" 
/dev/sdb: SEC_TYPE="msdos" LABEL="LOCKANDLOAD" UUID="4C01-72A5" TYPE="vfat" 

sdb is the flashdrive I've got in right now.

---

### Post by mouko on 2007-12-06
So is sda5 my bootloader partition?

---

### Post by meierfra on 2007-12-07
sda 5 is your swap space it is  used then you ran out of memory. Your ubuntu partiton does not show up. So there is something wrong with your ubuntu partition.



You probably should run

```
sudo fsck  /dev/sda1
```

but I don't know much about "fsck". 


You might also see whether testdisk (see my signature) can detect your ubuntu partition and files

---

### Post by meierfra on 2007-12-07
Just fixed a typo in my previous post.

---

### Post by Presto123 on 2007-12-07
I haven't read through the whole thing but I would suggest downloading SuperGrub and attempting to get to it there. It's pretty easy to use.

I was having an error 21 so, it might not work for you, but it is worth a try. Error 21 basically is that it could not find my external which has part of the grub file that was necessary. I used SuperGrub to reset my MBR (Master Boot Record) so that it could auto load my Windoze.

I still have to use the disk after doing this when I want to use my external, but it's not a big deal for me. There is some way to fix this, but like I said, it's no big deal for me.

---

### Post by meierfra on 2007-12-07
> I haven't read through the whole thing but I would suggest downloading SuperGrub and attempting to get to it there. 

This has turned out to be  filesytem problem, not a grub problem.

---

### Post by mouko on 2007-12-07
Screw it, I'm reinstalling.

---

### Post by meierfra on 2007-12-07
Why? I though you had lots of data on it?  There is a good chance you can rescue it.

---

### Post by meierfra on 2007-12-07
> I still have to use the disk after doing this when I want to use my external, but it's not a big deal for me. There is some way to fix this, but like I said, it's no big deal for me.


You should not  have to use the disk.  If Supergrub can boot ubuntu,  I can show you how to boot it without Supergrub. Just start a new thread and I will help you.

---

### Post by PmDematagoda on 2007-12-07
Sorry for the absence, had to do some attempts at getting normal GNOME to work again on Ubuntu 8.04(I might add that they were failed:(), so could mouko please bring me up to par again?

So what have you tried to do mouko, what errors did you get?

---

### Post by meierfra on 2007-12-07
PmDematagoda:

> buntu@ubuntu:/dev$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

Device Boot Start End Blocks Id System
/dev/sda1 * 1 9355 75144006 83 Linux
/dev/sda2 9356 9729 3004155 5 Extended
/dev/sda5 9356 9729 3004123+ 82 Linux swap / Solaris

(dev/sdb is a flashdrive)

> sudo mount -t ext3 /dev/sda1 /ubuntu
mount: wrong fs type, bad option, bad superblock on /dev/sda1,

> 
sudo blkid
/dev/sda5: UUID="972aabf5-3c99-414d-aef4-afc23a4a46ba" TYPE="swap"
/dev/sdb: SEC_TYPE="msdos" LABEL="LOCKANDLOAD" UUID="4C01-72A5" TYPE="vfat" 

---

### Post by PmDematagoda on 2007-12-07
Hmm, ok, try:-

```
fsck -f /dev/sda1
```

---

### Post by mouko on 2007-12-07
Thanks for your help guys, but I just reinstalled.  I had a couple-day old backup of my school documents, so no big loss.  The biggest issue is going to be getting my music, programs, and settings back again.  And installing the Cisco VPN client.  I installed it before, but somebody had to run two commands to (reset it I think) make it work.  If you have any idea about this, I'm open.

---

