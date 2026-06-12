---
title: "apt-get help please"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by tidy_boy on 2008-01-27
HI there I have not used ubuntu for a while now and I have come back to it after vista was annoying me 

I am trying to install amsn via apt-get 

```
matt@laptop:~$ sudo apt-get install amsn
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

I dont no what this means can someone please help me.


Many Thanks


Matt

---

### Post by taurus on 2008-01-27
Do you happen to have synaptic, Add/Remove, or even adept running while you executed that command from a terminal?  You need to close it down since you cannot run two same processes at the same time.

---

### Post by philinux on 2008-01-27
either use synaptic or make sure its not running at the same time.

---

