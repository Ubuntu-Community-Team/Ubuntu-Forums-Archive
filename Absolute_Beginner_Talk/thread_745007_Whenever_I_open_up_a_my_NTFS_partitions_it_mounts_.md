---
title: "Whenever I open up a my NTFS partitions it mounts the partition to the desktop?"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by Vorteilspreis on 2008-04-04
I just installed linux for the first time. Why whenever I open up a my NTFS partitions does it mount the partition to the desktop? Does it just do this with NTFS partitions or all partitions in general? These partitions are from when I had windows installed on my computer.

---

### Post by mikeyphi on 2008-04-04
> **pat666rick said:**
> I just installed linux for the first time. Why whenever I open up a my NTFS partitions does it mount the partition to the desktop?

In order to gain access to any hard drive - it must first be 'mounted'. So when you look at the NTFS partition the system has to mount it so that the OS knows where everything is - then let you see the contents....it's just the way Ubuntu (linux) works. 

You could, of course, have that partition permanently mounted.

---

### Post by kpkeerthi on 2008-04-04
> **pat666rick said:**
> I just installed linux for the first time. Why whenever I open up a my NTFS partitions does it mount the partition to the desktop? Does it just do this with NTFS partitions or all partitions in general? These partitions are from when I had windows installed on my computer.

Ubuntu mounts them to **/media/<label>** and puts a shortcut on your desktop.

---

### Post by bollix47 on 2008-04-04
If you don't want the icon to show on the desktop do the following:

Alt-F2

gconf-editor

apps > nautilus > desktop

Remove the checkmark next to volumes_visible

---

