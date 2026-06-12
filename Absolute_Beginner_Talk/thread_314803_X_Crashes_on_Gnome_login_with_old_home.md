---
title: "X Crashes on Gnome login with old /home"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by compwiz18 on 2006-12-08
I have my /home on a separate partition, and whenever I login to GNOME it doesn't work (I get returned to the login prompt) But if I try it with a different (fresh) user it works.  Any suggestions?  If you need more info I can give it to you, I'm just not sure what other info to post.

---

### Post by bapoumba on 2006-12-08
Hi,
if it is okay with a fresh user, this means there are problems with your regular user .conf files.

First check you have enough room on your partitions (**df -h**, should not be this as your fresh user is OK) and use the **default Human theme** if not already using it.

Then check .gconf and .gnome*. If you rename them one by one , and restart your regular session, you should be able to narrow down which one is messing up (a new default conf file will be created).

---

