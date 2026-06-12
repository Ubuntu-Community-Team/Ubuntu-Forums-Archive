---
title: "How do I make sound work on iMac8,1?"
date: 2009-08-12
forum: Apple Hardware Users
---

### Post by Madfoot713 on 2009-08-12
There's so many different solutions out there, between the wiki and posts on this forum and google, and I don't know which is the right one! Should I install the patch? Should I edit the /etc/modprobe/alsa-base.conf file? I don't know WHAT to do, and I really, really don't want to risk screwing up my ubuntu install (or worse)!

PLEASE help me out here, at least acknowledge me or something, last time I made a topic here I got no responses! DX

---

### Post by Madfoot713 on 2009-08-12
bump >_<

doesn't anybody have any advice for me here? =[

---

### Post by Madfoot713 on 2009-08-16
Well, my problem is now resolved. Turns out all I had to do was add a single line to the alsa-base.conf file, something that had "option=mbp3" in it (I forget what it is now >_>, but it's in the wiki). It sounds simple, but the fact that the wiki linked to a patch confused me a whole lot. =/

---

