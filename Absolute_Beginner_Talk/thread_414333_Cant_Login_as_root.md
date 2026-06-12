---
title: "Cant Login as root"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by vatechtigger on 2007-04-19
Sigh, every time I do an automatic update something stops working. 

so to login as root, at the login screen i would type root as my username, then my password.

well, after the update it now says the system administrator can no longer log in on this screen. So where do I do it then? Any help would be great. I need to log in as root to fix my fstqab again as after the update, it no longer sees my drives. Yikes!

---

### Post by tbg58 on 2007-04-19
By default the root password is disabled. The upgrade might have reverted it.
Log in as yourself then
sudo passwd root
and enter a new password.
If the root password is disabled in the standard way, this should get you going.
If it's something else, post another response and we'll have another look.
Kindest regards,
Rob in Mem

---

