---
title: "How to get writing permisson to hfs+ on usb?"
date: 2011-10-21
forum: Apple Hardware Users
---

### Post by Azyx on 2011-10-21
I have an usb/fw disk with hfs+  partition on. In OS-X I have writing access, but not in Ubuntu.  Have installed hfsplus, hfsutils. But I don't have writepermission when it auto-mount on the desktop.

/Cheers

---

### Post by Azyx on 2011-10-21
When it get mounted ls -al give me this:

```
drwxr-xr-x  4 root root  4096 2011-10-21 16:48 .
drwxr-xr-x 22 root root  4096 2011-10-11 17:59 ..
drwxr-xr-x  1 root root     9 2011-10-21 16:47 230GB
drwx------  7 azyx    azyx    32768 1970-01-01 01:00 FREECOM HDD

```

Freecom is another usb with fat, and the system is read only.

---

### Post by pindar on 2011-10-21
Did you try switching off journaling on the hfs volume?

---

### Post by Azyx on 2011-10-21
> **pindar said:**
> Did you try switching off journaling on the hfs volume?

Why should i do that, and if i must, how do I do it?

---

### Post by pindar on 2011-10-23
> **Azyx said:**
> Why should i do that, and if i must, how do I do it?
Yes, why should you do that, and how? If only there were a way to look for information on the internet. Like a website where you could enter terms in a search box, and it would tell you about websites where these terms are used and explained...

---

### Post by Azyx on 2011-10-23
> **pindar said:**
> Yes, why should you do that, and how? If only there were a way to look for information on the internet. Like a website where you could enter terms in a search box, and it would tell you about websites where these terms are used and explained...

**Allright I take and search on another place there the disdinformations are not so big as in as here on this forum**! [B]And when i find the awnser I don't tell you that it.

Good bye!
[/B]

---

### Post by Azyx on 2011-10-23
To all but pindar

[http://raamdev.com/mounting-hfs-with-write-access-in-debian](http://raamdev.com/mounting-hfs-with-write-access-in-debian)

/cheers

---

