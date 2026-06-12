---
title: "Partitioning question"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by emkersyt on 2006-10-03
Hi everybody,

I´ve got a (newbie-)question about partitioning harddrives with Linux-utilities. 
I have OSX and Linux (Ubuntu) installed on my powerbook. For this purpose I made varios partitions - one of them was intended as an data-exchange-partition between the two systems. I formatted this as an UFS-partition but after some google-research I found out that it´s much better using either HFS+ or ext2.
I tried to reformat it with Disk-utility from OSX but it tells me that all partitions are going to be erased and the data becomes lost. 
Anybody knows if this is the same with Linux using fdisk or mac-fdisk? Can I reformat just one particuliar partition without affecting the other ones, even if they are logical partitions of an extended one?

---

### Post by sonny on 2006-10-03
In linux you can install gparted, it's easy to use and very straightforward to understand.
```
sudo apt-get install gparted
```

---

### Post by emkersyt on 2006-10-04
Thanks. The first part worked well so far. 
I erased the UFS-Partition and both systems were still untouched.
Just now I have some troubble to mount the new hfs partition I made.

gparted refused to format hfs+ (just hfs with a max. size of about 2G and others like ext2 etc) so I tried out mac-fdisk. This seemed to work but now neither OSX nor Ubuntu recognizes this partition any more.

This is what mac-fdisk shows (where /dev/hda5 is the problematic one)

[HTML]/dev/hda
        #                    type name                  length   base      ( size )  system
/dev/hda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/hda2         Apple_UNIX_SVR2 swap                  488282 @ 95486072  (238.4M)  Linux swap
/dev/hda3               Apple_HFS Apple_HFS_Untitled_2  32134896 @ 262208    ( 15.3G)  HFS
/dev/hda4              Apple_Boot eXternal booter        17408 @ 32397104  (  8.5M)  Unknown
/dev/hda5               Apple_HFS OSXhome             63071560 @ 32414512  ( 30.1G)  HFS
/dev/hda6         Apple_UNIX_SVR2 linux               15625001 @ 95974354  (  7.5G)  Linux native
/dev/hda7         Apple_UNIX_SVR2 home                44702133 @ 111599355 ( 21.3G)  Linux native
/dev/hda8         Apple_Bootstrap untitled              262144 @ 64        (128.0M)  NewWorld bootblock

Block size=512, Number of Blocks=156301488
DeviceType=0x0, DeviceId=0x0[/HTML]

I tried to mount it but the normal mount -t didn't work:

[HTML]root@kvlarsylix:~# mount -t hfs /dev/hda5 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/hda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/HTML]


Then I found out about this which seems to be the hfs-mount:

[HTML]root@kvlarsylix:~# hmount /dev/hda5 5
hmount: /dev/hda5: invalid partition map (Invalid argument)
[/HTML]

So I tried also this

[HTML]root@kvlarsylix:/dev# hformat -l "OSXhome" /dev/hda5 5
hformat: /dev/hda5: invalid partition map (Invalid argument)[/HTML]

because I thought I´d remember that one has got to kind of introduce the new partition to the system.



Don't know really what to do next to get this partition working. Do I have to edit the partition-table somehow? Or should there happen some other process after formatting before mounting ?

---

