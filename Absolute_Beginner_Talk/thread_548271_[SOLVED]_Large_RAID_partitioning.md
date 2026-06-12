---
title: "[SOLVED] Large RAID partitioning"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by -=bb=- on 2007-09-11
Hi,

I am having quite a few problems partitioning my RAID5EE array into more than 4 drives under Ubuntu 7.04.

I have 10 x 500Gb SATA drives configured under and Adaptec 31605 card to run as a single large 4Tb drive (1Tb lost for redundancy).

I researched the drive size issue and to the best of my knowledge I need to have a gpt partition table to be able to access the whole drive space.

Using parted I created the following partitions
```

root@ubervisor:~# parted /dev/sdc
GNU Parted 1.7.1
Using /dev/sdc
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) p

Disk /dev/sdc: 4000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      17.4kB  1700GB  1700GB  ext3         media
 2      1700GB  2000GB  300GB   ext3         corp
 3      2000GB  2300GB  300GB   ext3         perso
 4      2300GB  2800GB  500GB   ext3         misc
 5      2800GB  3300GB  500GB   ext3         homes
 6      3300GB  4000GB  700GB   ext3         backups
```

After using parted I could access, read/write and format dev/sdc1-dev/sdc6 with no problems.

However after rebooting, only devices sdc1 - sdc4 are visible or mounted.

My fstab looks like this :
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/md0        /               ext3    defaults,errors=remount-ro 0       1
                /media/backups  ext3    defaults        0       2
# /dev/sdc2
UUID=d1c1816b-55bf-4732-9280-d34c41f1968b /media/corp     ext3    defaults        0       2
                /media/homes    ext3    defaults        0       2
# /dev/sdc1
UUID=cb042a0f-1a10-48a6-9c4d-b02e85e42a34 /media/media    ext3    defaults        0       2
# /dev/sdc4
UUID=92c670e6-00cf-48f9-a1c6-73b2861d00ab /media/misc     ext3    defaults        0       2
# /dev/sdc3
UUID=69af790f-0a21-4746-8510-09369c36f29f /media/perso    ext3    defaults        0       2
/dev/md1        none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

You can see there is no attempt to mount sdc5 or sdc6. 

According to [this thread]("http://ubuntuforums.org/showthread.php?t=429986&highlight=gpt+parted&page=2") there may be some problems with parted 1.7.1 and gpt. I have tried to upgrade to 1.8.8 following the directions in that thread, however each attempt to MAKE the new version results in an error ```
/usr/bin/ld: /usr/lib/../lib64/libuuid.a(uuidgen.o): relocation R_X86_64_32 against
`a local symbol' cannot be used when making a shared object; recompile with -fPIC
```Using ./configure CFLAGS="-fPIC" doesn't resolve the problem.

I have only a few days experience with Ubuntu (or *nix at all) so I would be grateful if I have made a complete ballsup of something here, that you guys go gentle on me :)

Otherwise, a nice simple 'then we press the key marked Enter' style idiot proof reply would be greatly appreciated. If you need any other information to help diagnose the problem, please let me know and I will reply as soon as I can.

Many thanks in advance

---

### Post by gn2 on 2007-09-11
Not exactly a beginner's question is it?

---

### Post by -=bb=- on 2007-09-11
I posted here because I am an absolute beginner. I tried to fix the problem but couldn't and don't know if it was a beginner's mistake or possibly something trickier.

Should I try to repost this in another forum or can I ask for an admin to move it?

Thanks

---

### Post by overdrank on 2007-09-11
Hi maybe these links will help

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://bfish.xaedalus.net/?p=188](http://bfish.xaedalus.net/?p=188)

---

### Post by -=bb=- on 2007-09-11
overdrank,

Thank you for the links. If I am not mistaken they relate more to configuring drives in a software array than partitioning an existing RAID device that is being managed already by dedicated hardware (the Adaptec 31605 card I mentioned earlier).

I had considered trying to create the RAID5 device in software but a) I have already bought the dedicated card ;) and b) I think the overhead would slow things down too much when I start to hammer away at the array.

I'm not sure if the problem is RAID related, due to parted 1.7.1 not correctly writing gpt or a large drive problem. 

Thank you nevertheless for taking the time to help though, it is much appreciated.

---

### Post by Scorpuk on 2007-09-11
On a slight tangent to your question.

I have 6 x 500GB SATA drives on my server set up as a software RAID 5.


Using bonnie++ to check its throughput I get the following result:

Writing to HDD:

64,580K/sec @ 95% cpu  (putc)
81,743K/sec @ 24% cpu  (Intelligent write) 
58,929K/sec @ 12% cpu  (re-write)

Reading from HDD:

66,488K/sec @ 94% cpu   (getc)
222,297K/sec @ 21% cpu  (Intelligent read)


System specs:

[http://scorpuk.plus.com/phpsysinfo]("http://scorpuk.plus.com/phpsysinfo")


EDIT: on another note which version of ubuntu are you using? 32bit or 64bit?

---

### Post by -=bb=- on 2007-09-11
The problem was in fact due to parted as mentioned in the thread I reference in my OP.

Once parted 1.8.8 was installed (following mostly the instructions given by philipMac) then parted detected the incorrect gpt label (it is apparently missing a fake msdos partition table). 

All is now well. Thank you for those who tried to help.

---

