---
title: "Partitions and Permissions Problems..."
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by adi-n on 2007-05-05
Hey everyone,

i've just installed ubuntu and have a partitions problem:

i have 2 hdd, first one has 1 partition ubuntu is installed on.

second hdd has 2 partition who were NTFS, ive formatted them with "GNOME partition editor" to "ext3" (what this means? linux file system?) but i still cant write on them.

please help!

---

### Post by taurus on 2007-05-05
You need to change the ownership of that new ext3 partition from root to your login name.  what are the outputs of these two commands from a terminal?

Applications -> Accessories -> Terminal
```
id
cat /etc/fstab
```

---

### Post by adi-n on 2007-05-05
Bah why is it so complicated...

Look at this:

```
adi@adi:~$ id
uid=1000(adi) gid=1000(adi) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),112(netdev),113(lpadmin),115(powerdev),117(admin),1000(adi)
adi@adi:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=462b4d97-b399-4118-a1ae-a83e1bc82f80 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=b3ac6828-53be-43c6-a1fe-a6db29ac5b9f none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
adi@adi:~$ 

```

OH and how do i change the partition name...?

---

### Post by taurus on 2007-05-05
You don't have an entry in /etc/fstab to mount it.  Therefore, I need to see the output of this command so I would know which partition it is.

```
sudo fdisk -l
```

---

### Post by adi-n on 2007-05-05
ok:


```
adi@adi:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4660    37431418+  83  Linux
/dev/hda2            4661        4865     1646662+   5  Extended
/dev/hda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2550    20482843+   b  W95 FAT32
/dev/hdb2            2551        4865    18595237+   f  W95 Ext'd (LBA)
/dev/hdb5            2551        4865    18595206   83  Linux
adi@adi:~$ 

```

---

### Post by taurus on 2007-05-05
So you want to mount /dev/hdb5 then.

Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/hdb5   /media/hdb5   ext3   defaults   0   1
```
Save it.  Then, create a new mount point and mount it.

```
sudo mkdir /media/hdb5
sudo mount -a
df -h  <-- you should see /dev/hdb5 mounted to /media/hdb5 at the bottom of the output
```
Now, change the ownership of /media/hdb5 from root to adi.

```
sudo chown -R adi:adi /media/hdb5
ls -la /media
```

---

### Post by adi-n on 2007-05-05
works cool, thanks, two more questions:

1. is there any easier way? like through GNOME partition editor?
2. how do i change the driver (partition) name from disk and disk-1 to something else?

huge thanks again!

---

### Post by taurus on 2007-05-05
1.  There is gparted in System -> Administration.  If you don't have it, install it with

```
sudo aptitude update
sudo aptitude install gparted
```

2.  Not sure exactly what you mean.  Are you talking about LABEL (or name) of your harddrive?

---

### Post by adi-n on 2007-05-05
1. ok thanks!
2. yes... my partitions are named disk and disk-1 ....

---

### Post by taurus on 2007-05-05
Which partitions?

---

### Post by adi-n on 2007-05-06
hdb1 & hdb5 ... both mounted like youve told me

---

### Post by ubnewbie2 on 2007-05-06
The mount point (the directory you created for the hard drive partition to be mounted on) can be any name you want.  Just alter the fstab entry to mount it to the directory name that you created.

---

### Post by adi-n on 2007-05-06
how? ive created those directories (hdb1 & hdb5) but i cant rename them..
i need to create new 2 dirs? if so, could you guide me? still a newbie...

---

### Post by ubnewbie2 on 2007-05-06
> **adi-n said:**
> how? ive created those directories (hdb1 & hdb5) but i cant rename them..
i need to create new 2 dirs? if so, could you guide me? still a newbie...

example for hdb5

edit fstab

```
gksudo gedit /etc/fstab
```

change the previous line for hdb5

```
/dev/hdb5   /mnt/mydisk   ext3   defaults   0   1
```

make the new directory and remount

```

sudo mkdir /mnt/mydisk
sudo mount -a

```

change ownership

```
sudo chown -R adi:adi /mnt/mydisk
```

So now the hd5 disk is accesible as /mnt/mydisk (or any name you choose)

---

