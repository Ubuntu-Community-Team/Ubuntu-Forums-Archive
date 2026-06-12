---
title: "How do I save a change in .xorg.conf ?"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-04-12
[FONT=monospace]I need to save a change in /etc/X11/**xorg.conf**.

I tried changing my device driver from fglrx to vesa. However, I cannot figure out how to save the change. There is no "save" or "save as" under file. Any suggestions would be greatly appreciated. 
kh

Thanks for the quick replies.
kh
[/FONT]

---

### Post by aysiu on 2007-04-12
This will help you:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

By the way, it's /etc/X11/xorg.conf, not /etc/x11/xorg.conf

Case matters.

---

### Post by KitChy on 2007-04-12
If you do sudo gedit /link/to/file/here it will then allow you to save the file...I think!

---

### Post by aysiu on 2007-04-12
> **KitChy said:**
> If you do sudo gedit /link/to/file/here it will then allow you to save the file...I think!
Or, better yet... ```
gksudo gedit /etc/X11/xorg.conf
``` More details on *sudo* vs. *gksudo*:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

