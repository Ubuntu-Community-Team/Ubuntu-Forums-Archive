---
title: "How to automount cds"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by churchill614 on 2007-08-14
How do I set up Feisty to autmount my data cd's? Also, it will not recognise music or film (dvd) media. I appreciate that music and films cannot be mounted as they are not a file system, but how can I get feisty to recognise them automatically?

There is an icon in computer for CD/DVD-RW, but when I insert a cd this is not accessible and no other icons are displayed to allow me access to the disk.

Please help, thanks.

---

### Post by Bagster on 2007-08-14
It should do it by default.... If not try going to 
System>preferences>Removable Drives and Media

and check that the "mount removable media when inserted" is checked

---

### Post by churchill614 on 2007-08-14
Thanks.  It didn't do it, and I have discovered that running hald works (needed to run Removable Drives and Media).  How do I get this service to autorun for all users?

---

