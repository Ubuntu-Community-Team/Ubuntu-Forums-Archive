---
title: "problem with permissions"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by oscar78 on 2006-12-21
I'm trying to execute the following command:  

andy@andy-desktop:~$ sudo md5sum /etc/X11/xorg.conf >/var/lib/x11/xorg.conf.md5sum 
bash: /var/lib/x11/xorg.conf.md5sum: Permission denied

but even with sudo I still do not have permission.  Is there a way to get around this?

Thanks

---

### Post by Hurricane on 2006-12-21
Hi there.

Try the following, worked for me:

md5sum /etc/X11/xorg.conf > sudo /var/lib/x11/xorg.conf.md5sum 

Hope that helps.

---

### Post by oscar78 on 2006-12-21
Thanks!

---

