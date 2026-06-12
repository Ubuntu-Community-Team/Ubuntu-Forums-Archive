---
title: "root user on live cd, i need to run gparted"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by madhatter43 on 2007-07-01
is there a way to make myself a root user while running the live cd? i need to run gparted to claim the partitioned part of my hard drive back.

---

### Post by madhatter43 on 2007-07-01
i just re-read the message i get when i try to run GNOME partition editor and it says "failed to run gparted as user root. failed to exec new process: exec format error"

---

### Post by Seisen on 2007-07-01
You can try this

```
gksudo gparted 
``` in the terminal

---

### Post by madhatter43 on 2007-07-01
it still gives me the same message when i try that, and it wont close normally, i have to force a quit

---

### Post by madhatter43 on 2007-07-01
::tear::

---

### Post by Raineer on 2007-07-01
My guess would be that your CD is bad.  That error isn't stating that you aren't running as root, it's actually saying you **are** but for some strange reason it can't start another process.

---

### Post by Seisen on 2007-07-01
You could download the Gparted live-cd and use that.

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php") there is also a version that you download onto a usk key.

---

### Post by Raineer on 2007-07-01
> **Seisen said:**
> You could download the Gparted live-cd and use that.

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php") there is also a version that you download onto a usk key.

Probably the best advice, I've fallen in love with that CD.

---

### Post by madhatter43 on 2007-07-01
ill get the gparted live cd, but what is a usk?

---

### Post by Seisen on 2007-07-01
Its a typo its supposed to be usb.

---

### Post by madhatter43 on 2007-07-01
can you link the version i can boot off of a usb drive? im having trouble finding it, thank yuo for all the help so far as well.

---

