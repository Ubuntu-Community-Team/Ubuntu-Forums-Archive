---
title: "how do i enable 2 network cards"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by alexlex on 2007-04-21
I am running ubuntu 7.04 and i have 2 network card 1 for direct internet and the other for my home network witch provides net access to my other computers. ubuntu will not let me run both cards at the same time.....

so i either have access to my home network or to internet but not both.. any suggestions

---

### Post by alexlex on 2007-04-21
bump

---

### Post by alexlex on 2007-04-23
bump

---

### Post by n3tfury on 2007-04-23
i'm guessing here because i'm fairly new to Linux, but i would imagine that the network manager will not let you enable two cards.  perhaps uninstalling network manager and manually configuring ifconfig for both cards would do the trick.  

hopefully someone with more linux networking knowledge can chime in on that idea.

---

### Post by oilchangeguy on 2007-04-23
found this by doing a google search:
[http://www.debian-administration.org/articles/470](http://www.debian-administration.org/articles/470) i know it's not for ubuntu, but it's debian, so it might work. other enter the bios and asign a new irq to the second network card.

also you typed "witch" it's not halloween yet. try which.

---

### Post by n3tfury on 2007-04-23
> **oilchangeguy said:**
> found this by doing a google search:
[http://www.debian-administration.org/articles/470](http://www.debian-administration.org/articles/470) i know it's not for ubuntu, but it's debian, so it might work. other enter the bios and asign a new irq to the second network card.

also you typed "witch" it's not halloween yet. try which.

and you typed "asign".  try "assign".

---

### Post by oilchangeguy on 2007-04-24
misspelling a word is different than using a completely wrong word.

---

### Post by n3tfury on 2007-04-24
if you're going to be a grammar nazi what's the difference?  it's not like you didn't understand what he/she was talking about.

---

### Post by Styan on 2007-04-26
I just updated and am experiencing the same thing.  Any ideas?



EDIT:::

I just went into my synaptics-package manager, and removed network_manager and network_manager-gnome.  Fixed my problem.

Hope that helps.

---

