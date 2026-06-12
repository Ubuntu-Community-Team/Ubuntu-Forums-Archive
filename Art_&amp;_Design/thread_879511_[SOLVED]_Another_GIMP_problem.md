---
title: "[SOLVED] Another GIMP problem"
date: 2008-08-04
forum: Art &amp; Design
---

### Post by Dopski on 2008-08-04
GIMP seems working! But actually not working! No tool is working! I don't know how this happened. GIMP previously work then just stop working without any hint why?

I am using Hardy Heron on my Celeron 2.53Ghz, 2GB Ram, Nvidia FX 5500 video card with 246 Video memory with restricted video driver in use and working fine. 

I tried to run GIMP in terminal and here is the output:



(gimp:5967): Gimp-Base-CRITICAL **: temp_buf_resize: assertion `width > 0 && height > 0' failed

(gimp:5967): Gimp-Base-CRITICAL **: temp_buf_resize: assertion `width > 0 && height > 0' failed

(gimp:5967): Gimp-Base-CRITICAL **: temp_buf_resize: assertion `width > 0 && height > 0' failed

(gimp:5967): Gimp-Base-CRITICAL **: temp_buf_resize: assertion `width > 0 && height > 0' failed

(gimp:5967): Gimp-Base-CRITICAL **: temp_buf_resize: assertion `width > 0 && height > 0' failed

(gimp:5967): Gimp-Base-CRITICAL **: temp_buf_resize: assertion `width > 0 && height > 0' failed

(gimp:5967): Gimp-Base-CRITICAL **: temp_buf_resize: assertion `width > 0 && height > 0' failed

(gimp:5967): Gimp-Base-CRITICAL **: temp_buf_resize: assertion `width > 0 && height > 0' failed






I hope someone here could help me restore my GIMP to its useful state.

Thank you.

---

### Post by loell on 2008-08-04
try using a fresh config

first backup it up

```
cp -rf  .gimp-2.4/ temp_gimp_config
```

then remove it

```
rm -rf .gimp-2.4/
```

then start gimp.

---

### Post by ajgreeny on 2008-08-04
You can do all this in nautilus if you find it easier, by making sure hidden files and foldersv are visible with Ctrl+H then just right click on the folder .gimp-2.4 and rename it to .gimp-2.4backup.  Now restart gimp.

---

### Post by Dopski on 2008-08-04
Thank you. I will try that.

---

### Post by Dopski on 2008-09-02
Found out that the problem is caused by the configured mouse directive from my xorg.conf file. 

Edited my xorg.conf and added the necessary directive for my wacom device.

Now my GIMP is working! as well as my wacom!

---

