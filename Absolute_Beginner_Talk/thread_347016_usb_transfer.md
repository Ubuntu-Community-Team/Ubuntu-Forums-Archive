---
title: "usb transfer"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by Snoochi on 2007-01-26
this is odd but when i transfer files onto a usb disk in ubuntu by drag and drop the files dont stay there and when its re plugged into the system they are gone please help???????:confused:

---

### Post by taurus on 2007-01-26
Do you have permission to write to the USB drive and before you unplug it, try to unmount it first?

Applications -> Accessories -> Terminal
```
sudo umount /media/usbdrive
```

---

### Post by zerhacke on 2007-01-26
Before you pull out the USB disk, unmount it.  USB drives don't transmit data to disk like hard disks do.

---

### Post by Snoochi on 2007-01-26
thanks yes unmounting the drives works but is there no way to do it via gui than code not to be a philistine but im lazy that way :)

---

### Post by taurus on 2007-01-26
Right click on the drive and unmount it from there.

---

