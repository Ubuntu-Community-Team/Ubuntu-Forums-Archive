---
title: "Help required installing a HP 720c printer"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2008-01-03
My daughter has a PC with Ubuntu 7.10 installed and she is trying to install an old HP 720C deskjet printer connected via a parallel port to it. She is using this method: System>administration>printing to install it and although it is recognised and drivers are found, when she is asked to "apply"  she then finds a separate window opens say something like:

PASSWORD REQUIRED
Password for (mydaughtersname) on localhost.

There is then a place for her to type in a password and options to choose,
Cancel or OK

Using her main computer sign-in user password is not accepted and pressing cancel doesn't help either. I'm unsure what this password request is for or where she can find it, can anyone help please?

---

### Post by linuxwizard on 2008-01-03
Look over this

[https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/155530](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/155530)

---

### Post by a.v.l on 2008-01-04
> **linuxwizard said:**
> Look over this

[https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/155530](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/155530)

Thanks for the link, my searches on the web seem to suggest it is a problem experienced by others, hopefully this link will offer some advice.

---

### Post by LowSky on 2008-01-04
some say that the deskjet710 driver works fine
or thy to disable apparmor then reenable, and everything should work...wierd but seems to work 
in terminal type
```
 sudo aa-complain cupsd
```
AppArmor can be reenabled with:
```
 sudo aa-enforce cupsd
```

---

### Post by BruisedQuasar07 on 2008-02-06
I think you are running up against a 7.04 system bug. I have the same problem.
I find most of the time when you try to do any administrator or root only task &
you get a box telling you to input the administrator password or asking if you
wish to switch to admin and then asks for admin password; it always replies
wrong password. 

In my experience, this always happens when you need admin status to do 
something with an HP printer. Just do a hot reboot:  Ctrl Alt Backspace
& enter the administrator name and password. 

--Bruised

---

### Post by airbornemist6 on 2008-02-06
> **a.v.l said:**
> My daughter has a PC with Ubuntu 7.10 installed and she is trying to install an old HP 720C deskjet printer connected via a parallel port to it. She is using this method: System>administration>printing to install it and although it is recognised and drivers are found, when she is asked to "apply"  she then finds a separate window opens say something like:

PASSWORD REQUIRED
Password for (mydaughtersname) on localhost.

There is then a place for her to type in a password and options to choose,
Cancel or OK

Using her main computer sign-in user password is not accepted and pressing cancel doesn't help either. I'm unsure what this password request is for or where she can find it, can anyone help please?

Yes, this is indeed part of a bug in 7.10. To the best of my knowledge there is no solution, only a workaround, which is listed in this thread. On another note, you got your daughter to run linux? She must make her father very proud lol.

> **BruisedQuasar07 said:**
> I think you are running up against a 7.04 system bug. I have the same problem.
I find most of the time when you try to do any administrator or root only task &
you get a box telling you to input the administrator password or asking if you
wish to switch to admin and then asks for admin password; it always replies
wrong password. 

In my experience, this always happens when you need admin status to do 
something with an HP printer. Just do a hot reboot:  Ctrl Alt Backspace
& enter the administrator name and password. 

--Bruised
He's running 7.10, this thread is 4 weeks old, and the error you are referring to is fixed already. Update your repos, or update to 7.10, this is an apparmor bug, you're thinking about a particularly annoying kernel bug that 7.04 had.

---

