---
title: "Interested in trying BSD, but will miss Gnome and apt-get"
date: 2008-06-22
forum: BSD
---

### Post by rockin_goliath on 2008-06-22
I am interested in trying out BSD, but I am looking for an easy to use desktop environment comparable to Ubuntu. Is there a BSD distribution that has something similar to apt-get? Is there a distribution with Gnome?

---

### Post by cardinals_fan on 2008-06-22
You can install GNOME on any BSD.  My favorite is NetBSD, but FreeBSD is better supported and has more software in ports.  You can install with binary packages (pkg_add) or through ports (which handle all the compiling for you).  I'll post with more later.

---

### Post by theonlyrealperson on 2008-06-22
You can also try kFreeBSD. It's the FreeBSD kernel with Debian's utils:

[http://www.debian.org/ports/kfreebsd-gnu/](http://www.debian.org/ports/kfreebsd-gnu/)

I don't know how well developed it is, but it's an interesting idea.

---

### Post by angryfirelord on 2008-06-22
In BSD, you use pkg_get for binaries and ports for sources. Ubuntu focuses on binaries where as the BSDs focus on compiling from source.

The newbie friendly BSD distro for people like me would be PC-BSD, but it uses KDE instead of Gnome and PBIs for package management. Still, I recommend checking it out.

[http://www.pcbsd.org/]("http://www.pcbsd.org/")

---

### Post by cardinals_fan on 2008-06-22
I recommend DesktopBSD over PC-BSD.

---

### Post by cammin on 2008-06-22
Also, it's pkg_add, not pkg_get.


PC-BSD has so few PBI's that it's not worth using them. The ones they have don't always work right, either. Besides that, it's a nice distro, though.

---

### Post by angryfirelord on 2008-06-23
Oops, I'm thinking of Solaris. :oops: Yes, it's pkg_add. 

As for PBIs, they have expanded the list a bit over the past year. Granted, there's not thousands of applications like in Ubuntu, but the commonly used stuff is there. 

[http://www.pbidir.com/]("http://www.pbidir.com/")
[QUOTE="cardinals_fan"]I recommend DesktopBSD over PC-BSD. [/QUOTE]
Sure, it has GUI tools for its package management, but DesktopBSD is awfully slow to release and I don't think a new user would put up with the compiling. But it's still worth checking out.

---

