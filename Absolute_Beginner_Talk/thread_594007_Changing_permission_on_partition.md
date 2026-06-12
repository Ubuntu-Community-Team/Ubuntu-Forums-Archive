---
title: "Changing permission on partition"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by jba6511 on 2007-10-27
I recently created some new partitions and can not access on of them. I have created a partition on dev/sda1 that is formated with ext3 and is for storage of virtualbox images. However, root owns this partition and I can not copy or paste to it. I tried to do sudo chown blake /dev/sda1 but it does not seemed to have worked. What do I need to do? A similar partition formatted with ntfs allows me to read and write with no problems.

---

### Post by taurus on 2007-10-27
Where do you mount /dev/sda1?  You need to use the mount point instead of device name.

```
id
df -h
```

---

### Post by jba6511 on 2007-10-27
[PHP]blake:~$ id
uid=1000(blake) gid=1000(blake) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),108(lpadmin),110(admin),115(netdev),117(powerdev),121(vboxusers),122(mysql),123(mythtv),1000(blake)
blake:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              20G  3.2G   16G  17% /
varrun                1.7G  100K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G   96K  1.7G   1% /dev
devshm                1.7G     0  1.7G   0% /dev/shm
lrm                   1.7G   34M  1.6G   3% /lib/modules/2.6.22-14-generic/volatile
/dev/sda7             113G  6.7G  100G   7% /home
/dev/sda1              82G  184M   77G   1% /media/sda1
/dev/sda5              79G   33G   46G  42% /media/sda5
/dev/scd0             580M  580M     0 100% /media/cdrom0
[/PHP]

would this mean that I need to do sudo chown blake /media/sda1 then?

---

### Post by taurus on 2007-10-27
Yip.

```
sudo chown -R blake:blake /media/sda1
ls -la /media
```

---

### Post by jba6511 on 2007-10-27
thanks

---

