---
title: "Help with Package Manger"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by john38242 on 2007-02-03
When I tried to open package manger or try to open Add remove programs this comes up 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


how do i fix this

---

### Post by meng on 2007-02-03
Open a terminal. Type:
sudo dpkg --configure -a
Enter user password when prompted.

---

