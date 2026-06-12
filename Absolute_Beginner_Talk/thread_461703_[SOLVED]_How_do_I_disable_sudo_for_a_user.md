---
title: "[SOLVED] How do I disable sudo for a user?"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by laptoplinux on 2007-06-02
I know how to set up a root account with password like most other Linux distros in Ubuntu, but now  I would like to disable sudo access for my user account.  How would I go about doing that, and how could I re-enable sudo access for my user account if I wanted to later on?

---

### Post by jordanmthomas on 2007-06-02
take them out of any group named wheel or admin.

---

### Post by jonward0690 on 2007-06-02
Well just go to system then administration then to user groups and properties then uncheck administer the system.Now to renable sudo privilages you would have to log in as root and do the same thing to your acount just put a check next to administer the system.

---

### Post by lazyart on 2007-06-02
Remove yourself from the sudoers group and you won't be able to sudo.  You'd better leave the back door open to log in a root to undo this.

---

### Post by eentonig on 2007-06-02
If you want to go all this way to be able to work via the old linux standards, why didn't or don't you just install a distro that still works via those standards?

---

