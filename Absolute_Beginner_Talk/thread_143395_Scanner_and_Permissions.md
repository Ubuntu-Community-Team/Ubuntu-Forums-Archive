---
title: "Scanner and Permissions"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by Max Roswell on 2006-03-12
So I'm trying to get my parallel port scanner recognized by SANE.  I've edited my dll.conf and mustek_pp.conf files.

XSANE won't recognize it *unless* I do sudo first.  I'm sure that means I have to change permissions on something, but I'm not sure on what.  Any pointers?

---

### Post by klytu on 2006-03-12
[QUOTE=Max Roswell]So I'm trying to get my parallel port scanner recognized by SANE.  I've edited my dll.conf and mustek_pp.conf files.

XSANE won't recognize it *unless* I do sudo first.  I'm sure that means I have to change permissions on something, but I'm not sure on what.  Any pointers?[/QUOTE]
I have a similar situation with a canon parallel port scanner (CanoScan FB620P). I also was unable to get xsane to recognize it without sudo"ing" first. I tried changing various permissions and groups settings for my userid to no avail. In the end I edited the menu entry for xsane to invoke it with gksudo and I just live with that. Another inconvenience I noticed is that anything I scan and actually save generates a file owned by root. So I have to chown the saved file to able to open and manipulate it GIMP or some such animal.

---

### Post by Max Roswell on 2006-03-12
Hmmmm...I guess I could do the same.  I'm still going to poke around to see if there's a slightly simpler way, because I'm lazy like that.

---

### Post by Red Ghost on 2006-03-12
[QUOTE=Max Roswell]Hmmmm...I guess I could do the same.  I'm still going to poke around to see if there's a slightly simpler way, because I'm lazy like that.[/QUOTE]
Going out and finding the real solution is harder. You aren't a true lazy person.

---

### Post by Max Roswell on 2006-03-13
I'd take offense to that, if I weren't so lazy.

So far, I've found this:

> For most parallel port scanners you not only need read/write access to the device, you also have to be root (or your application needs to be setuid root). The reason for this is that the backend must control the actual parallel port via I/O ports. This is necessary for all Linuces (linuxes?) 2.1 and above. 


At [http://www.xs4all.nl/~ljm/SANE-faq.html#47](http://www.xs4all.nl/~ljm/SANE-faq.html#47)

Which makes it sound like there simply may not be a solution other than just scanning things as sudo (with sudo?  what's the right phrasology?).

---

