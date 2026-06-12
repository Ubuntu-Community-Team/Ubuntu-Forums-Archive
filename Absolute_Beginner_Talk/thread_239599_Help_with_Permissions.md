---
title: "Help with Permissions"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by canarsie on 2006-08-19
I have 4 partitions on my hard drive, boot, root, swap and an extra one for media files (called data).  I can copy files into the data partition, but I can't play them.  The properties for the folder says any user can read it, but each individual file says it can only be read by the root user.  Any advice?

---

### Post by jordilin on 2006-08-19
Type:
```
sudo -i
```
and enter your password
Go into the problematic directory and type
```
chown yourusername:yourusername *
```
and all these files will be owned by you and not by root.
Hope that helps :mrgreen:

---

### Post by Dinerty on 2006-08-19
[http://psychocats.net/ubuntu/mountlinux.html](http://psychocats.net/ubuntu/mountlinux.html)

At the bottom of the page shows a nice little piece on permissions, i used it myself, so can clarify it works :)

---

### Post by canarsie on 2006-08-19
Yeah it's working fine now... thanks guys.

---

