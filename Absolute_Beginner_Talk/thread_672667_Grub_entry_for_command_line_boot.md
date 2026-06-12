---
title: "Grub entry for command line boot"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by dmitrijledkov on 2008-01-19
How do I add a new boot option in grub so that I boot into (x)Ubuntu into command line without X AND it will request me to login.

I tried recovery mode boot option, but I don't like it since it's root and I can't login into my account.
I did ```
login
``` it asked me for and Authorisation cookie don't know what that is.

---

### Post by ikex on 2008-01-21
You could, edit a new runlevel without X 

> In Debian/Ubuntu, the default runlevels 2-5 are identical (runlevel 2 is 
the default).  This allows one to create customized levels if desired.  
For example, removing the S13gdm symbolic link from /etc/rc2.d will 
allow the system to boot into a virtual console instead of X. 

then edit menu.lst for grub (im not to sure if grub can change runlevel @ boottime) but apperntly LILO can, or if worse came to worse telinit <run level> from the recovery mode to boot into that runlevel.

---

