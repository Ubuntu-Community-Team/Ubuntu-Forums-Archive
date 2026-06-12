---
title: "synaptic Error"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by blharmon on 2008-03-24
When running synaptic package manager I am now getting the following error: 

An error occured
The following details are provided.
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I have tried running su dpkg --configure -a and I get the following error: unrecognized option `--configure' 

I'm pretty much stuck since I'm a totally new user to Ubuntu. Any help appreciated.

---

### Post by Trail on 2008-03-24
Use sudo instead of su if you want to use it in the same command.

---

### Post by blharmon on 2008-03-24
That worked!!! Thanks much!

---

