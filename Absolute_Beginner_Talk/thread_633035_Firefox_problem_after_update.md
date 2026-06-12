---
title: "Firefox problem after update"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by bail_w on 2007-12-06
After i upgrade firefox to 2.0.0.11, it give me this problem. i have try to remove it and reinstall firefox but it does not solve the problem. Help please

---

### Post by lswest on 2007-12-06
ok, couple of ideas here.
A) check your hard drive, make sure it's not full

B) try running firefox as sudo, and see if the error is there (if not, it means it is a permissions problem)

C) uninstall firefox, and delete the hidden folder (you can see hidden files by pressing ctrl + H in nautilus) /home/[yourname]/.mozilla/  then re-install and it will then re-install those files, might solve your problem.

if any of those work, or if you get a different error, let us know, might help us figure this one out.

---

### Post by judolars on 2007-12-06
Please note that removing your profile directory will also delete all bookmarks, history, passwords, etc. A less drastical solution is suggested in this article from MozillaZine: [http://kb.mozillazine.org/Could_not_initialize_the_browser_security_component]("http://kb.mozillazine.org/Could_not_initialize_the_browser_security_component")

The instructions there are for Windows users, but should also work for you. As lswest said, the profile directory is located in your home directory, under .mozilla/firefox. It has some random name that ends with ".default".

---

### Post by bail_w on 2007-12-06
> **lswest said:**
> ok, couple of ideas here.
A) check your hard drive, make sure it's not full

B) try running firefox as sudo, and see if the error is there (if not, it means it is a permissions problem)

C) uninstall firefox, and delete the hidden folder (you can see hidden files by pressing ctrl + H in nautilus) /home/[yourname]/.mozilla/  then re-install and it will then re-install those files, might solve your problem.

if any of those work, or if you get a different error, let us know, might help us figure this one out.

A) there are plenty spaces 
B) tired that, problem still occurs.
C) will try that

---

