---
title: "When I turn my computer on..."
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by UFRaymond on 2008-04-07
**When I turn my computer on...**

The GRUB loader starts as normal.

Currently, I have both Windows XP and the latest version of Ubuntu installed.

In the GRUB loader, there are multiple options for Ubuntu; I always pick the Ubuntu version highest up in the list - I figure it must be the latest versions.

How do I get rid of all the extraneous Ubuntu versions between the latest version of Ubuntu and [at the very bottom] Windows XP?  Are all of these Ubuntu versions necessary?

Thanks,
Ray

---

### Post by tamoneya on 2008-04-07
```
sudo nano /boot/grub/menu.lst
```
Scroll down towards the bottom and delete the sections that add the two extraneous boot options

---

### Post by apothecaryaaron on 2008-04-07
Better yet, comment them out (add a ' # ' ) in front of them.  You might want them later.  I just moved mine to the bottom of the list with a copy and paste.  You never know when a recovery mode or mem-test will come in handy.

---

### Post by kpkeerthi on 2008-04-07
> **UFRaymond said:**
> **When I turn my computer on...**

The GRUB loader starts as normal.

Currently, I have both Windows XP and the latest version of Ubuntu installed.

In the GRUB loader, there are multiple options for Ubuntu; I always pick the Ubuntu version highest up in the list - I figure it must be the latest versions.

How do I get rid of all the extraneous Ubuntu versions between the latest version of Ubuntu and [at the very bottom] Windows XP?  Are all of these Ubuntu versions necessary?

Thanks,
Ray

[http://ubuntuforums.org/showpost.php?p=4544561&postcount=8](http://ubuntuforums.org/showpost.php?p=4544561&postcount=8)

---

