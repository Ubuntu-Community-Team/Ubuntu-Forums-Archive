---
title: "Display what hardware I'm running?"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by kungfugecko on 2007-06-28
I can't find the equivalent of windows' my computer> properties, to see what my processor speed / RAM is in xubuntu.  Any help? Thanks!

---

### Post by RanulfWolfSage on 2007-06-28
Goto System > Administration > System Monitor

---

### Post by kungfugecko on 2007-06-28
I'm running Xubuntu, theres no menus past Applications>System>

---

### Post by Papi-KB7VGW on 2007-06-28
Open a terminal, it is under accessories and enter

lspci

this will tell you all about your system

---

### Post by RanulfWolfSage on 2007-06-28
My apologies, missed the X on the front of that Xubuntu. I've only used ubuntu thus far myself, but it seems the post above will get you what you are looking for.

---

### Post by iver2435 on 2007-06-28
Alternate ways:

      In a terminal, type:      lspci -v
        (v is for verbose)

      Install the "hardinfo" package from Synaptic Package Manager

---

### Post by reset3x on 2007-06-28
> **kungfugecko said:**
> I can't find the equivalent of windows' my computer> properties, to see what my processor speed / RAM is in xubuntu.  Any help? Thanks!

Try lshw .... That'll give you just about everything...

---

### Post by RomeReactor on 2007-06-28
Hi. You can also run:
```
sudo lshw
```
from the terminal.

---

### Post by kungfugecko on 2007-06-28
Thanks guys! hardinfo seems to be just what I was looking for =)

P.S. You are all freaking brilliant.  I think the most impressive thing about ubuntu/xubuntu is the community! Every noob question I've had has been answered in minutes!!

---

### Post by Papi-KB7VGW on 2007-06-28
that is what the community is all about   :popcorn:

---

### Post by chandler on 2007-06-28
Another way: sudo cat /var/log/dmesg

A little more info ;)

---

### Post by eternalsword on 2007-06-28
> **chandler said:**
> Another way: sudo cat /var/log/dmesg

A little more info ;)
shouldn't need sudo for catting unless for some reason dmesg could only be read by root :p

---

