---
title: "Can't get partition on disk to mount on file system"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by shopjohn8 on 2007-12-25
Hello all
I have two disks on my system, the first is an u320 SCSI 36gig and the second is a IDE 120gig. 
The mobo is IBM with a single AMD opteron 242 and 2 gigs ram and on board SCSI.
I installed 7.10 desktop edition and for hardware reasons the IDE drive always is the first to boot, there is not a specific boot drive option in the BIOS. I installed '/boot' in the first partition of the IDE drive, '/' on the first partition of the SCSI drive, and a swap '/var' and '/usr' on separate partitions on that drive.
On the IDE disk there are '/boot', a swap, '/home' and two unused partition under an extended partition.

I can mount them as disks, Nautilus can see them in the file browser, but I can not use them. I have tried to change there owner as they are “root” by default. what am I missing? if I add mount points they to them  the free space of that folder does not change. 

Any suggestions on partition mounting? :confused:

---

### Post by taurus on 2007-12-25
You cannot write outside of your own $HOME directory.  To do that, you need to be root and that's why the sudo command is for.  What do you want to write and where do you want to write to?

Applications -> Accessories -> Terminal
```
gksudo nautilus
```
That would allow you to have full access so better be careful of what you delete.  Don't change the defaults permissions if you don't know what you are doing.

---

### Post by logos34 on 2007-12-25
post the output of 

sudo fdisk -l

and

cat /etc/fstab

---

### Post by shopjohn8 on 2007-12-25
Thanks for replying Taurus and Logos34

I wont to practices adding partitions and files. I am working with my first install and am going to dump my old system when i am setup. i want to have a backup of all my files ( music, documents and downloaded misc. stuff) linked to my home directly. (symbolic link?).
 I mounted /, /var, and /usr, on the faster drive for more performance and am using the slower drive for storage. 

Using sudo command will end when the file browser is closed?


Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          30      240943+  83  Linux
/dev/hda2              31         331     2417782+  82  Linux swap / Solaris
/dev/hda3             332        5802    43945807+  83  Linux
/dev/hda4            5803       14593    70613707+   5  Extended
/dev/hda5           10163       14593    35591976   83  Linux
/dev/hda6            5803       10162    35021637   83  Linux

Partition table entries are not in disk order

Disk /dev/sda: 36.4 GB, 36401479680 bytes
255 heads, 63 sectors/track, 4425 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e572e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1459    11719386   83  Linux
/dev/sda2            1460        1760     2417782+  82  Linux swap / Solaris
/dev/sda3            1761        2702     7566615   83  Linux
/dev/sda4            2703        4425    13839997+  83  Linux


shopjohn@wabble:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=380e2a40-5f49-424a-b0a7-c8ab5cbcb3d8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=c21a44d3-92af-4bb9-bf96-1e2a3a86d4c0 /boot           ext3    defaults        0       2
# /dev/hda3
UUID=7caf8402-afb5-4729-8f5e-e6de8189b908 /home           ext3    defaults        0       2
# /dev/hda4
UUID=fdc499da-1aef-424b-89d4-34a6ca9d5a74 /opt            ext3    defaults        0       2
# /dev/sda4
UUID=ce1489c3-b6e8-453d-b553-f6a506a4d0e2 /usr            ext3    defaults        0       2
# /dev/sda3
UUID=48ac59f3-6571-4a64-9631-78a0410521f3 /var            ext3    defaults        0       2
# /dev/hda2
UUID=58dfbe53-76d0-408c-9eeb-f39687bdf186 none            swap    sw              0       0
# /dev/sda2
UUID=17acc5a1-2afa-48a6-a62f-7cdd98108e80 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by RSLxH on 2007-12-25
I have a load of partitions on a main storage and distro-test harddrive. Whenever I want to mount a partition to use it as a folder/directory, I do this:

Make the directory (call it what you want)
```
sudo mkdir /TestDirectory
```

Then edit your fstab file (always back it up first), and where you can see your drives "var" "usr" "opt" "home" etc, you just add /TestDirectory after the Ext3 Linux partition that you want to mount.
```
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
```

Your line will look something like:
```
# /dev/hda3
UUID=7caf8402-afb5-4729-8f5e-e6de8189b908 /home ext3 defaults 0 2
```
...but instead of home it will be /TestDirectory.

Now you need to mount the drive to the directory:
```
sudo mount -a
```

I think your not being able to use the partitions you have mounted stems from not having the right permissions, so we are going to make your mounted directory readable and writeable:
```
sudo chown -R shopjohn:shopjohn /TestDirectory
```
```
sudo chmod -R 755 /TestDirectory
```

Now you should have your partition mounted and with read/write access. Just look in your "Places" "Computer" directory for "TestDirectory".

---

