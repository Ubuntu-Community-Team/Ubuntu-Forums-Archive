---
title: "having issues mounting on Kubuntu"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by Ryupower on 2006-10-29
Hi :)

I'm having trouble mounting on Kubuntu. I want to use fstab, since this worked easily on Ubuntu. :)

I am NEW to KDE! First time Kubuntu! First time KDE!
so....

I type:
/etc/fstab

what do I get?

Permission denied

Then I try it again with the root shell:
/etc/fstab

PERMISSION DENIED.


So...what am I doing wrong that it won't let me open it?

---

### Post by ReaderRat on 2006-10-29
You have to tell it what you want to do with it. Like 
```
sudo gedit /etc/fstab
``` 
to edit it.

---

### Post by eriefisher on 2006-10-29
What are you trying to mount?? Konqueror always asks what you want to do when connect a usb drive or insert a cd/dvd etc.

eriefisher

---

### Post by Ryupower on 2006-11-05
another partition. :)

NVM, problem solved. ^^
thanks!

---

