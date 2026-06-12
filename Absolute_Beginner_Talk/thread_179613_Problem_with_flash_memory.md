---
title: "Problem with flash memory"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by dontpanic0 on 2006-05-20
Yesterday I shut down my computer with my card reader and the memory card plugged into my computer.  Now, when I plug it in, I can see the disk drives, but not the card in the drive.  This also happens with my flash memory stick, but that card isn't even removable!  On the same computer, when I boot windows, they work fine.  

Thanks in advance,
Dontpanic0

---

### Post by Klaidas on 2006-05-21
I guess linux didn't like when you didn't unmount it :/
When you plug in, try mountinng the card manually (using terminal). Post here how it worked :-|

---

### Post by dontpanic0 on 2006-05-21
OK, but one problem, I'm new to linux and I don't know how to unmount using the terminal.  How do I do that?

---

### Post by DSn0wMan on 2006-05-21
[QUOTE=dontpanic0]OK, but one problem, I'm new to linux and I don't know how to unmount using the terminal.  How do I do that?[/QUOTE]

You can use the umount command in the terminal

```
umount /dev/name_of_your_device
```

sorry in the case of USB it might be /media/name_of_your_device

ie /media/usbdisk

you can type
```
more /etc/mtab 
``` to see a listing of devices

---

### Post by Klaidas on 2006-05-21
No problem :) It's
```
sudo umount /dev/your_usb_flash
```

---

### Post by dontpanic0 on 2006-05-21
I looked in the /media folder, it wasn't there.  When I do properties on the drive in 'computer' it says that it is not mounted.

---

