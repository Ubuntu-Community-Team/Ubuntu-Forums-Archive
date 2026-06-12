---
title: "what happened to mplayer?"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by Cruz on 2006-09-21
I was looking for a suitable media player today and the whole world seems to be praising mplayer. On many pages I saw "just install it with synaptic", but I just can't see it there. Yes I have ALL repositories enabled. All I can see is the kmplayer, which is clearly not the mplayer. So what's the deal?

---

### Post by croak77 on 2006-09-21
It's in multiverse. Double-check or post your /etc/apt/sources.list.

---

### Post by Cruz on 2006-09-21
Yes you are right I didn't do it right. Multiverse wasn't enabled.

---

### Post by Brunellus on 2006-09-21
worth noting that mplayer is actually several different packages, even on i386:  one for i386, one for i586, and one for K7.  apparently mplayer is one of those things that REALLY benefits from being compiled especially for your particular architecture.  

h'mph. Maybe I'll apt-build it sometime.

---

