---
title: "New user.."
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by raven5 on 2007-01-08
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

This message comes up when trying to "add/remove" programs or when using synaptic package manager. I'm on Ubuntu 6.10 edgy. Its worked fine before. Any ideas please on how to run this in manual , I've wrote this in "terminal" but nothing happens.:-?

---

### Post by moma on 2007-01-08
Goto command line (menu selection: Applications -> Accessories -> Terminal) and run:
$ [COLOR="SeaGreen"]sudo dpkg --configure -a[/COLOR]

---

### Post by kj1h234lkj1234 on 2007-01-08
Try running:
```
sudo dpkg --configure -a
```

in Applications -> Accessories -> Terminal, and copy/paste the output here if the problem doesn't go away.

---

### Post by raven5 on 2007-01-08
Thanks...that worked fine:)

---

### Post by Josh1 on 2007-01-08
If it asks you to type something in Command Line, usually you will need to add "sudo" (superuser) before the command it asks you to type in.

---

