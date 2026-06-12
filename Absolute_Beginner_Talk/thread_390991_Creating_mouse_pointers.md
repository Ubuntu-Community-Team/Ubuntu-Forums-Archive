---
title: "Creating mouse pointers"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by ProjectWhat on 2007-03-22
how do i creat custom mouse cursors for ubuntu. Is there some type of app, etc??

---

### Post by yabbadabbadont on 2007-03-22
```
/home/bubba $ aptitude show xcursorgen 
Package: xcursorgen
State: installed
Automatically installed: no
Version: 1:1.0.1-0ubuntu1
Priority: optional
Section: x11
Maintainer: Daniel Stone <daniel.stone@ubuntu.com>
Uncompressed Size: 61.4k
Depends: libc6 (>= 2.4-1), libpng12-0 (>= 1.2.8rel), libx11-6, libxcursor1 (> 1.1.2)
Conflicts: xbase-clients (< 6.8.2-35)
Replaces: xbase-clients (< 6.8.2-35)
Description: X cursor generation
 xcursorgen is a tool to generate cursors for the Xcursor library from a set of PNG files. 
 
 More information about X.Org can be found at: <URL:http://xorg.freedesktop.org>
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg> 
 
 This module can be found as the module 'app/xcursorgen' at :pserver:anoncvs@cvs.freedesktop.org:/cvs/xorg

```
I haven't played with it, even though it is installed.

---

### Post by ProjectWhat on 2007-03-22
ok i have that installed now. But How do I open it?
when I go to a terminail and type "xcursorgen" it does nothing, just sits there.

---

### Post by yabbadabbadont on 2007-03-22
In the terminal, type "man xcursorgen".  ;)

---

