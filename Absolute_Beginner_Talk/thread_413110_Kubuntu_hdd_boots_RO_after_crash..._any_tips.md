---
title: "Kubuntu hdd boots RO after crash... any tips?"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by acodring on 2007-04-18
I just got an old PII 400 running as a Mythfrontend and was quite pleased with myself as I watched a playoff hockey game...

Then I got overconfident and asked the machine to copy a bunch of files to another machine at the same time.

The machine froze and I resorted to a hard reset.

Now it won't boot into X and leaves me at a command prompt. I can't do much since it complains about the disk being mounted read only if I try to save files, view a man page (can't create temp...), etc.

Some random relevant details to fill in a few gaps, please ask if you need more info:

Kubuntu Edgy 6.10 (writing this thanks to the LiveCD)

12GB HDD, autoformatted by kubuntu /dev/hda

I can mount /dev/hda1 as ext3 and see home and other directories
ubuntu@ubuntu:~$ dmesg | grep hda
[   65.326883]     ide0: BM-DMA at 0x1000-0x1007, BIOS settings: hda:pio, hdb:DM                        A
[   65.612257] hda: IBM-DTTA-351290, ATA DISK drive
[   67.223285] hda: max request size: 128KiB
[   67.281408] hda: 25385472 sectors (12997 MB) w/464KiB Cache, CHS=25184/16/63,                         UDMA(33)
[   67.281440] hda: cache flushes not supported
[   67.281577]  hda: hda1 hda2 < hda5 >

Konqueror from the LiveCD won't mount the hda1 using the graphical right click 'mount'

This command does mount it ok:
ubuntu@ubuntu:~$ sudo mkdir /media/hda1
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hda1 /media/hda1
ubuntu@ubuntu:~$ ls /media/hda1
bin    dev   initrd          lib         mnt   root   srv  usr    vids
boot   etc   initrd.img      lost+found  opt   sbin   sys  var    vmlinuz
cdrom  home  initrd.img.old  media       proc  share  tmp  video  vmlinuz.old

ubuntu@ubuntu:~$ sudo fdisk -l  /dev/hda
Disk /dev/hda: 12.9 GB, 12997361664 bytes
255 heads, 63 sectors/track, 1580 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1511    12137076   83  Linux
/dev/hda2            1512        1580      554242+   5  Extended
/dev/hda5            1512        1580      554211   82  Linux swap / Solaris
ubuntu@ubuntu:~$       

fsck reports that hda1 is clean, and complained about hda5.
I tried mkswap on hda5 but that hasn't helped...


Here's fstab from dead machine:
ubuntu@ubuntu:~$ cat /media/hda1/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/hda1
UUID=edfefe8f-af1d-4d0e-9503-c88e73ec3656 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hda5
UUID=9aa68e57-3a80-470d-8f09-1f427a08cf32 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/ /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
\134\134192.168.0.103\134media\134videos / cifs uid=0,gid=114,auto,rw,nouser,user=username,password=password 0 0
ubuntu@ubuntu:~$   


Any thoughts, magic commands to try are most welcome!

Cheers,
Andrew

---

### Post by acodring on 2007-04-18
Google told me about another nifty command I barely understand...
Seeing the full list below, it might be good to explain that this used to be a windows machine and it did have 5 partitions on it before. I'm not however trying to dual boot.

ubuntu@ubuntu:~$ sudo sfdisk -l -x /dev/hda

Disk /dev/hda: 25184 cylinders, 16 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: The partition table looks like it was made
  for C/H/S=*/255/63 (instead of 25184/16/63).
For this listing I'll assume that geometry.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/hda1   *      0+   1510    1511-  12137076   83  Linux
/dev/hda2       1511    1579      69     554242+   5  Extended
/dev/hda3          0       -       0          0    0  Empty
/dev/hda4          0       -       0          0    0  Empty

/dev/hda5       1511+   1579      69-    554211   82  Linux swap / Solaris
    -           1511    1510       0          0    0  Empty
    -           1511    1510       0          0    0  Empty
    -           1511    1510       0          0    0  Empty

ubuntu@ubuntu:~$

---

### Post by acodring on 2007-04-19
I don't normally talk to myself in real life... but thought I should close this out for future noobs.

I found another tool, qtparted and used it to get the machine running again.

- Boot into livecd
- run qtparted as root (sudo qtparted from a command prompt in a terminal window)
- select /dev/hda
- delete /dev/hda5
- commit changes by clicking on save icon
- try to reformat the 'free' partition that replaced /dev/hda5 (it was named /dev/hda1-1) but qtparted wouldn't let me
- exit qtparted, mess with some other things to no effect
- restart qtparted and see that it now shows the free space as /dev/hda2
- 'create' /dev/hda2
- format /dev/hda2 as linux-swap 
- commit changes
- exit qtparted
- sudo mkdir /media/hda1 (just need somewhere to mount the main partition temporarily)
- sudo mount -t ext3 /dev/hda1 /media/hda1 to get access to the main partition of the hard drive
- sudo vim /media/hda1/etc/fstab to edit the fstab table 
-  fix the old swap entry to refer to /dev/hda2 instead of /dev/hda5
- save changes and exit vim with :wq
- restart into mythfrontend glory!

---

