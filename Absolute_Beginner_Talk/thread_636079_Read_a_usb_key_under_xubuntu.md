---
title: "Read a usb key under xubuntu"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by Asimov4 on 2007-12-09
Hello everybody!
I've recently installed xubuntu on an old computer (bought in 1999, pentium II) that could read usb keys under windows xp. But now that I've installed xubuntu I can't find how to browse my usb key.
Their doesn't seem de be any usb folder in the media folder, and I tried fdsik that only displayed hard drive partitions.

Could you help me?

---

### Post by ddrplayer512 on 2007-12-09
Does the USB key's read/write light flash when you insert it?

---

### Post by nsilva on 2007-12-09
try this to see all the USB devices connected to the computer
```
lsusb
```

Also you might look a the system messages when u connected
```
dmesg
```

Let me know

---

### Post by Asimov4 on 2007-12-09
Thanks for your solutions, but actually I tried another usb key that worked perfectly.

The first one was quite old, maybe that was the problem.

---

