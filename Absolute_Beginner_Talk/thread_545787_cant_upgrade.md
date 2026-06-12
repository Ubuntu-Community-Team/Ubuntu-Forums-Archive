---
title: "cant upgrade"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by rude_lee on 2007-09-08
i have ubuntu fiesty ultimate and this is wat comes up when i get the upgrade notification and i press install

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

any help please and utorrent wont open up its screen.......... the icon appears and its running but it is forever hiding and i dont know how to uninstall and install it back under wine i would love to get utorrent running again

---

### Post by overdrank on 2007-09-08
> **rude_lee said:**
> i have ubuntu fiesty ultimate and this is wat comes up when i get the upgrade notification and i press install

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

any help please and utorrent wont open up its screen.......... the icon appears and its running but it is forever hiding and i dont know how to uninstall and install it back under wine i would love to get utorrent running again

Hi if you open the terminal and use the command
```
 sudo dpkg --configure -a 
```
This should solve the issue.

---

### Post by rude_lee on 2007-09-08
thanks that worked before it was saying i had no permissions but any help with utorrent even if it is to uninstall is please

thanks again

---

