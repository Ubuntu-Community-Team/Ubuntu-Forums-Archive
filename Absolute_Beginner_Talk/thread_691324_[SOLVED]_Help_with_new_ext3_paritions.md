---
title: "[SOLVED] Help with new ext3 paritions"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by nodegamra on 2008-02-08
I installed two new hard drives 250Gb each.
I made one new primary partition on each drive with fdisk and confirmed changes.
Formated the partitions with mkfs.
Mounted the partitions and I can see the partitions
I even made an fstab entry for each and they mount on startup fine

My problem is that I cant write to the partitions unless I am root
How could I change it to be able to use the partitions as a regular user?
:confused:

---

### Post by taurus on 2008-02-08
You need to change the owner of the mountpoint for that partition from root to your login name.  _Assuming_ your login name is **node** and the mount point for that partition is /media/drive, run

```
sudo chown -R **node**:**node** /media/drive
ls -la /media
```

Now, do the same for the second partition, mount point.

---

### Post by jan quark on 2008-02-08
try this

```
sudo chown -R usr:usr CU
```

usr:usr is your username for instance bob:bob and CU is the path to the partition for finstance /media/sda1

```

sudo chmod -R 755 CU
```



```
ls -la
```

---

### Post by nodegamra on 2008-02-08
Sorry guys I must be doing something wrong still no go.

---

### Post by taurus on 2008-02-08
What exactly did you run?

Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
df -h
id
```

---

### Post by nodegamra on 2008-02-08
Disk /dev/hda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16ab16ab

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4665    37471581   83  Linux
/dev/hda2            4666        4870     1646662+   5  Extended
/dev/hda5            4666        4870     1646631   82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004e6c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002b871

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux

__________________________________


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=4fffb023-4d92-44c4-bad3-be32f2b884a6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=7ad2932d-1951-4336-95a4-0fb1c3c182db none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
192.168.1.100:/home/node/Desktop/dvdrip-data /home/node/transcode nfs rsize=8195,wsize=8195,timeo=14,intr
/dev/sda1       /home/node/media2       ext3    defaults        1       1
/dev/sdb1       /home/node/media3       ext3    defaults        1       1


________________________________________

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              36G  815M   33G   3% /
varrun                506M   56K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M  100K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
/dev/sda1             230G  188M  218G   1% /home/node/media2
/dev/sdb1             230G  188M  218G   1% /home/node/media3

_____________________________________________

uid=1000(node) gid=1000(node) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),109(lpadmin),110(admin),1000(node)

---

### Post by taurus on 2008-02-08
```
sudo chown -R node:node /home/node/media2
sudo chown -R node:node /home/node/media3
ls -la ~
```

---

### Post by nodegamra on 2008-02-08
I repeated your first post and it woked all of the sudden!
Sorry the trouble and thanks for the help.

---

