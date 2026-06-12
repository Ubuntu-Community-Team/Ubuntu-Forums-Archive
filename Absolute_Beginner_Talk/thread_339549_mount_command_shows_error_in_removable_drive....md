---
title: "mount command shows error in removable drive..."
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by mrdeeno on 2007-01-15
When I run the 'mount' command, i get an error on my removable drive:

/dev/hda5 on / type ext3 (rw,errors=remount-ro)


and on top of that, the drive used to be called usbdisk-1, but now it's named _PNG and there's a bunch of weird characters.

How do i fix this?

---

### Post by benuski on 2007-01-16
Did you accidently unplug it without ejecting the drive first?  I've done that once or twice, almost killing my drive.  If you did that, it might have corrupted your bootsector on the external drive.

Attach the disk, and keep it unmounted, and then run

```
sudo fsck.vfat -a /dev/sda1
```

replacing "sda1" with wherever it is mounted.  I am assuming that you're running FAT32 on this drive.  It will tell you if the bootsector is corrupted, and will allow you to restore it from the backup.

---

