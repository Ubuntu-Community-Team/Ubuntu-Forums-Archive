---
title: "Stop Ping response"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by gregj5916 on 2007-08-21
Sorry this was submitted in error, i would del if i could see how.

---

### Post by igknighted on 2007-08-21
In case anyone comes around later looking for the answer (ie, if you found this via a search)

ctrl+c stops the current action in the terminal.  So if the pings wont stop, hit ctrl+c.

In order to use the ping command with a pre-defined number of pings, try this:

```
ping -c 5 www.gentoo.org
```

Where ping is the command (as before) and -c means you are going to tell the computer how many, 5 is the number of pings I chose (you can use any integer you want), and [www.gentoo.org](www.gentoo.org) is the site that I always use to test ping (habit, i used ping a lot testing connections after a gentoo install and it stuck), you may of course use whatever site you like.

---

### Post by alastairthegreat on 2007-12-03
thanks, i just searched and found this, just what i needed :D

---

