---
title: "resolution and gaim issue"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by Devile on 2006-09-07
in my dell inspiron 6400 the highest offered display in ubuntu is 1024x768 and it should 1280x800 (i think)...  

also with gaim it'll only run for like 10 minutes then it just shuts down...  Please help...

---

### Post by Devile on 2006-09-07
bump... please help

---

### Post by jlsheehan on 2006-09-08
Hi,

I just got my 6400 to work by searching the other threads, I think the steps basically went like this:

1. update all the packages
2. add the universe and multiverse repositories
3. install 915resolution (from the synaptic package manager)
4. I did a "sudo dpkg-reconfigure xserver-xorg" and entered all the defaults (just hit enter at every question) because I was messing around with xorg.conf but you might not have to, not sure if it actually changed anything.
5. reboot and X should look ok now

I also installed linux-image-686 and linux-restricted-modules-686 to make use of both processors.

Hope this helps.

Jeff

---

