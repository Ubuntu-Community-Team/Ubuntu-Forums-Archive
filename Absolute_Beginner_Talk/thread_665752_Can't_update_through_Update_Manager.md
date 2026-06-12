---
title: "Can't update through Update Manager"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by jamesburns on 2008-01-12
Please help
When in update manager I cannot update software. Am getting: 

Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '31457283' '--progress-str' 'Please wait, this can take some time.' '--finish-str' 'Update is complete' '--set-selections-file' '/tmp/tmp4wuKwO' as user root.

The underlying authorisation mechanism (sudo) does not allow you to run this program. Contact the system administrator.

Any ideas please

James

---

### Post by eapache on 2008-01-12
How are you running it? If you're running it from the command line, don't run it as sudo. If you are using the menu link, open up the menu editor (right-click) and print out what the update manager link says.

---

### Post by taurus on 2008-01-12
Or what happens if you run these two commands from a terminal, assuming you close synaptic down first?

```
sudo apt-get update
sudo apt-get upgrade
```
Use the same password that you log in with.

---

