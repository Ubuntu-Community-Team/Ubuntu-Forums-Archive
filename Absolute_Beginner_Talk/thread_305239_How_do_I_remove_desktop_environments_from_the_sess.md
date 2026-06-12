---
title: "How do I remove desktop environments from the session picker?"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by Antarctica on 2006-11-23
A couple of days ago, I installed Enlightenment, version 16, and was not pleased at all with it.  I didn't know how to do anything, so I uninstalled it by going to tty1 (CTRL+ALT+F1), logging in, and running **sudo apt-get remove enlightenment**.  Later on, I went into synaptic and removed everything else relating to Enlightenment.  Now at the login screen, when I go to choose a section, E Gnome, E KDE, and a couple others are still there to choose from.  How can I remove those entries?  Thanks.

---

### Post by aysiu on 2006-11-23
Go to /usr/share/xsessions and delete whatever's there that's related to Enlightenment.

---

### Post by Antarctica on 2006-11-23
Thanks a lot!  I'll have to write that down!

---

### Post by aysiu on 2006-11-23
I'm kind of amazed the *apt-get remove* didn't remove the session, too, but... sometimes weird things happen.

---

### Post by rejser on 2006-11-23
Don't you have to purge to remove them?
"sudo apt-get --purge remove enlightenment"

---

### Post by Antarctica on 2006-11-23
I've got Enlightenment totally removed, but what do you mean by *purge*?  What does it mean to purge to remove?

---

