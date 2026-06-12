---
title: "apt-get update problem"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by grim918 on 2006-07-29
I keep getting this error when I try to run

sudo apt-get update 

Here is the error that I get
> 
grim@ubuntu:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory


It was working before and I just ran into this problem today. Can someone please help me out.

---

### Post by T700 on 2006-07-29
Somewhere (maybe another desktop) you have a session of apt-get, aptitude, Adept, or Synaptic open.  If not, there may be a file that is locked and needs to be deleted.  For a quick fix, try logging out of the session and back in.

Paul

---

