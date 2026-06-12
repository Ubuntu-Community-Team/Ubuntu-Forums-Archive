---
title: "Upgrading failed when downloading VLC? Now I can't open updates"
date: 2010-04-17
forum: Apple Hardware Users
---

### Post by sastusbulbas on 2010-04-17
As I said I cant open update centre. I get this message so what do I do with it?

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Seems I now cannot open software centre too?

---

### Post by amd-64 on 2010-04-17
Close software center, synaptic and any other package management software and run
```

sudo dpkg --configure -a

```

---

### Post by sastusbulbas on 2010-04-17
Being a bit of a noob here,

What do I open and put that into ? And in any specific manner?

---

### Post by jaco223 on 2010-04-17
> **sastusbulbas said:**
> Being a bit of a noob here,

What do I open and put that into ? And in any specific manner?

Open a terminal window and type at the prompt

sudo dpkg --configure -a
You will asked to put in your password for sudo (SuperUser Do).
See if that helps.

---

