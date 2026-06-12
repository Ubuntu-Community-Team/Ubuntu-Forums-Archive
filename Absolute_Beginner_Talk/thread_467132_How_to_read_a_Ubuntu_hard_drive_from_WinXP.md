---
title: "How to read a Ubuntu hard drive from WinXP?"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by MartyNg on 2007-06-07
Maybe this is not possible, but does anyone know a way to access an Ubuntu hard drive from another hard drive that is running Windows XP? (NTFS if it matters)  I am hoping there is a way to get at least read-only access, but read/write would be nice as well.

I've configured the Automatix NTFS tool in Ubuntu to auto-mount my XP hard drive and have that working succesfully.

Thanks!

---

### Post by rich.bradshaw on 2007-06-07
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by esavato on 2007-06-07
If you are using ext2 or ext3, then get the driver from this site:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

Follow the instructions in the FAQ if you have ext3.

---

### Post by MartyNg on 2007-06-07
Fantastic! Thanks guys! Once again, I am surprised by the knowledge and speed of you guys in the Linux world. After spending several years as a Windows guru in various IRC chat rooms over the years, it's nice to be on the receiving end of knowledge, in my new adventure into Linux!

Take care.
=D>

---

### Post by candtalan on 2007-06-07
Welcome!

---

### Post by warcriminal on 2007-06-07
Read these articles;

[http://www.goitexpert.com/entry.cfm?entry=Connect-Vista-To-A-Linux-Share--UBUNTU](http://www.goitexpert.com/entry.cfm?entry=Connect-Vista-To-A-Linux-Share--UBUNTU)

[http://www.goitexpert.com/entry.cfm?entry=Windows-File-and-Printer-Sharing-with-Samba-How-To-Guide](http://www.goitexpert.com/entry.cfm?entry=Windows-File-and-Printer-Sharing-with-Samba-How-To-Guide)

---

### Post by MartyNg on 2007-06-07
> **esavato said:**
> If you are using ext2 or ext3, then get the driver from this site:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

Follow the instructions in the FAQ if you have ext3.

While this seems to work okay, I've noticed something strange. When I try to install software in Windows now, it seems to uncompress files to the Linux drive, which I labeled Z:

Is there something I don't know about how windows expands temporary installation files? I'm trying to install .NET framework 3.0.

---

