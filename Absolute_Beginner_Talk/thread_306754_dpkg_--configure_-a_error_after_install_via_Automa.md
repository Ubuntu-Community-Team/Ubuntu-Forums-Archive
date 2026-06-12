---
title: "dpkg --configure -a error after install via Automatix"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by pollywog on 2006-11-25
I just installed Ubuntu 6.10, and attempted to download a few programs via Automatix. After attempted install I get an error message telling me that I must manually run ' dpkg --configure -a ' . I cut and paste this command into the terminal, and it comes back telling me that " requested operation requires superuser privilage". I performed the install, and I am the only user, so who is this superuser, and how can I get them the run this script for me?

---

### Post by ReaderRat on 2006-11-25
```
sudo dpkg --configure -a
```

[How **sudo** Works](http://www.ubuntuforums.org/showthread.php?t=275605)

---

### Post by pollywog on 2006-11-25
thanks, you're a lifesaver!-interesting link

---

