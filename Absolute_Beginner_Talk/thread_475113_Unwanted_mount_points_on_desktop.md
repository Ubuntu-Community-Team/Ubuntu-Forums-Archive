---
title: "Unwanted mount points on desktop"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Sparkster185 on 2007-06-15
Hello,

I am new to Gnome (been a Kubuntu user since I switched to Linux).  I recently installed ubuntu-deskop and I like it so far, but I have one small problem.

I have two Windows partitions on the same HD that my root folder is on.  Gnome decided to put icons for each of these partitions on my desktop.  I would like to remove them but I can't seem to figure out how. 

Thanks in advance,
Sparkster

---

### Post by mikewhatever on 2007-06-15
Hit Alt+F2 and type gconf-editor. Navigate to apps>nautilus>desktop and uncheck desktop icons.

---

### Post by Golyadkin on 2007-06-15
The option you are looking for is called "volumes visible".

---

### Post by Sparkster185 on 2007-06-15
That's exactly what I wanted.  Thanks.

---

### Post by Golyadkin on 2007-06-16
You are welcome! I remember when I wanted to get rid of them the first time, the only way I knew how was to unmount them :D

---

### Post by PhutterMan on 2007-06-20
Is there any way (other than unmounting) to do this selectively?  For instance, I'd like it if an icon came up on my desktop when I put in a usb drive or attach a portable hard drive, but I'd rather not have an icon for my Windows install partition sitting on my desktop all the time.  Should I just look into preventing it from mounting, instead?

Commenting it out in fstab didn't work; with that done it just seems to mount a little later and have a different name.  I have no need to mount it, I have a different shared partition for exchanging stuff between the two OSes, but how do I stop it from mounting?!

Any advice is appreciated.  Thanks!

---

