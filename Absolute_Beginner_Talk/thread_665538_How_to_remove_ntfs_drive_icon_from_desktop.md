---
title: "How to remove ntfs drive icon from desktop?"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-01-12
Thank you for reading my post
Can some one please let me know how i can remove my ntfs drive icons from my desktop and let them be mounted in the same time?
for example when I open Computer from places i see all of ntfs icons but not on my desktop?
Thanks.

---

### Post by fiddledd on 2008-01-12
Edit your gconf the option to show hide volumes on desktop is there, as well as many others. I'm not using Ubuntu atm so I can't rememeber the exact location in gconf but I think its nautilus->desktop. Gconf editor is in your applications menu under system, if you can't see it just right click main menu and selck Edit Menu, then check it so it shows.

---

### Post by linux phreak on 2008-01-12
Editmenu>System tools>Configuration editor.In that go to apps>nautilus>desktop.Uncheck 'Volumes visible'.

---

### Post by legolas_w on 2008-01-12
Thank you for reply.
But my system does not have that System tools>Configuration editor software installed, at least I can not find it in the menu which is placed in top of the screen.

Any other solution?

Thanks

---

### Post by pagef4ult on 2008-01-12
read this one 

> [http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/](http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/)

---

### Post by fiddledd on 2008-01-12
> Gconf editor is in your applications menu under system, if you can't see it just right click main menu and selck Edit Menu, then check it so it shows.

Did you try what I said?

---

### Post by linux phreak on 2008-01-12
> **legolas_w said:**
> Thank you for reply.
But my system does not have that System tools>Configuration editor software installed, at least I can not find it in the menu which is placed in top of the screen.

Any other solution?

Thanks

All you have to do is rightclick on the main menu on top of screen and click 'edit menus'.

---

