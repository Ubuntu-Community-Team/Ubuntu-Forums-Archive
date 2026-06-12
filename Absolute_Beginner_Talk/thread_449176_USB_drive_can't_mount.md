---
title: "USB drive can't mount"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by abijah on 2007-05-20
Messing around... 
i changed the "Mount Point" field 
in the Drive and Volume tab 
of the Drive Properties to "/home/mydir/" 
now when i plug-in my drive it doesn't mount.

How do i fix this?

---

### Post by abijah on 2007-05-20
thank goodness for the internet!

here was my fix:

<open shell>
$gconf-editor

<starts "Configuration editor">
under  System > Storage > Drives and Volumes, remove the values.

---

