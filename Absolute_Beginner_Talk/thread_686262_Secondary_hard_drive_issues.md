---
title: "Secondary hard drive issues"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by Scott_L on 2008-02-03
Just installed Ubuntu 7.04 and upgrading to 7.10 as we speak, so far everything's working fine... well almost everything

 My secondary hard drive is recognized and I have access to it, I can open all the files that were on it but I am unable to actually delete anything or add anything to it, it says I do not have permission, How do I give myself permission?

Any help would be appreciated, thanks.

---

### Post by jaytek13 on 2008-02-03
```
sudo chown username:root /path/to/drive
```

This will make you the owner, although it seems you probably already are if you can read it.

```
sudo chmod 775 /path/to/drive
```

This will give you read and write permissions.

---

### Post by Scott_L on 2008-02-03
Thanks, but now ive got a new issue, upon restarting my PC after updating to 7.10, I am unable to mount that hard drive now

---

### Post by jaytek13 on 2008-02-03
Do you know what that drive is formatted as? 

You can find out doing

```
sudo fdisk -l
```

---

### Post by Scott_L on 2008-02-03
this is what I got 

```
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x10fb68cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *           2      969021   488386080    5  Extended
/dev/sdb5               2      969021   488386048+   7  HPFS/NTFS

```

Note: I can actually see the drive, But when I try to see the contents it tells me I am unable to mount it

---

### Post by jaytek13 on 2008-02-03
What does the content of your /etc/fstab look like? And can you mount it with sudo?

---

### Post by Scott_L on 2008-02-03
here's the contents of my fstab 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2d205621-5d9b-40ca-9b25-189bf0144279 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=78969c08-e489-4a57-b217-0abb3202702c none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

and I'm a noob to linux/ubuntu so I don't even know how to mount it with sudo

---

### Post by jaytek13 on 2008-02-03
Well, you can mount all available unmounted devices with 

```
sudo mount -a
```

Or, you can mount the device itself

```
sudo mount /dev/sda5
```

But from the looks of it it doesn't actually seem like you have a mount point for that... And even though fdisk is listing it as a ntfs drive in fstab it's listed as a swap partition... You say you could see the files before?

---

### Post by Scott_L on 2008-02-03
Couldn't mount it either way

When I first installed Ubuntu (7.04) I could see all the files and use them (Audio/Video files), Now I can't access the drive at all

---

### Post by jaytek13 on 2008-02-03
Is the update finished?

---

### Post by Scott_L on 2008-02-03
Yes, the update was finished and installed and my PC was restarted, it all occurred after the restart.

But it's okay now, I was able to force mount it and I now have full read and write privileges. Thanks for the assistance anyways.

---

