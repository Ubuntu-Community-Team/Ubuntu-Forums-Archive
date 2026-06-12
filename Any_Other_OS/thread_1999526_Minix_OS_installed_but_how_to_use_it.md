---
title: "Minix OS installed but how to use it"
date: 2012-06-08
forum: Any Other OS
---

### Post by tech291083 on 2012-06-08
Hi,

I have downloaded the latest Minix OS - **minix_R3.2.0-116fcea.iso.bz2 (366 MB)** and installed it using the following guide. Now I whenever I boot minix, I get to a point where a terminal greets me, but I do not know as to what to do next to run it as any other OS. I downloaded it thinking it is a full-featured GUI OS, but all I see now is a terminal. I have seen screenshots of this OS and it looks to me that it is full with GUI components ie menu, buttons etc. Hope I am correct here. Please help me out, thanks.

[http://www.minix3.org/doc/A-312.html](http://www.minix3.org/doc/A-312.html)

[http://www.minix3.org/download/](http://www.minix3.org/download/)

---

### Post by eyeofliberty on 2012-06-08
Hmm, if it's an X windowing based GUI, typing "startx" in the terminal should get you going, but I have no experience with Minix, so I don't know for sure. If that works, you would then have to edit the runlevel to get it to start up automatically each time you boot.

---

### Post by Erik1984 on 2012-06-08
Minix has no graphical desktop (at least not by default), not when I tried it. Had to use it in VM for university courses years ago.

** correction:** It does seem possible to start a graphical session:
[http://wiki.minix3.org/en/UsersGuide/IntroductionToX](http://wiki.minix3.org/en/UsersGuide/IntroductionToX)

---

