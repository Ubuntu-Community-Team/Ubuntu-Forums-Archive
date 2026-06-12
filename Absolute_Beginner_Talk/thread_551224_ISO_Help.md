---
title: "ISO Help"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by Tootles on 2007-09-14
i have a iso file i want to mount, how do i do it in terminal

---

### Post by llamakc on 2007-09-14
With the loopback device.

sudo mount -o loop /path/to/file.iso /path/to/where/you/want/to/mount

so something like:

sudo mount -o loop ~/disc.iso /media

would work. Then just "cd /media" to start browsing the files.

---

### Post by psusi on 2007-09-14
Do not mount things directly in /media.  Auto detected devices which show up on your desktop are mounted in /media, so make a new directory for it under media and mount it there, and it will show up on the desktop.

---

### Post by [Alsharifi] on 2007-09-15
u want to burn a .ISO file onto a disc?

put the blank disc in,right click the file and burn to disc?

---

### Post by llamakc on 2007-09-15
> **psusi said:**
> Do not mount things directly in /media.  Auto detected devices which show up on your desktop are mounted in /media, so make a new directory for it under media and mount it there, and it will show up on the desktop.

Only auto-detected devices that have entries in /etc/fstab will show up on the Desktop.

You can mount the looped iso anywhere you want. Making a clean unused directory is a good idea though.

---

### Post by psusi on 2007-09-15
If you mount it under /media it shows up on the desktop.  If you mount it directly in /media, it will cover up access to anything else mounted under there, so don't do that.

---

### Post by madman100 on 2007-09-15
hi m8 for mounting iso you can usr kiso or Gmount-iso

---

