---
title: "preventing the forkbomb"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by Trzone on 2007-12-28
Is there any way to make a permanent change to Ubuntu to prevent the Forkbomb or at least prevent it from spiraling out of control?  I am off to bed..

---

### Post by jas0 on 2007-12-29
Haha, I don't think this is a good topic for the absolute beginner talk forum. 

I remember that fork bombing was the talk of the town a few years ago in the IRC channels I frequented. So, first of all, as far as I remember Debian was pretty well off at the time. Are there new developments? Unpatched flaws? If so, I would love to see more info.

---

### Post by Trzone on 2007-12-29
If you add the following lines to /etc/security/limits.conf 

# prevent core dumps
*	hard	core	0

#limit user processes per user to 150
*	soft	nproc	100
*	hard	nproc	150


It seems to prevent the forkbomb, as well as add another security feature.

It was added by the Bastille program, which you should not use if you do not know what you are doing.

[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)

Probably the solutions to many security problems.

---

### Post by Dr Small on 2007-12-29
Check this thread out:
[http://ubuntuforums.org/showthread.php?t=626213&page=4](http://ubuntuforums.org/showthread.php?t=626213&page=4)

---

### Post by Trzone on 2007-12-29
Whenever i try to run the forkbomb, it says this

bash: fork: Resource temporarily unavailable

Which supposedly restricts the forkbomb.

---

### Post by skymera on 2007-12-29
to prevent it:

- Dont run it.

---

### Post by Trzone on 2007-12-29
Is it possible to hide a forkbomb within a program?  I think forkbombs are more of an annoyance to servers than desktops.  It is not a concern to the average Ubuntu user, but many other distros are protected against it by default.

---

