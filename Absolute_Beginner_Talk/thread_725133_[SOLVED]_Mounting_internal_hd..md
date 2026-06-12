---
title: "[SOLVED] Mounting internal hd."
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by lover_of_sc on 2008-03-15
Hi there,

I have two internal hd:s both a 150g on a ext filesystem. I have mounted the drive as media/disc. 

I am not used to linux at all, will this media be utilised together with my main drive> Or do I need to treat that one as a separate hard drive?

pasted from fdisk:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf5966b27

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   300431564   150215751   83  Linux
/dev/sda2       300431565   312576704     6072570    5  Extended
/dev/sda5       300431628   312576704     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1de2c90e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   312576704   156288321   83  Linux


pasted from fstab:

anders@anders-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a8ece2c8-1bfb-4f2d-8261-e418284af78d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=f3692d2a-63a0-4f91-befe-1a8406428a35 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

many thx.

---

### Post by glennric on 2008-03-15
According to your fstab you don't have the second drive setup to mount at all.  Have you manually mounted it?  If so you should be able to navigate to /media/disc and view the drives contents.

---

### Post by taurus on 2008-03-15
Didn't we just go through this not that long ago?  

Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdb1   /media/disc   ext3   defaults   0   1
```
Save it and reboot.

---

### Post by lover_of_sc on 2008-03-15
taurus  - sorry to pester you again mate, I managed to mess my entire computer up severly yesterday so I copied all of my files to my external hard drive this morning and reinstalled everything. All works 100% except the &%$%$%£^£ sdb1 again. I did what you told me (again) and still no luck:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a8ece2c8-1bfb-4f2d-8261-e418284af78d /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb1   /media/disc   ext3   defaults   0   1
# /dev/sda5
UUID=f3692d2a-63a0-4f91-befe-1a8406428a35 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf5966b27

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   300431564   150215751   83  Linux
/dev/sda2       300431565   312576704     6072570    5  Extended
/dev/sda5       300431628   312576704     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1de2c90e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   312576704   156288321   83  Linux

i understand that you probably loose your will to live over my lack of skill in linux. Sorry!

---

### Post by taurus on 2008-03-15
What do you mean no luck with /dev/sdb1?  Did you either reboot or mount it with

```
sudo mount -a
```
What's the output of these commands from a terminal?

```
df -h
id
```

---

### Post by lover_of_sc on 2008-03-15
I did reboot the computer after I changed the fstab as per your instructions.

no luck = I could not find sdb1 in the media.

here you go:

anders@anders-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             142G  119G   15G  89% /
varrun               1014M   96K 1013M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M  104K 1013M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   34M  980M   4% /lib/modules/2.6.22-14-generic/volatile
anders@anders-laptop:~$ 


uid=1000(anders) gid=1000(anders) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),108(lpadmin),110(admin),115(netdev),117(powerdev),1000(anders)
anders@anders-laptop:~$

---

### Post by taurus on 2008-03-15
And you said /dev/sdb is also an internal drive?  Fire up gparted in System -> Administration and see what does it say about /dev/sdb.  If you only want to create one partition, /dev/sdb1, then it should start at 1, not 63.  Is there something like unallocated space before /dev/sdb1?  Take a screenshot and post it here if you wish.

---

### Post by lover_of_sc on 2008-03-15
It should be completely empty, but for some reason it states that I have 2.52Gb used? please see attached screen dumps.

---

### Post by taurus on 2008-03-15
Since you don't have anything on /dev/sdb1 right now and it is not mounted, can you use gparted and delete /dev/sdb1?  Now, you should have the whole disk unallocated, /dev/sdb.  Create /dev/sdb1 again and the partition should start from 1 this time instead of 63.  Then, format it to ext3.

---

### Post by lover_of_sc on 2008-03-15
I just tried that and the it created the exact same partition again? Still started at 63, and I still cant see it under /media/

---

### Post by lover_of_sc on 2008-03-15
Here is the new info from fdisk / fstab if it helps mate?

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf5966b27

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18701   150215751   83  Linux
/dev/sda2           18702       19457     6072570    5  Extended
/dev/sda5           18702       19457     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1de2c90e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a8ece2c8-1bfb-4f2d-8261-e418284af78d /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb1   /media/disc   ext3   defaults   0   1
# /dev/sda5
UUID=f3692d2a-63a0-4f91-befe-1a8406428a35 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by taurus on 2008-03-15
> **lover_of_sc said:**
> Here is the new info from fdisk / fstab if it helps mate?

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf5966b27

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18701   150215751   83  Linux
/dev/sda2           18702       19457     6072570    5  Extended
/dev/sda5           18702       19457     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1de2c90e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               **[COLOR="Blue"]1       19457[/COLOR]**   156288321   83  Linux


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a8ece2c8-1bfb-4f2d-8261-e418284af78d /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb1   /media/disc   ext3   defaults   0   1
# /dev/sda5
UUID=f3692d2a-63a0-4f91-befe-1a8406428a35 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

Actually, it start at 1 now.

See if you can mount it with 

```
sudo mount -a
```
And by the way, I assume you have already created a mount point, /media/disc, for it, right?

---

### Post by lover_of_sc on 2008-03-15
nope, I am afraid not:

anders@anders-laptop:~$ sudo mount -a
[sudo] password for anders:
mount: mount point /media/disc does not exist


sorry

---

### Post by taurus on 2008-03-15
Then you need to create the mount point first before you can mount it.

```
sudo mkdir /media/disc
sudo mount -a
df -h
```
Now, I assume you want to write to /media/disc without using sudo.  You just need to change the ownership of /media/disc from root to your login name, anders.

```
sudo chown -R anders:anders /media/disc
la -la /media
```

---

### Post by lover_of_sc on 2008-03-15
Ohhh puha, yes that worked! Hope i don't have to bother you again mate. Cheers for your support. thanks,

---

