---
title: "Copy image to USB drive"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by _rob_ on 2006-03-13
I am trying to copy an image file to a USB drive (Breezy) in order to softmod an Xbox for linux install.  

The HOWTO ([http://www.xbox-linux.org/wiki/Software_Method_HOWTO#Copying_the_MechInstaller_Files_on_a_USB_Memory_Stick](http://www.xbox-linux.org/wiki/Software_Method_HOWTO#Copying_the_MechInstaller_Files_on_a_USB_Memory_Stick)) says to: "remove usb-storage module with modprobe -r usb-storage in order to enable write of disk image".

But after I do that (similar to how it says to), I cannot "cat" the image to /dev/sda(1).  I think that the error says it's not there.

Any ideas?  Thanks!

---

### Post by stuporglue on 2006-03-13
```
The HOWTO (http://www.xbox-linux.org/wiki/Softw...B_Memory_Stick) says to: "remove usb-storage module with modprobe -r usb-storage in order to enable write of disk image".

But after I do that (similar to how it says to), I cannot "cat" the image to /dev/sda(1). I think that the error says it's not there.
```

Instead of removing the module, just make sure all partitions of the disk are unmounted. The modprobe -r stuff is just to make sure you're not imaging a device that's in use.

---

### Post by _rob_ on 2006-03-13
Thanks.  I'll give it a try.

---

