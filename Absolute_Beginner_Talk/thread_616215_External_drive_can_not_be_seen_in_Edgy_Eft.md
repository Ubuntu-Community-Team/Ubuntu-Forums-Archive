---
title: "External drive can not be seen in Edgy Eft"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by Tonechiller on 2007-11-18
Hi,
I am running Edgy Eft and I have a laptop hard drive in an external USB2.0 case.  I have formated two partitions on it a 30G FAT32, and a 50G NTFS.  I have written data to it under Win XP, and I now intend to use it to back up data on my Edgy Eft machine.  Problem is it does not auto mount and when I do a "sudo fdisk -l" I do not see the drive anywhere?  I check the file system and under /dev, there is not anything starting in "sd", so I feel that Edgy Eft does not even see this drive.  I have a 2G memory stick that works just fine, auto mounts and all.

Can anyone please point me in the right direction?  I have checked these forums, but most of the similar threads, show using the "sudo fdisk -l" command to find the drive and manually mount it.  All I see are the three partitions that Edgy Eft installs.

Cheers,
Tone

Additional, I have installed ntfs-3g, just on the off chance that Edgy Eft will see the NTFS partition instead of the FAT32 one.

---

### Post by Qwerty_ on 2007-11-18
Since you have installed ntfs-3g try installing ntfs-config.

```
 sudo apt-get install ntfs-config
```

Then run

```
 sudo ntfs-config
```

Select your required options, hopefully that will help you.

---

### Post by Tonechiller on 2007-11-22
Thanks,
When I try this it says "Package not found"  I typed it just as you put it, maybe I am missing something on my distro?

Is there any other way to check my usb devices?

Cheers,
Tone.

---

