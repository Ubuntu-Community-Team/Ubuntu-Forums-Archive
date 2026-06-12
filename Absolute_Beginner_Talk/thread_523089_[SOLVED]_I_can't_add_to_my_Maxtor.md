---
title: "[SOLVED] I can't add to my Maxtor"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by Murtadh on 2007-08-11
Hi

I use my Maxtor one touch III with my windows perfectly, but with Ubuntu I can only read, so is there a way to give the permission to  to add files in it normally :confused:

---

### Post by insane_alien on 2007-08-11
its likely formatted in ntfs. 

there is an ntfs driver (ntfs-3g i believe) but i'm not sure if it is stable or if it is still sketchy.

---

### Post by testube_babies on 2007-08-11
It's stable, all you have to do (on Feisty or newer) is
```
sudo apt-get install ntfs-config
``` and then a configuration tool will show up in your applications menu to let you write to NTFS.

---

### Post by Murtadh on 2007-08-12
I install it, and all what I needed to do more is to make a chdsk to my Maxtor with windows and now everything work perfect. **Thanks**.

---

