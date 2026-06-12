---
title: "Mounting in XFCE"
date: 2005-12-25
forum: Absolute Beginner Talk
---

### Post by jbmalone on 2005-12-25
I just installed the XFCE desktop, and I love it.  However, in GNOME my external harddrive and usb card reader were noticed automatically.  How do I access and mount these drives in XFCE?  I just logged back into GNOME and they are there and everything is perfect.  Any help would be appreciated.  Thanks.

---

### Post by 23meg on 2005-12-25
See if running gnome-volume-manager helps. If it does, add it to your session startup.

---

### Post by kaamos on 2005-12-25
And when you have gnome-volume-manager running run "gnome-volume-properties" and disable nautilus popping up when an usb stick or hd is attached.

---

### Post by jbmalone on 2005-12-25
Thanks you guys.

---

### Post by Zelut on 2006-01-16
using the above how do you include something in startup using XFce?

---

### Post by robotgeek on 2006-01-16
[QUOTE=kuyaedz]using the above how do you include something in startup using XFce?[/QUOTE]
I believe that there should be a "save session" when you logout in xubunu. However, if that is not the case enable it from "Settings -> Sessions and Startup -> General -> Prompt on Exit" 

It should be saved, and the next time you login, it will launch automatically. 
[http://www.xfce.org/documentation/docs-4.2/xfce4-session.html](http://www.xfce.org/documentation/docs-4.2/xfce4-session.html)

---

