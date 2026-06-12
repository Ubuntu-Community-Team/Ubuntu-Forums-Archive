---
title: "Pin Version - Apt-Get"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by OffHand on 2007-03-17
Hi 

Is it possible to exclude a package from updating?

I tried to put


Package: amsn
Pin: release v=0.96RC1-1
Pin-Priority: 1001


in /etc/apt/conf and /etc/apt/preferences but that does not work.

any ideas?

---

### Post by eljalill on 2007-03-17
You can do that in synaptic under package> lock version, once you have the package marked.

---

### Post by OffHand on 2007-03-17
> **eljalill said:**
> You can do that in synaptic under package> lock version, once you have the package marked.

Nah, that has been broken for ages. Thanks for your reply though  :)

---

### Post by eljalill on 2007-03-17
Has it? I had the impression, it worked for me... 
But hard to know really, since I rarely know about the updates, that I am not getting ;) .

---

### Post by OffHand on 2007-03-17
> **eljalill said:**
> Has it? I had the impression, it worked for me... 
But hard to know really, since I rarely know about the updates, that I am not getting ;) .

[https://launchpad.net/ubuntu/+source/synaptic/+bug/42178](https://launchpad.net/ubuntu/+source/synaptic/+bug/42178)

---

