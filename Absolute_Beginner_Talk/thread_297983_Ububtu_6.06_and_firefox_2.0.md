---
title: "Ububtu 6.06 and firefox 2.0"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by alienexplorers on 2006-11-12
I downloaded Firefox 2.0, Bon Echo 2.0 and Minefield 3.0a1.  My question is there a way to remove Firefox 1.5.0.7 and use Firefox 2,0 in place of it.  I saw that removing 1.5.07 removes parts of the gnome desktop and other programs.  Is there a way to insert 2.0 in place so that these 0ther items are not lost.

---

### Post by ciscosurfer on 2006-11-12
You can divert the original FF package.

You can run FF 2.0 from it's directory without installing.

Just some suggestions.

---

### Post by tassoman on 2006-11-12
Would work making a symlink?

---

### Post by ciscosurfer on 2006-11-12
You can try removing with apt-get instead of aptitude (apt-get won't try to pull all those other packages, as I recall), then you can install the 2.0 version.

Symlinking?  The entire 1.5.0.7 directory?  Sounds tedious.

You can look at the man pages for dpkg-divert as well```
man dpkg-divert
```

Or you can simply download the FF 2.0 file from Mozilla, extract it, and run FF from that directory.

---

### Post by tassoman on 2006-11-12
I mean download mozilla.com tarball, extract to /opt and symlink the binary /usr/bin/firefox to /opt/mozilla/thebinaryof2

---

### Post by ciscosurfer on 2006-11-12
Ah.  I misunderstood.  Yeah, I suppose that would work.  Don't know how well though.

---

### Post by tassoman on 2006-11-12
Let's try it's the most oldschool way.
instead of download some dumb bashscript or deb package from yet another blog

---

### Post by nanotube on 2006-11-12
hey now, my script isn't dumb. :)

so try the script that aysiu and i cobbled together over many months. you will see it under the first link in my sig (the install official mozilla build of firefox section). 

it will do exactly has been suggested - install the mozilla build into /opt, move the original ubuntu with dpkg-divert, and symlink the new firefox to /usr/bin/firefox, so whenever you run firefox, you get the new version.

---

### Post by tassoman on 2006-11-12
Sorry man I woulnd't hurt you. I was wrong. I was mean dumb people who does things like monkeys without use our own mind, and learn by themself.

BTW instead of a SH is better a RTfM! not for you, for them! :P

---

### Post by nanotube on 2006-11-12
> **tassoman said:**
> Sorry man I woulnd't hurt you. I was wrong. I was mean dumb people who does things like monkeys without use our own mind, and learn by themself.

BTW instead of a SH is better a RTfM! not for you, for them! :P

hey, no big deal :) 

you are right in that it's better to learn how things work. but some people are too busy to be messing around with this stuff, not everyone has the time to spend. hence, we have automated solutions.

---

