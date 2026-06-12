---
title: "Firefox not loading thumbnails properly"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by amazingtaters on 2008-03-25
So, when I try to load most images in firefox, I get a problem best expressed by pictures...

The first picture is before the image is expanded to full size, the second is what it should look like. So, does anyone know why this happens?

---

### Post by c-ron on 2008-03-26
Hi, if you want to disable Firefox's image resizing feature, type about:config in the address bar and press Enter. Find the entry for browser.enable_automatic_image_resizing, doubleclick it to change it to ' false'.

See below for a fix.

---

### Post by c-ron on 2008-03-27
The possible fixes (work-arounds) are to install the restricted binary drivers for your card,

OR,

In /etc/X11/xorg.conf add to the Device: section:: 
```
Option "AccelMethod" "EXA"
Option "MigrationHeuristic" "greedy"
```

---

### Post by amazingtaters on 2008-03-28
That would be solid if I was using an NVidia card but my lappy has a Radeon XPress 1100.

---

### Post by c-ron on 2008-03-29
AFAIK, adding those options to xorg.conf will work for cards other than NVDIA's.

---

