---
title: "Missing Mounts"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by bon_the_one on 2008-02-06
Hi All,

I'm posting this in Beginners because I MUST be making some mistake, but for the life of me I can't work out where. In previous systems (SuSE, FC) everything I've put in fstab has shown up as a mounted volume when I've done a 'df' or 'mount'. Gutsy seems different tho, and I wonder if anyone can tell me why? 
I'm after knowing because I run MythTV on my system and monitoring disk space on volumes is quite important as I like recording stuff, but at the moment I'm never sure what space I've got left!

My fstab reads thus : 
proc            /proc           proc            defaults        0       0
/dev/sda3       /               ext3            defaults,errors=remount-ro 0       1
/dev/sda1       /boot           ext2            defaults        0       1
/dev/sda4       /home/bon       ext3            defaults        0       1
/dev/sdb1       /home/mythtv    ext3            defaults        0       1
/dev/sda2       none            swap            sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec    0       0

As you can see, I have disk1, part 4 for my 'home/bon' and a whole disk devoted to myth on 'dev/sdb1'.

When I call mount as root tho, I am shown this : 
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

As you can see, I cannot see my sda4 and sdb1 mounts.
"df -h" shows me this :
/dev/sda3              19G   16G  2.1G  89% /
varrun                248M  128K  248M   1% /var/run
varlock               248M     0  248M   0% /var/lock
udev                  248M  144K  248M   1% /dev
devshm                248M     0  248M   0% /dev/shm
lrm                   248M   33M  215M  14% /lib/modules/2.6.22-14-generic/volatile

Again, I cannot see my home/bon or my home/mythtv mounts, and so not see what the available disk space is. 

Can anyone please tell me why this is occurring, and what I can do to get all the mounts showing as I am used to? Is this an Ubuntu thing where all space is lumped under '/' or have I messed up fstab somehow? 

I'd really appreciate some help, 
Many Thanks,

Ian

---

### Post by talsemgeest on 2008-02-06
Maybe try messing around with the options?

---

### Post by njparton on 2008-02-06
When you try the following, what happens?:

```
sudo mount -a
```

If they still don't mount, try deriving their UUID's and mount via them instead. I can't recall the command to find the UUID of a drive or partition but someone else will chime in with it.

---

### Post by bon_the_one on 2008-02-06
Thanks for your help so far,

I've already tried both of those options, being used to Lin for a few years now. (Although gutted Ubuntu will only mount by ID, not by label, which used to be handy!)

I know the Vol's are mounted for sure, because in the '/' tree "/home/bon" and "/home/mythtv" are empty when I bring the system up off the LiveCD. I just put them into the tree as mount points. Once my system is up from the local install, both directories are populated with the data on the discs. So they are DEFO mounting! This is whats confusing me! I know they are there, but I can't see them in 'mount' or 'df' !

Any other ideas?!

Thanks!
Ian

---

### Post by hyper_ch on 2008-02-06
first of all, I'd use

"0  2" as mounting options and not "0  1"

and post the output of:

```

sudo fdisk -l

```

And use the [ code] tags to make it more readable.

---

### Post by bon_the_one on 2008-02-06
```


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e9136

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          16      128488+  83  Linux
/dev/sda2              17         514     4000185   82  Linux swap / Solaris
/dev/sda3             515        3004    20000925   83  Linux
/dev/sda4            3005        9729    54018562+  83  Linux

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a991a98

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401   83  Linux

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00034b0b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9729    78148161    b  W95 FAT32

Disk /dev/sdd: 1015 MB, 1015808000 bytes
32 heads, 61 sectors/track, 1016 cylinders
Units = cylinders of 1952 * 512 = 999424 bytes
Disk identifier: 0x00000000


```

Is what shows, so I know the partitions are there!

---

### Post by hyper_ch on 2008-02-06
> 
The sixth field, (fs_passno), is used by the fsck(8) program to determine the order in which filesystem checks are done at reboot time.  The root filesystem should be specified with a  fs_passno  of  1,  and other  filesystems  should  have  a fs_passno of 2. 

Try chaning the /dev/sda4 to  "0  2" and see if that helps.

---

### Post by bon_the_one on 2008-02-06
I get an error saying it can't fsck the volumes because they are already mounted. Ctrl-D to continue or enter root passwd. Thats not much help!

---

### Post by bon_the_one on 2008-02-06
Oh, both volumes are Ok, I've run fsck over them and they check out ok, and as mentioned previously, they mount fine as when booted they are in place. They just don't show up in df or mount.

---

### Post by logos34 on 2008-02-06
try creating new mount points in /media directory.  (that's the standard place).  

Do they appear now in df and mount?

Or perhaps change fstab to use the 'UUID=xxx' format

---

### Post by bon_the_one on 2008-02-06
Ok, tried uuid, no help.

I'm not mounting them in /media, as they're home directories, not /media mounts. Surely Ubuntu can give information for mounts on stuff outside /media? Or has the OS been knobbled to make it useless? If thats the case I'll have to switch to something that can give proper readings.

Thanks,
Ian

---

### Post by njparton on 2008-02-06
I mount in both /media and /mnt so that's not the problem.

---

### Post by logos34 on 2008-02-06
> **bon_the_one said:**
> Ok, tried uuid, no help.

I'm not mounting them in /media, as they're home directories, not /media mounts. Surely Ubuntu can give information for mounts on stuff outside /media? 

Normally, yes...I'm just throwing out suggestions to try.  

It is odd that neither shows up in the above commands despite being visibly mounted at the correct points.

---

