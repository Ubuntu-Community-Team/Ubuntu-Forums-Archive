---
title: "Can you have /tmp and /opt partitions? Kubuntu Dapper 6.06"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by darkworld on 2007-04-30
Hi

The df output and fdisk-l output are as follows:

Filesystem           1K-blocks Used Available Use% Mounted on
/dev/hdb1              2664368    288916   2240108  12% /
varrun                  193136       104    193032   1% /var/run
varlock                 193136         4    193132   1% /var/lock
udev                    193136       156    192980   1% /dev
devshm                  193136         0    193136   0% /dev/shm
lrm                     193136     18856    174280  10% /lib/modules/2.6.15-28-386/volatile
/dev/hdb6              7273744    600612   6303640   9% /home
/dev/hdb10            17299004   2042988  14377264  13% /usr
/dev/hdb7              3020140    601156   2265568  21% /var
/dev/sda1               978416         4    978412   1% /media/sda1
/dev/sda4              1006896        92    955656   1% /media/sda4
*************************************************************
and .....

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         337     2706921   83  Linux
/dev/hdb2             338        4865    36371160    5  Extended
/dev/hdb5             338         483     1172713+  82  Linux swap / Solaris
/dev/hdb6             484        1403     7389868+  83  Linux
/dev/hdb7            1404        1785     3068383+  83  Linux
/dev/hdb8            1786        2295     4096543+  83  Linux
/dev/hdb9            2296        2677     3068383+  83  Linux
/dev/hdb10           2678        4865    17575078+  83  Linux
************************************************************

hdb8 and hdb9 dont appear to be mounted and they were my /tmp and /opt partitions I think. trying to mount them doesnt appear to work??????

---

### Post by Bachstelze on 2007-04-30
What happens when you try to mount them, instead of what you expected ?

---

### Post by darkworld on 2007-04-30
This is the reply

mount: can't find /dev/hdb9 in /etc/fstab or /etc/mtab

and this is the /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb6       /home           ext3    defaults        0       2
/dev/hdb10      /usr            ext3    defaults        0       2
/dev/hdb7       /var            ext3    defaults        0       2
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by Bachstelze on 2007-04-30
Obviously, mount cannot guess the mount parameters so if the partition is not in your fstab, it won't be able to mount it. Either add a line in your fstab or specify all the needed parameters in your mount command.

---

### Post by darkworld on 2007-04-30
got to pop out. back in 40mins

can I update the fstab?????

---

### Post by darkworld on 2007-04-30
so 

mount /dev/hdb9 isnt sufficient???

not sure I understand this

do you mean

mount /dev/hdb9 /directory   ??????

---

### Post by Outrunner on 2007-04-30
I don't know much about edititng the fstab config file either but you can

```
sudo mkdir /mnt/[dirname]
```

and

```
sudo mount /dev/hdb9 /mnt/[dirname]
```

---

### Post by Bachstelze on 2007-04-30
> **darkworld said:**
> mount /dev/hdb9 isnt sufficient???

Of course not ! Linux doesn't have the power to read your mind yet so it cannot guess *where* you want to mount the partition and *what* filesystem there is on it.

```
sudo mount /dev/something -t filesystem /somewhere
```

---

### Post by darkworld on 2007-04-30
Thanks for all the replies above guys.

I didnt intend to not have /tmp and /opt partitions mounted continuously. I must have mucked up in my installation somewhere. Not sure whether to live with it or reinstall.???

Er just one thought why does it automatically mount some of my usb stick partitions? why doesnt it wait for me to tell it where then????

---

