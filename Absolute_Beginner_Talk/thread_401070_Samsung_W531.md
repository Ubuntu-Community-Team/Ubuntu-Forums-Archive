---
title: "Samsung W531"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by TheMono on 2007-04-04
I recently bought a Samsung W531 Mobile. It comes with a USB cable, and supposedly works as a standard USB mass storage device. lsusb gives 'Samsung Electronics co., Ltd Z100 Mobile Phone' as a result, but I can't mount anything (I'm using Kubuntu)

Any ideas how I could mount?

---

### Post by ajgreeny on 2007-04-04
pmount should mount it automatically if it is recognised as a standard usb drive.  Are you sure it is not already mounted?  look in /media/sd*, the * will vary, probably, depending on your system, but it may already be there waiting for you.  It should also show on the desktop if your system is set to show usb drives.

---

### Post by TheMono on 2007-04-04
Solved - It was my own stupid fault. If you go into the menu in the phone (9 - 6 - 1 for anyone who has one), you have to put it into PC connect mode. Then, yes, it does pick up as a standard USB drive.

---

