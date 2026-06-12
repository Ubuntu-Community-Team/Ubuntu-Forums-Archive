---
title: "I have a problem @ updating any thing..."
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by finalfantasy on 2008-04-02
when I run any thing throw the terminal or the synaptic 
an error message is displayed :
  



 E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

please someone help

---

### Post by ugm6hr on 2008-04-02
Try:

```
sudo dpkg --configure -a
```

This generally happens if apt was interrupted midway through an installation.

---

### Post by Teber on 2008-04-02
ok ok. so i was typing very much the reply already posted. the OP should have no complaints about the service of this forum!

---

### Post by finalfantasy on 2008-04-03
thanx so much
but what was that???
sorry of being late to reply

---

