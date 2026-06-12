---
title: "Rxvt-Unicode Termcap FreeBSD"
date: 2009-01-11
forum: BSD
---

### Post by jjte on 2009-01-11
I decided to switch my file server to FreeBSD due to my getting sick of Debian and its various quirks.
It is a command line only system, primarily accessed via SSH.
The Rxvt-Unicode package (and the port) requires a whole lot of X dependencies.
Being a command line only system, I don't fancy installing graphical deps.

Every application on the system is treating my terminal as a dumb terminal, and applications requiring input refuse to start.
The problem (I thought) was the lack of a termcap entry for Rxvt-Unicode. So, I found an entry, and appended it to /usr/share/misc/termcap.
I was surprised to find that I had the same problem as before, so I rebooted, upon boot, I opened an SSH connection from my desktop, but the same problem remains.

I remember reading somewhere that I need to put the termcap entry in termcap.src.
Due to my very limited BSD experience (literally an hours experience), I have no idea where to find this.
I tried searching my local ports with "make search name=termcap", but there were no results.

Any help would be great, Xterm isn't very nice.

---

### Post by cardinals_fan on 2009-01-11
> **jjte said:**
> I decided to switch my file server to FreeBSD due to my getting sick of Debian and its various quirks.
***_It is a command line only system_***, primarily accessed via SSH.
The Rxvt-Unicode package (and the port) requires a whole lot of X dependencies.
Being a command line only system, I don't fancy installing graphical deps.

Every application on the system is treating my terminal as a dumb terminal, and applications requiring input refuse to start.
The problem (I thought) was the lack of a termcap entry for Rxvt-Unicode. So, I found an entry, and appended it to /usr/share/misc/termcap.
I was surprised to find that I had the same problem as before, so I rebooted, upon boot, I opened an SSH connection from my desktop, but the same problem remains.

I remember reading somewhere that I need to put the termcap entry in termcap.src.
Due to my very limited BSD experience (literally an hours experience), I have no idea where to find this.
I tried searching my local ports with "make search name=termcap", but there were no results.

Any help would be great, Xterm isn't very nice.
*emphasis mine*

Why are you running X on a command-line only system?

Anyway, this might be useful:

[http://pod.tst.eu/http://cvs.schmorp.de/rxvt-unicode/doc/rxvt.7.pod#I_need_a_termcap_file_entry](http://pod.tst.eu/http://cvs.schmorp.de/rxvt-unicode/doc/rxvt.7.pod#I_need_a_termcap_file_entry)

---

### Post by LateNiteTV on 2009-01-11
check out sysutils/jfbterm

---

