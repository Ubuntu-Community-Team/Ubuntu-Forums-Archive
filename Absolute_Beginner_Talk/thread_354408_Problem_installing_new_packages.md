---
title: "Problem installing new packages"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by Freemind11 on 2007-02-05
Whenever I try to install a new package it tells me this:

E: dpkg was interrupted, you must manually run 'dpkg --configure - a' to correct the problem.


I bring up the terminal but when I try to run that through the command line it gives me this message:

dpkg: requested operation requires superuser privilege


Now, I'm not sure what that means but I'm guessing it's trying to say I'm not the system administrator or whatnot. Only problem is, I am. I only have one user on the system and it's the same one I installed with. Any help would be very much appreciated.

---

### Post by meng on 2007-02-05
Try
sudo dpkg --configure -a

and enter your user password when prompted.

---

### Post by taurus on 2007-02-05
Applications -> Accessories -> Terminal
```
sudo dpkg --configure - a
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install **package_name**
```

---

