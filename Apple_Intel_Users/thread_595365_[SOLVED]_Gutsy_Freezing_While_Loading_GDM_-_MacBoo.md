---
title: "[SOLVED] Gutsy Freezing While Loading GDM - MacBook"
date: 2007-10-28
forum: Apple Intel Users
---

### Post by troseph on 2007-10-28
When I boot my system, everything goes fine until GDM loads, X starts just fine, but when GDM is loading it will freeze the machine.. However, I am able to get the system to load fully by going to the Recovery mode and running "init 3" Then everything (including GDM) works totally fine.. What might be the problem?

---

### Post by troseph on 2007-10-28
Resolved. The Wacom script in runlevel 2  was causing the hang. Fixed by running deleting the wacom script from /etc/rc2.d/

---

