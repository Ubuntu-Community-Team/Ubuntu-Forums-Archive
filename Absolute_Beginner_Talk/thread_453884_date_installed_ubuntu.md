---
title: "date installed ubuntu"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by Clay_Banger on 2007-05-24
is there a way to check the date that ubuntu was installed?

ive had a look through the logs, and i can only view todays, and i cant find anything in Kinfocentre. Also i have had a look in system settings and cant find anything.

---

### Post by vtel57 on 2007-05-24
Navigate to /boot/grub. Right click on the device.map file, choose Properties. On the "Basic" tab, look toward the bottom where it says when the file was modified. That date should probably be the date that you installed Ubuntu, when that file was initially created.

---

### Post by Clay_Banger on 2007-05-24
Thats just what I wanted. Thanks.

---

### Post by vtel57 on 2007-05-24
Keep in mind, Clay, it's not a fool-proof way to tell, but that file is one of the ones that gets created on install and should not have changed since then, other than to be accessed by the system. However, the original modified date is probably the date that you installed the OS. I checked this on three of my seven distros before posting it here. It's accurate on my system.

Luck!

---

