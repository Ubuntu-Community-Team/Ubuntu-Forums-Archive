---
title: "help with broken synaptic - error message"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by jubuntu on 2008-01-03
im just getting this error message and its killed synaptic.



E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


can anyone tell me what to do?

thanks

---

### Post by Rocket2DMn on 2008-01-03
Run
```
sudo dpkg --configure -a
```
:)

---

### Post by jubuntu on 2008-01-03
I still get the error message.

---

### Post by sciencewhiz on 2008-01-03
> **jubuntu said:**
> I still get the error message.

Can you post the entire message from when you ran sudo dpkg --configure -a?

---

### Post by Rocket2DMn on 2008-01-03
First, please make sure that you typed that command out correctly, then run ```
sudo apt-get update
sudo apt-get upgrade
``` and post the output, please.

---

### Post by jubuntu on 2008-01-03
sorted, thanks for help!

---

