---
title: "mp3 usbdisk"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by none211 on 2007-02-01
I'm having trouble with my mp3 player. i'm trying to load it up with songs and I can't. if I plug it in a usb port the icon appears on my desktop but when I double click it, i see nothing on it and that's fine, but there's plenty on it. i can't seem to find out how to view files and work with them on the usb drive even when I have the thing open. can anyone help?

---

### Post by taurus on 2007-02-01
Applications -> Accessories -> Terminal
```
sudo umount /dev/sda1
sudo mount -t vfat /dev/sda1 /media/usbdisk -o iocharset=utf8,umask=000
ls -la /media/usbdisk
```

---

### Post by none211 on 2007-02-01
i tried to unmount and mount, that worked, but when i look through the device, i see nothing. when I disconnect it i have a load of songs on it. wasaaabi? I'm confused

---

### Post by none211 on 2007-02-01
does anyone have suggestions?

---

### Post by shareMenaPeace on 2007-02-01
when you got the file browser open with the mp3 device go to the options and check under view -- view hidden files?

---

### Post by .plaid on 2007-02-01
The routine questions:

1. Has it ever worked on this set up? 

2. If so, have you made any hardware or software changes recently?

Not so helpful to you, but maybe it'll get the juices flowing for the next guy, who will certainly be smarter than me....

.

---

### Post by none211 on 2007-02-01
there dosen't seem to be a show hidden files under an options menu

---

### Post by none211 on 2007-02-01
sorry. I didn't look hard enough

---

### Post by shareMenaPeace on 2007-02-01
I meant "view" from the menu.

---

