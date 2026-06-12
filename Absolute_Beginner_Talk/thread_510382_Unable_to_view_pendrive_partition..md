---
title: "Unable to view pendrive partition."
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by r4ndom on 2007-07-26
i have a usb micro sd reader in which i created a 50mb ext3 file system to backup my data. Having reinstalled windows i cannot find the data which is very important to me as it is my own code. After a bit of digging I have discovered that the drive that appears empty in the gnome file explorer thingy is actually missing 50mb of space from where it says the capacity. I then look at the usb device as a whole in gparted and it appears as one partition with 50mb of used space. So i would be very grateful if someone could help me restore my data if you need anymore info feel free to ask.

---

### Post by phr0ze on 2007-07-26
I don't see where windows comes into play with all this but windows can not natively read ext3. To use it in ubuntu it just needs to be properly mounted. Unfortunately I don't know the commands off the top of my head.

---

### Post by r4ndom on 2007-07-27
> **phr0ze said:**
> I don't see where windows comes into play with all this but windows can not natively read ext3. To use it in ubuntu it just needs to be properly mounted. Unfortunately I don't know the commands off the top of my head.

well I also installed windows along with ubuntu and if thats true that it just needs correctly mounting I'll have a look although I don't think its as simple as that as gparted sees it as a single partition and the gnome explorer only mounts one partition which is 50mb less than the capacity of the pendrive.

EDIT: an attempt which resulted in another mount with a missing 50mb

```

george@george-desktop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           20056       30401    83104245    5  Extended
/dev/sda3           12749       20055    58693477+  83  Linux
/dev/sda5           30147       30401     2048256   82  Linux swap / Solaris
/dev/sda6           20056       30146    81055894+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1015 MB, 1015808000 bytes
32 heads, 63 sectors/track, 984 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         984      991840+   6  FAT16
george@george-desktop:~$ sudo mount /dev/sdb1 /media/usb
mount: mount point /media/usb does not exist
george@george-desktop:~$ sudo mkdir /media/usb
george@george-desktop:~$ sudo mount /dev/sdb1 /media/usb
george@george-desktop:~$ 


```

Im getting the feeling that it is simply impossible to create more than one partition on a micro sd therefore I'll have to just reformat and start again could someone clarify this please.

---

### Post by r4ndom on 2007-07-27
sorry for the bump but I've noticed almost every thread that is not solved in the second post is ignored by everybody for example this thread [http://ubuntuforums.org/showthread.php?t=506873](http://ubuntuforums.org/showthread.php?t=506873) there needs to be some thing where you can mark your thread as solved or something

---

### Post by r4ndom on 2007-07-27
Ok well seen as I'm not getting any help here I'll leave the partition until maybe one day I will be more learned in linux and I'll be able to recover it and laugh at how I sucked at coding.

---

