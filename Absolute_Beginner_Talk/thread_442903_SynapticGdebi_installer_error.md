---
title: "Synaptic/Gdebi installer error"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by tabithaboof on 2007-05-14
I seem to be having problems with Synaptic and the deb installer.

When running Synaptic I get this error

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

Unfortunately I dont understand what dpkg is and entering the above command in terminal give me a message "requested operation required a superuser privilege"

When running the Gdebi package installer I get an error saying 

"Onlye one software management tool is allowed to run at the same time

Please close the other application e.g. "update manager" aptitude" or "synaptic" first"

But I dont have anything else running. I would really appreciate some help with this one.

---

### Post by alienexplorers on 2007-05-14
You have to enter
 > sudo dpkg --configure -a

---

