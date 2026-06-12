---
title: "Tranfering files via LAN between Ubuntu 7.10"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by papuccino1 on 2008-01-09
I want to transfer some files via wired LAN between two Ubuntu's.

I can see his computer, but he can't see me. 

How do I transfer it? 
 
When I right click>share folder, what should I put in the "share through" part? And in allowed hosts?


Thanks for the help.

---

### Post by feistybird on 2008-01-10
1, Check System > Admin > Network > General > Domain : 
And make sure you have same Domain name same as your friends Windows Domain

2. Double check whether the IP address of both computer are in the same range, ie. 192.168.0.x

3. First try share the folders located in your /home directory only, right click on the foler, and look for 'properties', make sure the shared folder's read permission is allowed for "OTHERS"

---

