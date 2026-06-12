---
title: "question about installation"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by thungmail on 2008-03-17
Hi
I installed some software and there is a message at the end of processing:
**ldconfig deferred processing now taking place**
Can somebody tell me what it is

---

### Post by Oldsoldier2003 on 2008-03-17
> **thungmail said:**
> Hi
I installed some software and there is a message at the end of processing:
**ldconfig deferred processing now taking place**
Can somebody tell me what it is

[https://answers.launchpad.net/ubuntu/+source/gnome-terminal/+question/15849](https://answers.launchpad.net/ubuntu/+source/gnome-terminal/+question/15849)
> 
This is normal and to do with triggers, if a package requires ldconfig to be run after installing a library then the trigger cause the command to be run only once at the end of installation rather than after every library is installed. ldconfig creates the necessary links and cache to shared libraries

---

