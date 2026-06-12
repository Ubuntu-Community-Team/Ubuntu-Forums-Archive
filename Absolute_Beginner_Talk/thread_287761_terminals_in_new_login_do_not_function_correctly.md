---
title: "terminals in new login do not function correctly"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by IanVaughan on 2006-10-29
Due to another problem I am [having]("http://www.ubuntuforums.org/showthread.php?p=1678463") I created a new account, of which the terminal does not function correctly.

The tab key actually tabulates, instead of auto-completing. 
And the arrow keys produce control chars, instead of moving the cursor or showing last commands.

---

### Post by IanVaughan on 2006-10-29
Ok, so that solves that one!

The new user account had the wrong Shell!
Via Gnome gui, System->Administration->Users and Groups,
Select the account, select Properties, Advance
Change Shell to "/bin/bash" (Mine was set to "/bin/sh")
And Re-login.

Not sure how to change this via cli?
Also not sure where the default is of /bin/sh?

---

