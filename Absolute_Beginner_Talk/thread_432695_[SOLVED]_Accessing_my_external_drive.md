---
title: "[SOLVED] Accessing my external drive"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-05-04
I formatted my external hard drive to EXT3. Now, it doesn't mount at all. I know we have to put in an entry in the /etc/fstab, but I don't know how. Here is the output for fdisk -l

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3142    25236914+   7  HPFS/NTFS
/dev/sda2            3142        6403    26192896    7  HPFS/NTFS
/dev/sda3            6404       15722    74854867+  83  Linux
/dev/sda4           15723       19457    30001387+   5  Extended
/dev/sda5           15723       16842     8996368+  83  Linux
/dev/sda6           16843       19332    20000893+  83  Linux
/dev/sda7           19333       19457     1004031   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

```

Also, why is it recognizing the external drive as sdb1 ? Why not just like a USB drive which it did before I formatted it from NTFS to EXT3 ?

I have a dual boot with Vista. Can someone guide me as to how I will assign a drive letter for this external drive ?

The only option it shows me is 'Delete Volume' in the Disk Management Utility in Vista. The rest of the options are all ghosted. 

Could it be because I already have 3 primary partitions and the DVD drive = 4 and it cannot handle another one? We should still be able to 'mount' it as a slave drive, correct?

---

### Post by astrauss on 2007-05-04
OK, I know I'm not giving you detailed info here, but it's a start. Windows cannot read HDD's formatted in ext3. I had a utility which allowed that to work, but it broke after installing Feisty.

---

### Post by Cypher on 2007-05-04
Is the external drive connected to the PC through USB? What was the drive name before you formatted it to EXT3?

Do you only have one internal HD?

I'm going to assume that /dev/sdb is your external HD, so try this from the command line
```

sudo mkdir /mnt/temp
sudo mount -text2 /dev/sdb1 /mnt/temp

```
Assuming you got no errors, try
```

mount

```
to see if the new drive is mounted, and follow that by
```

df -h

```
to get the available diskspace. Assuming this all works, you can add something like the following to your /etc/fstab file to make the mount happen automatically during boot.
```

/dev/sdb1      <MOUNT-PATH>       ext3      defaults       1    2

```
<MOUNT-PATH> here is a location of your choice, it could be something like "/media/external" or "/mnt/external"..

---

### Post by Inxsible on 2007-05-04
> **astrauss said:**
> OK, I know I'm not giving you detailed info here, but it's a start. Windows cannot read HDD's formatted in ext3. I had a utility which allowed that to work, but it broke after installing Feisty.

I have installed [FS-Driver]("http://www.fs-driver.org/"), and i can read my EXT3 partitions from my internal drive.

---

### Post by Inxsible on 2007-05-04
Thanks Cypher.

yes, sdb1 is my external drive. I got no errors. 

One question before I modify the fstab however, Won't I require some UUID. i see that all the other mounts have some kind of alphanumeric code for the UUID key before the mount point.

Should I now delete the temp mount point i created under /mnt/temp ?

Also why doesn't it recognize as a simple USB drive like it did when it was in NTFS format ?

---

### Post by Inxsible on 2007-05-04
I just restarted my machine and now I cant see my external drive again.

neither in /mnt/temp nor in the location that i specified in the fstab: /media/WD500

I don't think it mounted automatically. Did I do something wrong ?

---

### Post by Cypher on 2007-05-04
OK..good to hear that it mounted without any issue, and yes you're right..you're going to need a UUID for that. I'm a little new to that concept, so lemme quickly read up on before I offer any unwise advice.

You can safely "rm -rf /mnt/temp" if you've "sudo umount /mnt/temp" already. 

I'm uncertain as to why it sees the drive any different based on the formatting of it. It should always be a USB drive..

Lemme get back to you on the UUID..
**UPDATE:**
Ok I'm back..:)
Type
```

sudo vol_id -u /dev/sdb1

```
This will give you the UUID for that device, so in the fstab you'd put something like
```

UUID=<big-string-of-UUID> /media/WD500 ext3 defaults,errors=remount-ro 0 1

```

---

### Post by Inxsible on 2007-05-04
> **Cypher said:**
> OK..good to hear that it mounted without any issue, and yes you're right..you're going to need a UUID for that. I'm a little new to that concept, so lemme quickly read up on before I offer any unwise advice.

You can safely "rm -rf /mnt/temp" if you've "sudo umount /mnt/temp" already. 

I'm uncertain as to why it sees the drive any different based on the formatting of it. It should always be a USB drive..

Lemme get back to you on the UUID..
**UPDATE:**
Ok I'm back..:)
Type
```

sudo vol_id -u /dev/sdb1

```This will give you the UUID for that device, so in the fstab you'd put something like
```

UUID=<big-string-of-UUID> /media/WD500 ext3 defaults,errors=remount-ro 0 1

```

Currently at work..Will try it first thing tonight !!

Thanks again Cypher !!

---

### Post by Cypher on 2007-05-04
You're very welcome and let us know how you do..

---

