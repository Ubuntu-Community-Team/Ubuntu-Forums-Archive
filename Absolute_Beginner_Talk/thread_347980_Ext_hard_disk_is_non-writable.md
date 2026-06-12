---
title: "Ext hard disk is non-writable"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by Hishgraphics on 2007-01-28
I plugged in an USB external hard disk into my 6.06 machine. I can read read everything, but when I tried moving files into it, it tells me that I don't have the permission to write it. Checking file permissions, it's true enough the ext hard disk is non-writable. I can't check the write box.

Any help, thanks?

---

### Post by mendingo84 on 2007-01-28
is it formated ntfs?

---

### Post by Hishgraphics on 2007-01-28
Doh!

That should have been the first thing I checked.

Yes it is. Thanks.

---

### Post by dexter on 2007-01-28
You can try installing the ntfs-3g driver, which enables ntfs write support in linux.

---

