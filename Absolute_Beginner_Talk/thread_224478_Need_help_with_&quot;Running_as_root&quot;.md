---
title: "Need help with &quot;Running as root&quot;"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by dolbinau on 2006-07-28
Hey,

I'm in Ubuntu! It's great! Anyway, to get my wirless adapter working I'm using ndiswrapper. I'm up to the stage to compile my drivers and it wants to write to /etc/ndiswrapper - However, I get an error in the terminal saying Unable to create: "Make sure you are running as root".

I take it means this is like an admin? There is only one user account on my installation and I am sure I am 'root' or admin, am I not? Please explain/help :).

---

### Post by Sef on 2006-07-28
use can use gksudo to run as a temporary root.

Also if you are compiling make sure that you have installed build-essential.

---

### Post by aysiu on 2006-07-28
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

