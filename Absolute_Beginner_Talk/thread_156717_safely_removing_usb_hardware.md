---
title: "safely removing usb hardware"
date: 2006-04-07
forum: Absolute Beginner Talk
---

### Post by abbrew on 2006-04-07
Is it necessary to somehow safely remove things that are linked via usb?  In Windows XP (which I stopped using a few months ago when I found Ubuntu) I would always click this thing that would stop the usb drive and say I can unplug it it is "safe to remove".  Should I do something similar in Ubuntu?  What is the unmount thing I see when I right click a usb object?  Is that the same?  --- Thanks for the help!

---

### Post by aysiu on 2006-04-07
Unmounting a device is the same as safely removing it.

---

### Post by kelinu on 2008-03-21
When unmounting a device, it has the exact same effect as safely remove hardware in XP.  Remember to always unmount before removing a device to avoid errors/crashes.

Hope this helps,
Michael

---

### Post by jose158 on 2008-03-21
> **kelinu said:**
> When unmounting a device, it has the exact same effect as safely remove hardware in XP.  Remember to always unmount before removing a device to avoid errors/crashes.

Hope this helps,
MichaelWay to open up a 2 year topic:lolflag:

---

### Post by billgoldberg on 2008-03-21
In case you don't know how to unmount: right-click the drive icon (either on the desktop, or in the file manager) and press unmount. A box will appear in the bottom right corner telling you it's safe or not safe to remove it.

---

### Post by billgoldberg on 2008-03-21
> **jose158 said:**
> Way to open up a 2 year topic:lolflag:

Haha, didn't notice it.

:lolflag:

---

### Post by stevieP on 2008-06-18
Or if you're a command line person:

% sudo umount /media/disk

or whatever the name of the usb device is. 

(3 months old I know :) )

---

