---
title: "Problem with add/remove applications"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by crystalireland on 2007-10-22
When i try to get anything from the add/ remove thing, it says 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

If I try to upgrade to 7.10, it says 
Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first.

even if nothing else is running! help

---

### Post by Maestro23 on 2007-10-22
Did you try what it said?

> sudo dpkg --configure -a

---

### Post by crystalireland on 2007-10-22
now the update manager says 
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
and if i do that it comes up with an install screen for java and I can't do anything on it
and the add/remove isn't responding

---

### Post by crystalireland on 2007-10-22
Now the update manager says
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

---

