---
title: "how do I play dvds"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by chuck88 on 2008-01-18
ok, I am trying to go through the steps of medubuntu for 3rd party something or other, can't remember what it said. and I get this message: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
don't understand what to do, cant make it run with the alt F2 thing, all I want to do is play DVDs, is there a slow person's guid to this? Also how do I get back to this post to see if anyone answered without googling it?:)

---

### Post by thelatinist on 2008-01-18
> **chuck88 said:**
> ok, I am trying to go through the steps of medubuntu for 3rd party something or other, can't remember what it said. and I get this message: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
don't understand what to do, cant make it run with the alt F2 thing, all I want to do is play DVDs, is there a slow person's guid to this? Also how do I get back to this post to see if anyone answered without googling it?:)

Just what it says.  In terminal, run:

```
sudo dpkg --configure -a
```

---

### Post by RomeReactor on 2008-01-18
Hi. Please open a terminal and run the command:
```
sudo dpkg --configure -a
```
after that, run:
```
sudo aptitude update
```

To see if new messages are posted in this thread, you can subscribe to it from the **Thread Tools** menu above the first post.

---

