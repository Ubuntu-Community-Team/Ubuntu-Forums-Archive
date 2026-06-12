---
title: "Help!!! Install bind in desktop edition"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by KilluaX on 2007-05-18
Hi, all

I want to install bind9 in my box with desktop edition ubuntu

But when I type
 > sudo apt-get install bind9

I got this
 > root@linux:/etc/apt# apt-get install bind9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package bind9 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  dnsutils
E: Package bind9 has no installation candidate


I don't know what to do, please help

thanks

---

### Post by deadgobby on 2007-05-18
Check in synaptic.

---

### Post by KilluaX on 2007-05-18
> **deadgobby said:**
> Check in synaptic.

There is no bind9 in my synaptic

Should I use a server edition of Ubuntu?

Thanks for reply

---

### Post by demosdemon on 2007-05-19
bind9 is not avaliable in the ubuntu repos... only bind 8...

I have a pending bug report on it: [https://bugs.launchpad.net/ubuntu/+source/bind/+bug/108426](https://bugs.launchpad.net/ubuntu/+source/bind/+bug/108426)

---

