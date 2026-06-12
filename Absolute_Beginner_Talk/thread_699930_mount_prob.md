---
title: "mount prob"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by moondoggy17 on 2008-02-17
im. trying to mount an iso image but can not fig. out this last part of the code
```

mount -t iso9660 -o loop <Image_File> <Mount_Point>
```

its the last part that i'm having trouble with 
what is the mount point

---

### Post by freebeer on 2008-02-17
it's where you want it to mount under your file system.  If you want it under /home you can create a folder called "imagedisk" (or whatever you like) then your mount point would be /home/imagedisk.

---

### Post by Origin415 on 2008-02-17
The mount point is the folder you want the data in the iso file to appear at.

I personally have a folder /media/iso to mount it, as Gnome will automatically show an icon on the desktop when an iso is mounted there (or anywhere in the /media folder)

Make a folder to mount the iso to,
```
sudo mkdir /media/iso
``` 
for instance, and use that directory as the mount point.

---

### Post by moondoggy17 on 2008-02-17
ok that worked but not how i wanted, dose anyone a daemon tools style mount and whats the un-mout code

---

