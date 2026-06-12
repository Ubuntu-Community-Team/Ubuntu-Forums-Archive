---
title: "Changing Workstation Name"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by ZeroXR on 2007-03-03
I goofed and misspelled the computer name for my project laptop... How do I go about changing the name of the computer?

The part in bold is what I want to change.

(username) @ **(computer-name)**$

---

### Post by taurus on 2007-03-03
If you need to change the name of your machine, you need to change it in two places:  /etc/hostname & /etc/hosts.  They must have the same name or sudo won't work and network won't work, either.  

So, be real _careful_.

```
gksudo gedit /etc/hostname /etc/hosts
```

---

### Post by highneko on 2007-03-03
It should be possible in -> system -> administration -> networking -> then go into the general tab and change the hostname.

---

### Post by ZeroXR on 2007-03-03
My thanks, you all ROCK~!

---

