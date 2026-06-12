---
title: "My ipod isn't autodetected."
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by Specter043 on 2007-08-15
My ipod used to automount, but now it doesn't.  I have no idea how to mount it now,, or even where it's supposed to be mounting.  I just know it used to show up on my desktop, and now it doesn't.  Any ideas to get it back?

---

### Post by Inxsible on 2007-08-15
Try and use pmount. Look at my signature for instructions on how to do that.

---

### Post by Specter043 on 2007-08-15
I read it, but I didn't really understand this part

where X = s or h
* = a,b,c...
?=1,2,3...

---

### Post by iver2435 on 2007-08-15
I think what he's saying is like if your iPod, when connected, has a device name of sdc1, then you would do:

```
sudo pmount /dev/sdc1 MOUNT_POINT
```


where X = s ,
* = c,
and
?=1

Hopefully that clears it up for you   :-)

---

### Post by Specter043 on 2007-08-15
What is an example of a good mount point for me to use?

---

