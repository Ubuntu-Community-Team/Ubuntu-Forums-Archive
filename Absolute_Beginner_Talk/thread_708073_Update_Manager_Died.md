---
title: "Update Manager Died?"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by techmunkey on 2008-02-26
While trying to download 35 new updates this evening I got the below message. I try to run the command as sudo and it fails and gives some direction on *.deb package management. 

Any happen to know how to clear this and get update manager working?

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by kpkeerthi on 2008-02-26
Close synaptic and update manager if running. Open a terminal and enter
```
sudo dpkg --configure -a
```

Might clear things up.

---

### Post by Crafty Kisses on 2008-02-26
> **techmunkey said:**
> While trying to download 35 new updates this evening I got the below message. I try to run the command as sudo and it fails and gives some direction on *.deb package management. 

Any happen to know how to clear this and get update manager working?

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Run the command that it tells you.

---

### Post by techmunkey on 2008-02-26
I left off a space in the command. I corrected it and it was vmware wanting a serial number. I got one and everything appears to be okay. Thanks for quick response.

---

### Post by Crafty Kisses on 2008-02-26
> **techmunkey said:**
> I left off a space in the command. I corrected it and it was vmware wanting a serial number. I got one and everything appears to be okay. Thanks for quick response.

Mark the thread solved. :KS

---

