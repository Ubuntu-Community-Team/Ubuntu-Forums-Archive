---
title: "[SOLVED] External Drive issue"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-05-04
I had a 500 GB external drive in NTFS format. It used to connect as a USB drive.
 
I then formatted it to EXT3. Since then it is not recognized as a USB drive in Ubuntu as well as Vista
 
I was able to auto mount that drive in Ubuntu, but every time I start my computer and the drive is not connected, it gives me failure on the fsck.
 
1) Is there any way to tell Ubuntu, that it is an external USB drive?
 
2) I can see this drive as 'Disk 1' in the Disk Management Utility in Vista. But I cannot mount it and neither can I assign a drive letter to it. All options, except 'Delete Volume' are ghosted. I should mention that I have 3 primary partitions mounted in Vista and plus the DVD Drive. Is that the reason why it won't let me mount it in Vista, since i already have 4 drives ?
 
 
Can someone please help me use this drive as an External USB Drive ? ](*,)

---

### Post by taurus on 2007-05-04
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Inxsible on 2007-05-04
Would you believe that this time when I restarted my machine, it mounted as an USB Drive !!!!

I just hope it stays that way.

Although, Could you help me mount this in Vista?

my fdisk -l is 
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

---

### Post by taurus on 2007-05-04
If you want to view ext3 filesystem in Vista, try installing fs-driver from [http://www.fs-driver.org](http://www.fs-driver.org).

---

### Post by Inxsible on 2007-05-04
Yeah, I already have FS -Driver installed. My problem is that i cannot mount my external drive in Vista, even though its an external USB drive. When I boot into Vista, and then go to Disk Management, i can see the disk there labeled as Disk 1, but all options to mount it are ghosted.

Mebbe i should try booting in one more time. Hopefully like Ubuntu it will recognize it as USB this time. That is too much to ask of Vista...but lets see !!

---

