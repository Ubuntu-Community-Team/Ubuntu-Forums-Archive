---
title: "admin functions"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by vjconnor on 2006-05-14
I am unable to  do admin tasks in ubuntu desktop (configure, add users) since my root password is not recognized

i am able to use the root password and command line in terminal  / console window,
so the root password is  valid

---

### Post by tonyr on 2006-05-14
You need to enter **your** password at the password prompt.  

The Ubuntu way is to arrange for the user declared at installation to be the
system administrator, and allow him/her to do anything as root using **sudo**.

Ubuntu does not expect you to ever be logged in as root.  You violate many
Ubuntu assumptions when you do that.  See
[https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

---

