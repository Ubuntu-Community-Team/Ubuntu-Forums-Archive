---
title: "[SOLVED] Errorfor locale settings"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-06-12
Whenever I do anything in the terminal I get this error. For eg. i was changing my cups-pdf.conf file with this command
```
gksudo gedit /etc/cups/cups-pdf.conf
``` and got this error in the terminal before my gedit opened up

```
(gksudo:6674): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(gedit:6675): Gdk-WARNING **: locale not supported by C library

(gedit:6675): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

```

This started happening after I un-installed the open office that came with Ubuntu and installed the version from openoffice.org. How can I install the locale related packages ?


Thanks,

---

### Post by Hendrixski on 2007-06-12
hhmmm... my best guess would be to "apt-cache search local" and find one for your area...probably english
so  language-pack-en may be all you need

If that doesn't help then I have no idea

---

### Post by Hendrixski on 2007-06-12
By the way.. did you google this???
there are l ike a thousand results for that exact error message

---

### Post by Inxsible on 2007-06-12
I did, i actually rectified it by installing language-pack-en. Just forgot to mark it resolved.

Thanks for your help tho !!

---

