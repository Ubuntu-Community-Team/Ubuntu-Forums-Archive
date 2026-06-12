---
title: "Added 2nd EXT3 drive and can't write [Resolved]"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by getut on 2006-12-03
Ok... I added a second hard drive to my new system, made it one big partition and formatted it EXT3. I have it mounted in a mount point, but can only write to the drive as root.

I followed a guide that said that I needed to do a sudo chmod 777 on the mount point folder which I did, but I still can't write to the folder(drive) as my normal logged on self.

This is line I added to my fstab file:
/dev/sdb1 /media/media_drv ext3    default 0 0

Please help.

---

### Post by bodhi.zazen on 2006-12-03
> **getut said:**
> Ok... I added a second hard drive to my new system, made it one big partition and formatted it EXT3. I have it mounted in a mount point, but can only write to the drive as root.

I followed a guide that said that I needed to do a sudo chmod 777 on the mount point folder which I did, but I still can't write to the folder(drive) as my normal logged on self.

This is line I added to my fstab file:
/dev/sdb1 /media/media_drv ext3    default 0 0

Please help.

That is quite odd. Unmount and re-mount the partition.

If you can not write yet, can you check the output of:
```
ls -lah /media
```

---

### Post by getut on 2006-12-04
Ahh.. how stupid of me. A reboot fixed it.

The walkthrough I used said to do a sudo mount -a and that should get it going. It didn't.

After rebooting though everything is working normally. Thank you.

---

