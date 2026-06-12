---
title: "FreeBSD harddisk mount issues"
date: 2008-07-09
forum: BSD
---

### Post by disappearedng on 2008-07-09
Hi everyone,
 The following is what my fdisk editor shows under sysinstall
 
```

Disk name:      ad4                                    FDISK Partition Editor
DISK Geometry:  60801 cyls/255 heads/63 sectors = 976768065 sectors (476937MB)

Offset       Size(ST)        End     Name  PType       Desc  Subtype    Flags

         0         63         62        -     12     unused        0
        63   90188847   90188909    ad4s1      8    freebsd      165
  90188910  122865120  213054029    ad4s4      8    freebsd      165
 213054030  763714035  976768064    ad4s2      8    freebsd      165
 976768065       5103  976773167        -     12     unused        0

```
My freebsd Partition is located under ad4s4.
 ad4s1 and ad4s2 are just empty partitions.
 
 When I boot up, I get the following:
```

 F1: FreeBSD
 F2: FreeBSD
 F4: FreeBSD

```

 How do I disable both F1 and F2 in the boot menu? I tried using boot0cfg but failed miserably, 
 under man boot0cfg
 
Code:
To enable just slices 1 and 2 in the menu:
boot0cfg -m 0x3 ad0
So if I just want the boot menu to have just F4, is the following correct?
 
```

boot0cfg -m 0x1 ad4
or 
boot0cfg -m 0x8 ad4

```
2nd Problem
 How do I mount ad4s1 and ad4s2 under /usr?
 please look at what I did:
 
```

[disappearedng@ /]$ cd /usr
[disappearedng@ /usr]$ ls
X11R6   bin     compat  games   home    include lib     libdata libexec local   mount   obj     ports   sbin    share   src
[disappearedng@ /usr]$ cd mount/
[disappearedng@ /usr/mount]$ ls
350gb   50gb
[disappearedng@ /usr/mount]$ mount /dev/ad4
ad4     ad4s1   ad4s1c  ad4s2   ad4s2c  ad4s4   ad4s4a  ad4s4b  ad4s4c  ad4s4d  ad4s4e  ad4s4f  
[disappearedng@ /usr/mount]$ sudo mount /dev/ad4s1 50gb/
Password:
mount: /dev/ad4s1 : Invalid argument
[disappearedng@ /usr/mount]$ sudo mount /dev/ad4s2 350gb/
mount: /dev/ad4s2 : Invalid argument
[disappearedng@ /usr/mount]$

```
I looked up man mount and I just don't understand how this works.
 
 In addition, 
 How do I get FreeBSD to automatically mount when the system starts??
 
 Thx

---

### Post by disappearedng on 2008-07-10
Anyone??

---

### Post by Bachstelze on 2008-07-11
Your partitioning scheme is wrong. You should have only one FreeBSD partition, and then divide it into slices using disklabel. I guess the best would be to reinstall if you can afford it, it's going to be *very* cumbersome otherwise.

---

