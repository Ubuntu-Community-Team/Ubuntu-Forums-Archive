---
title: "update problem"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by carrslanding on 2007-09-22
When trying to update my software, I get the following message - any ideas for solving this problem?

Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

---

### Post by ijason on 2007-09-22
that sounds like a networking problem, at the router level. usually if your DNS is xxx.0.0.1 that will be the address given your computer by the router, and the router is supposed to forward connectivity to that specific port so that your computer sees the internet and so that the internet sees the router's DNS.

check to see that your network cards are detected and connected, and then check to see if other machines on the network can see the www. 

sorry i don't have more specific advice :)

---

