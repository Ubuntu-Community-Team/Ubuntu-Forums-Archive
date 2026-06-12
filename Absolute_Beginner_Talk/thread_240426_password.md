---
title: "password"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by chromaglow on 2006-08-20
Is there a su password other than the one i set up for my profile because everytime i enter my password it says authentication failure....

anyone?
anyone?

---

### Post by mssever on 2006-08-20
Use sudo (with your regular password) instead of su. By default, the root password is disabled in Ubuntu.

EDIT: sudo -i will give you a root shell. Use gksudo for graphical programs.

---

### Post by Madpilot on 2006-08-20
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Ubuntu is set up to use sudo & your regular user password, rather than root/su/etc.

---

### Post by uberg on 2006-08-22
Most traditional flavors of Unix (ie. Linux) set up a root account.  Ubuntu doesn't.  You have to use sudo anytime you want to run something with root privileges.  If you really want to you can enable the root account.  This wiki page explains more:[https://help.ubuntu.com/community/RootSudo#head-8352bb412ccfc81b89a48144986e8690c66e338c](https://help.ubuntu.com/community/RootSudo#head-8352bb412ccfc81b89a48144986e8690c66e338c)  Section 6 in particular explains how to enable the root account.  

My first install of Ubuntu i enable the root account as it felt weird to not have it available but have since learned to work without it.  Good luck!

---

