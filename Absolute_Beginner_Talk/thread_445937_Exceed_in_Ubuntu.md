---
title: "Exceed in Ubuntu?"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by jdrodrig on 2007-05-16
Hi All,

This is my first week with Ubuntu and I still have some pretty basic questions.

So far -in my soon to be deleted- Windows partition I use my Campus' Matlab and Mathematica through a combination of Putty's ssh and Exceed X-Window in order to get the graphical interface of such programs. What would be the equivalent in Ubuntu? Both applications reside in a machine in which uname -a gives:

Linux thor.socsci.umn.edu 2.6.9-42.0.10.ELsmp #1 SMP Fri Feb 16 17:13:42 EST 2007 x86_64 x86_64 x86_64 GNU/Linux

Thanks,
Daniel

---

### Post by Najand on 2007-05-16
You need to login your campus using:
```

$ ssh -Y USERNAME@DOMAIN
```
(Change USERNAME and DOMAIN with suitable values)
on a terminal in gnome or X server in general.
Then try to run your GUI included programs using ordinary commands.

---

### Post by carlosqueso on 2007-05-16
You should be able to open up a terminal and type ```
ssh -X <username>@thor.socsci.umn.edu
``` where <username> is your username on the UMN servers.

---

### Post by jdrodrig on 2007-05-16
Thanks a lot for the quick response, I will try that right away.

---

