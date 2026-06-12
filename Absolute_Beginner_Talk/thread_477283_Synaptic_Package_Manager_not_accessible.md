---
title: "Synaptic Package Manager not accessible"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by dcalvani on 2007-06-18
Hi, I've just tried to launch Synaptic Package Manager. I was asked (as usual) to insert my password. I must've mistyped (although I'm not sure). Anyway, I tried again, inserted the right password, and the following message popped up:

'E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.'

I run 'dpkg --configure -a' on Terminal, and got the following:

'dpkg: requested operation requires superuser privilege'

Do you know what I should do? Thank you!!!

---

### Post by fakie_flip on 2007-06-18
sudo gives you super user privileges.

sudo dpkg --configure -a

---

### Post by dcalvani on 2007-06-18
Thank You!!!

---

