---
title: "Ati Video Driver Question"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by seekyrr on 2006-08-27
I have an ATI Radeon Mobility M7 video card in my A31 laptop.

Dapper Drake works good, after a new install, but I am wondering if there is a "better" or optimized driver available to get better 2d performance for watching movies and such? 

Thanks

Seek

---

### Post by gborzi on 2006-08-27
You can try the "radeon" driver instead of the default "ati" driver in xorg.conf. Check in your /etc/X11/xorg.conf for a line with > Driver "ati" and change it to > Driver "radeon"
for further settings of this driver see the manpage (man radeon) and search in these forums, there are good suggestions.

---

