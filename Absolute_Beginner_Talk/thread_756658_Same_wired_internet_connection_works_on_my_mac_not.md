---
title: "Same wired internet connection works on my mac not Ubuntu"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by AeThEr777 on 2008-04-16
So mozilla on ubuntu works but its just so slow, on my mac its fast! Can someone help fix this?

---

### Post by MrFSL on 2008-04-16
It has been discussed here that installing the statically compiled firefox speeds up its performance quite a bit. There is a script that manages it for you. Search the forms its in there.

---

### Post by gandaran on 2008-04-16
> **AeThEr777 said:**
> So mozilla on ubuntu works but its just so slow, on my mac its fast! Can someone help fix this?

firefox is shipped in ubuntu to work for dial-up connections, but you can do some tuning if you use broadband.
type about:config in firefox navigator bar and change the following items.

network.http.pipelining (to) true

network.http.proxy.pipelining (to) true

network.http.pipelining.maxrequests (to a number like) 20

---

