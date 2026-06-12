---
title: "Warning in terminal"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by phil66 on 2007-06-08
Ubuntu 6.06.LTS

When I input a command in a terminal such as "sudo gedit /boot/grub/menu.1st"

I get two warnings 1 from gtk the other from gdk both warnings read the same

"gedit:17968:gtk Warning**: locale not supported by c library. Using the fallback 'C' locale"

The numbers change but the script remains the same

No suggestions on how to correct this warning on the terminal

Any suggestion will be welcomed on how to correct warning

---

### Post by Nekiruhs on 2007-06-08
please use gksudo for graphical apps.

---

### Post by phil66 on 2007-06-08
ray@ray-desktop:~$ gksudo gedit /boot/grub/menu.1st

(gksudo:6790): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
(gedit:6791): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(gedit:6791): Gdk-WARNING **: locale not supported by C library

(gedit:6791): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
ray@ray-desktop:~$

Latest results using gksudo gome ui warning added to list of warnings.

---

### Post by Shazaam on 2007-06-08
Could be a typo.
try--
menu.lst (small L)

not menu.1st (first)

---

### Post by phil66 on 2007-06-08
ray@ray-desktop:~$ gksudo gedit /etc/apt/sources.list

(gksudo:13192): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(gedit:13193): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(gedit:13193): Gdk-WARNING **: locale not supported by C library

(gedit:13193): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
ray@ray-desktop:~$

Sorry not a typo here is another warning using a different command
The pages are opening and I can edit without any problems
The warning are my concern

---

### Post by forestpixie on 2007-06-08
it's a bug apparently - it's in launchpad

:)

---

### Post by forestpixie on 2007-06-08
here it is 

[https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/23917](https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/23917)

---

### Post by phil66 on 2007-06-08
Thanks for the bug report they seem to cover all the problems

But no fix implied

---

