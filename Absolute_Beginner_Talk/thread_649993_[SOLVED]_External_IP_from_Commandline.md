---
title: "[SOLVED] External IP from Commandline?"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by ckennow on 2007-12-25
How do I find out what my ip address is from the command line.  I don't have a gui installed and i'm on my laptop ssh'ing to my server.

---

### Post by SOULRiDER on 2007-12-25
Try ifoncifg or install lynx (CLI web browser) and go to whatismyip.com

---

### Post by xeth_delta on 2007-12-25
ifconfig should give you information about your network interfaces. You will find in that there is an IP associated to the interface in use. Of course, if that IP is assigned by a router in a local network, and what you want is the actual external IP, the problem changes a bit. You could then try to check what IP the router is assigned or use a webpage that shows you your IP.

[EDIT] SOULRiDER posted while I was typing, I agree with him, whatismyip.com is a good solution

---

### Post by ckennow on 2007-12-25
So yeah lynx worked I guess it was already installed:

commandline is
         lynx [www.whatsmyip.org](www.whatsmyip.org)

---

