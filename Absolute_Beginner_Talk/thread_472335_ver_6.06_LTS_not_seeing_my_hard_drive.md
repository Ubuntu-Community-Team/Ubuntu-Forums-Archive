---
title: "ver 6.06 LTS not seeing my hard drive"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by gasnmyveins on 2007-06-12
I ran the cd and can run Ubuntu from it. However, it isn't seeing my HD, so I can't install it. It doesn't show up when I look in the system section of ubuntu. I'm sure it's something simple, but I know just about nothing regarding computers. If someone can give me a little advice, it would be much appreciated.
 Some of the specs: 320gb internal HD. Athlon xp 1600+. Gigabyte 7dxr. 1 gb memory.
 I also have a 40 gb drive with windows on it hooked up as a slave, and it's not seeing that one, either.

---

### Post by Najand on 2007-06-13
Open a termianl and type:
```

sudo fdisk -l

```Then copy and paste it here.

---

### Post by gasnmyveins on 2007-06-13
This will be tough. I'm posting using our laptop and having the install problem on the tower, which is not yet online. I'll be entering everything here by hand and trying to be sure I get it all right.
 Also, the disk I am trying to install to has the NTSF partition with about 10 gigs of pictures on it. I'd like to save them if I could, even though I burned them to DVD before my other drive with WinXP crashed.
 Here's what happened. The # sign in line 2 of the usages section is used to represent a symbol my keyboard does not have which looks like a capital T with the right hand side of the top bar dropped to the bottom. Sorry.

 fdisk: invalid option -- 1

Usages: fdisk [-b SSZ] [-u] DISK          Change partition table
              fdisk -# [-b SSZ] [-u] DISK     List partition tables(s)
              fdisk -s PARTITION                Give partition sizes in blocks
              fdisk -v
Here DISK is something like /dev/hdb or /dev/sda and PARTITION is something like /dev/hda7
-u: give start and end in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
ubuntu@ubuntu:~$

---

### Post by gasnmyveins on 2007-06-13
Doh!!!!!!! I just missed something simple. I switched the hard drives for the install and didn't get the power plugged into the drive all the way. #-o

 On the other hand, it seems to be resizing my partition now. ;)  How long should that take, anyhow? I'm freeing up about 160 gigs on a 320 gig drive, with 10 gigs of pictures on it. Thanks.

---

