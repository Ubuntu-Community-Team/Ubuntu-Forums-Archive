---
title: "&quot;Cannot eject volume&quot;"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by EleFlameMax on 2007-12-12
I'm trying to eject a cd but it's telling me that I "cannot eject volume". Argh.

---

### Post by Rocket2DMn on 2007-12-12
If it's on your desktop, right click the icon and try to eject or unmount from there.  If that fails, try unmounting it manually (assuming it's mounted at /media/cdrom):
```
sudo umount /media/cdrom
```
If that still fails, you may just have to force it out with a bent paperclip in the emergency eject hole.

---

### Post by CREEPING DEATH on 2007-12-12
I had the same problem the other day, except I fixed it with ```
sudo umount /dev/cdrom
```

CD

---

### Post by rockinlinux on 2007-12-12
does it happen all the time or is this the first time?  chances are your drive is not mounted in /media rather in /dev so the second one that CREEPING DEATH said most likly will be correct. also like  was said already try to right click> unmount volume and then press the eject boot on the drive. if either of these do not work then reboot, if it still wont unmount then make a paper clip straight and there is a small hole on the front of the drive. carefully insert the straintened paper clip and push (you will feel resistance) and the drive will open so you can have your disk back.

---

### Post by Rocket2DMn on 2007-12-12
> **rockinlinux said:**
> does it happen all the time or is this the first time?  chances are your drive is not mounted in /media rather in /dev so the second one that CREEPING DEATH said most likly will be correct. also like  was said already try to right click> unmount volume and then press the eject boot on the drive. if either of these do not work then reboot, if it still wont unmount then make a paper clip straight and there is a small hole on the front of the drive. carefully insert the straintened paper clip and push (you will feel resistance) and the drive will open so you can have your disk back.

It's not mounted at /dev - that is where you see the device though.  It works to unmount from the /dev directory as well.

---

