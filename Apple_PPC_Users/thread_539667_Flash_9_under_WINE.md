---
title: "Flash 9 under WINE"
date: 2007-08-31
forum: Apple PPC Users
---

### Post by john_spiral on 2007-08-31
Hi,

Are there any PPC users out there who have Flash ver 9 installed via WINE?

I got the below howto from google:

[http://www.howtoforge.com/ubuntu_flash_player9](http://www.howtoforge.com/ubuntu_flash_player9)

---

### Post by stmiller on 2007-08-31
There's no WINE for PowerPC, unfortunately. The closest thing you can do to get Adobe Flash is to possibly use qemu in combination with a nspluginwrapper hack like this person says: [http://www.advogato.org/person/dwmw2/diary.html?start=150](http://www.advogato.org/person/dwmw2/diary.html?start=150)

---

### Post by john_spiral on 2007-09-03
from [http://www.advogato.org/person/dwmw2/diary.html?start=150](http://www.advogato.org/person/dwmw2/diary.html?start=150)

[COLOR="DimGray"]"11 Dec 2006 »
Wheee. With a little bit of hacking to provide NPTL support in qemu, nspluginwrapper can now run the i386 flash plugin inside firefox on PowerPC machines.

The colours seem wrong-endian (just as when we run the standalone flash player in qemu-i386), and on some content it'll crash after a couple of clone() calls so I suspect the TLS stuff isn't quite right -- but it's getting there..."[/COLOR]

have any PPC users got this working?

A possible solution would be to run a i386(PC) version of Firefox with all plug-ins on a PPC as a Citrix type application. 

let me explain:

In the Windows world Citrix allows you to run Windows XP applications under Windows NT.

Is there an equivalent piece of technology in the open source world that will allow you to run i386 apps on a PPC?

---

### Post by Afishionado on 2007-09-03
Uh, Qemu is the only thing I can think of.

It's not an issue of emulating a different version of the operating system; it's an issue of emulating the i386 hardware that Flash is built to run on, unfortunately.

---

### Post by stmiller on 2007-09-03
Check out this thread, though sort of old:

[http://forums.gentoo.org/viewtopic.php?t=117774](http://forums.gentoo.org/viewtopic.php?t=117774)

It outlines how you can use qemu to run adobe flash, if you are interested in diving in.

---

