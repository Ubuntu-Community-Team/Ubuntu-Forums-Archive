---
title: "Dialog box on boot"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by avanrens on 2007-08-05
I get a dialog box with the following on boot;
user's $home/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permission. user$ $home directory must be owned by user and not writable by other users. How do I prevent the dialog box from appearing at boot.

---

### Post by ddrichardson on 2007-08-05
Change the permission to 644 by doing a chmod 644 .dmrc

Did you restore this home partition from another account?

---

### Post by avanrens on 2007-08-05
Change the permission to 644 by doing a chmod 644 .dmrc
I issued the above command but that did not fix it.

Did you restore this home partition from another account?
No I didn't restore the home partition from another acc.

I am still very new to Ubuntu and some how I've changed the permission, but again this how we learn.

---

