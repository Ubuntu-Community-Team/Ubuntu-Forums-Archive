---
title: "libgpod link"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by MrGreen on 2007-08-29
Hi,

I have loaded gtkpod-aac no problem but keep getting 

ldconfig: /usr/lib/libgpod.so.0 is not a symbolic link

when trying to run gtkpod...

Is there a way to fix this ie clear out packages out reload them?

the file its pointing to is a regular file not a link?

MrG

---

### Post by MrGreen on 2007-08-29
Tia

---

### Post by Perfect Storm on 2007-08-29
Try with
```

sudo ln -s /usr/lib/libgpod.so.1 /usr/lib/libgpod.so.0

```

---

### Post by MrGreen on 2007-08-29
Thank you ;-)

---

### Post by Perfect Storm on 2007-08-29
My pleasure.

Enjoy.

---

