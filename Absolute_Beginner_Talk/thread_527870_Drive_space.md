---
title: "Drive space"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by marty922 on 2007-08-17
G'day all,

When I look at gparted for my hda1 drive, it reports that I have 12.G free.

But when using nautilus, it says only 600M

Where's the other 12G?

Cheers,

Marty

---

### Post by funpop on 2007-08-17
maybe nautilus shows the free space on your root partition ?

 
> df -h

in a terminal shows disk space on all mounted partitions

---

### Post by marty922 on 2007-08-17
```

~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda6              55G   27G   25G  53% /
varrun                506M  104K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  128K  506M   1% /proc/bus/usb
udev                  506M  128K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-16-generic/volatile
/dev/hdb1             230G  217G  635M 100% /media/hda1
/dev/disk/by-uuid/00DC43B7DC43A62E
                      112G  106G  6.6G  95% /media/sdb1
/dev/hdc              698M  698M     0 100% /media/cdrom0
/dev/sdc1             1.9G  803M  1.2G  42% /media/disk

```

So why does it show 217G used of 230G but only 635M free?

---

### Post by schorsch on 2007-08-17
Is this an ext2/ext3-filesystem? Please type

```
mount
``` and post the output here.

If so, please type

```
tune2fs -l /dev/hdb1
``` and post the output.

I guess, the amount of for root reserved percentage of the filesystem ist set to the default 5%. This is done so that even if the filesystem is full root is able to do something like delete, tar etc. And 5% of 230GB will be ~12GB ....

If so you can change this by:

```
umount /dev/hdb1
tune2fs -m 0 /dev/hdb1
mount /dev/hdb1
```

This sets the reserved block count to 0 percent and there should be more space available

---

### Post by hyper_ch on 2007-08-17
do this:

```

cd /media/hda1
du > output.txt

```

then open output.txt and you will see how much space each directory and subdirectory is using... so youc an find out where you waste all your space.

---

