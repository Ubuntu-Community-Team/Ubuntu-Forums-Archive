---
title: "error message - what does it mean?"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by whiffy badger on 2007-10-30
I've been trying to open synaptic, I get the following message:

[B] E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/B]

Any suggestions?

---

### Post by 67GTA on 2007-10-30
Something happened, and dpkg didn't finish what is was doing. Run the command it gave you in a terminal to reset everything.

> dpkg --configure -a

---

### Post by taurus on 2007-10-30
Try running these commands from a terminal.

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by whiffy badger on 2007-10-30
thanx!

---

### Post by rickconroy on 2007-10-30
I'm having same problems but entering those commands doesn't solve the problem for me.
any other suggestions?

---

### Post by Maestro23 on 2007-10-30
> **rickconroy said:**
> I'm having same problems but entering those commands doesn't solve the problem for me.
any other suggestions?

What exactly where you trying to do when that resulted in the error?

---

