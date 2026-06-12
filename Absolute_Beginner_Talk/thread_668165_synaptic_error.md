---
title: "synaptic error"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by kenno69 on 2008-01-15
I am a new boy
Please help..when I try to open the Synapti package manager I get...
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What do i do...
Ta ken

---

### Post by Paul820 on 2008-01-15
Open up the terminal and type
> sudo dpkg --configure -a

---

### Post by hyper_ch on 2008-01-15
You do what it tells you to do... only prepend it with a "sudo" so that it runs as root.

---

### Post by lgambett on 2008-01-15
Following the istructions you received from Synaptic you should;
- open a terminal
- issue this command
**sudo dpkg --configure -a**

---

### Post by kenno69 on 2008-01-16
Thanks for ur help..all is fine now.
kenno

---

