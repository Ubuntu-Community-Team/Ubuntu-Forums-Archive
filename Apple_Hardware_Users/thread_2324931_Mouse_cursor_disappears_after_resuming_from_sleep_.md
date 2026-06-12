---
title: "Mouse cursor disappears after resuming from sleep mode"
date: 2016-05-17
forum: Apple Hardware Users
---

### Post by paraponemenos on 2016-05-17
Hi, all

I've been using Xubuntu on an old MacBook3,1 (MB062xx/A). It works rather smoothly, save for the following annoying situation: the mouse cursor disappears after resuming from sleep mode.

Initially, I installed Xubuntu 15.10. After resuming from sleep mode, everything behaved normally. However, since I performed the upgrade to 16.04, the cursor started disappearing after resuming. Sometimes it appears after opening and closing a few windows, but most of the time doesn't, and I have to reboot in order to have it displayed again. The cursor is still there, since I can move it, launch applications, etc. However, it's not displayed.

Just in case, here is the output of uname -a:

Linux ramiro-MacBook 4.4.0-22-generic #40-Ubuntu SMP Thu May 12 22:03:46 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Any ideas?

Ramiro

---

### Post by slickymaster on 2016-05-17
*Thread moved to **Apple Hardware Users**.*

---

### Post by PaulW2U on 2016-05-17
> **paraponemenos said:**
> Any ideas?
Yes, a widely reported bug - [https://bugs.launchpad.net/ubuntu/+bug/1568604](https://bugs.launchpad.net/ubuntu/+bug/1568604). 

It's even mentioned in the [Release Notes]("http://xubuntu.org/news/xubuntu-16-04-release/").  :)

---

### Post by paraponemenos on 2016-05-17
Ok, I have to write a few times: RTF Release Notes... I apologize for just making noise.

---

