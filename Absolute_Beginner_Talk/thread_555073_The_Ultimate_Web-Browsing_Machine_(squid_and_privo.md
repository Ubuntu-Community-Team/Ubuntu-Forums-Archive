---
title: "The Ultimate Web-Browsing Machine (squid and privoxy) not working"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by bone2006 on 2007-09-19
I was looking at this post about the ultimate browsing machine, which was setup for fedora

[http://tinyurl.com/368jo2](http://tinyurl.com/368jo2)

For some reason squid isn't working.  It terminates, doesn't run and I get something like:
FATAL: Could not determine fully qualified hostname.  Please set 'visible_hostname'

Anybody able to get this to work on a debian based distro?

---

### Post by ravenwere on 2007-09-19
welcome to the joys of /etc/squid/squid.conf. The best thing to do is find a good tutorial and work through the conf file but this is industrial grade stuff!

So expect some heartache.

---

### Post by ravenwere on 2007-09-19
PS there needs to be a line in the squid.conf file

visible_hostname *your computer.your domain*

or words to that effect.

---

