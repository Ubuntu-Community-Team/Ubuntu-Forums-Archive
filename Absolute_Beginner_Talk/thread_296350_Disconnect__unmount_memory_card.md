---
title: "Disconnect / unmount memory card"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by matt_b on 2006-11-09
I have an inbuilt memory card reader in my laptop. When in Windows XP I used to have to "eject" the card in windows before physically removing it otherwise I risked data corruption (according to windows). Is the same true in Linux/Ubuntu? If so, where do I go to dismount/unmount the card? In XP I had an icon in the system tray which I had to right-click...

Thanks
matt

---

### Post by bodhi.zazen on 2006-11-09
Yes. You can do it from the GUI in Linux as well. It is called "unmount".

From the CLI:```
sudo umount <mount_point>
```
Yes, umount (one n) NOT unmount not two n's.

---

### Post by qscgz on 2006-11-09
If you insert a pen drive an icon will be placed on the desktop. To unmount/ eject make a right mouse click at the icon and use the "eject" entry. Should be the same with a smart card media.

---

### Post by matt_b on 2006-11-09
Thanks for that - can't believe I missed it! I scanned through the right-click options but missed the obvious "eject" entry!

---

### Post by .t. on 2006-11-09
Don't use umount if it's removable media. Use "eject <device>". umount doesn't tell the device it's happy to be removed, or turn off the power; even if it is ready.

---

