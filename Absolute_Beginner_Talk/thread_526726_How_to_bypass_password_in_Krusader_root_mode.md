---
title: "How to bypass password in Krusader root mode?"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by tico on 2007-08-15
I've made a shortcut to open Krusader in root mode (Root Privileges) using the command

/usr/bin/kdesu krusader

It works fine, but every time it asks me to provide my root password. I'd like to type in once and make it retain the password, so that it will open without prompting me for the root password every time I want to open Krusader in root mode.
Is there a way to do that?

Thanks.

---

### Post by kellemes on 2007-08-16
Not sure if there is a way..
Just wonder why you would do this.. Krusader as root gives you all the power to destroy your system.

---

### Post by rich.bradshaw on 2007-08-16
Not really the best idea...

---

### Post by bodhi.zazen on 2007-08-16
You might want to check out expect : 

[http://www.linuxjournal.com/article/3065](http://www.linuxjournal.com/article/3065)

	[http://www.linux.com/articles/56066](http://www.linux.com/articles/56066)

---

### Post by tico on 2007-08-16
> **rich.bradshaw said:**
> Not really the best idea...

I often need to use Krusader root mode to try to explore a little bit my system. I don't think I'll destroy it, I'm very careful.


> You might want to check out expect :

[http://www.linuxjournal.com/article/3065](http://www.linuxjournal.com/article/3065)

[http://www.linux.com/articles/56066](http://www.linux.com/articles/56066)

Thanks for the links, but it seems a bit too complicated. I'd like to find a way to easily put the password in the shortcut and your tips imply too much work (don't have enough time at this right moment).

Thanks.

---

### Post by bodhi.zazen on 2007-08-16
you can try configuring sudo

see man sudoers, look at the examples at the bottom

you may need to replace (in /etc/sudoers): 

Defaults !lecture,tty_tickets,!fqdn

With    :  Defaults !lecture,tty_tickets,!fqdn,env_keep+="DISPLAY HOME XAUTHORIZATION"

---

