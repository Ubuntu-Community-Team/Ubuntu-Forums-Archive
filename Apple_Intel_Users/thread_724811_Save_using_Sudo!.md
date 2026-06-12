---
title: "Save using Sudo!"
date: 2008-03-15
forum: Apple Intel Users
---

### Post by JohnRowley on 2008-03-15
I have just edited /etc/x11/xorg.conf by opening the file and adding specific line to help the touchpad! I, however, now cannot save because i dont have the permission! I DONT want to login as root, i simply want a way to save this file. Any help as usual will be greatly appreciated!

Thanks

---

### Post by Khaine on 2008-03-15
This is what the sudo and su commands are for.  When you need root privileges to modify a file  you use sudo command /location/to/file eg in your case:

$sudo nano /etc/X11/xorg.conf

then you can edit the file and save it.  You cannot use sudo to raise the privileges of a command you have already run, which it sound like you want to do.

---

### Post by JohnRowley on 2008-03-15
Thank you so much :P

---

