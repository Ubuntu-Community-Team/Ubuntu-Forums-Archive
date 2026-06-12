---
title: "XUbuntu 7.10 screensaver not comming on"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by winterfire on 2008-01-03
This is becoming a bad habit. Now  I've got a new question. I have just installed  XUbuntu on a second laptop(same type and configuration as my first one) The only diffrence is the user name and laptop name are diffrent. I have the screensaver to come on at 5 minutes and to lock the screen when it does. but the screensaver does'nt come on and the screen goes blank but doesent lock. How do I get the screensaver to work? And while I'm setting things up, where is "power management" in the XUbuntu menu?
                  Sorry to be a pain.

---

### Post by gn2 on 2008-01-06
Applications>Settings>Settings Manager>Screensaver>Advanced
Should get you fixed up.

---

### Post by chewearn on 2008-01-20
> **gn2 said:**
> Applications>Settings>Settings Manager>Screensaver>Advanced
Should get you fixed up.

I just installed Xubuntu over the weekend, came across the same problem as the OP.  Your suggestion quote above; but there is no "Advanced" anywhere on the Screensaver dialog.

---

### Post by chewearn on 2008-01-20
Ok, nevermind, after somemore googling, I came across this:
[https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/68251](https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/68251)

Looks like gnome-screensaver is not launched automatically due to bug; so manually add a start-up entry solves the problem.

---

### Post by gn2 on 2008-01-20
> **AstalaVista said:**
> I just installed Xubuntu over the weekend, came across the same problem as the OP.  Your suggestion quote above; but there is no "Advanced" anywhere on the Screensaver dialog.


Oops, it must have been changed in 7.10.

---

