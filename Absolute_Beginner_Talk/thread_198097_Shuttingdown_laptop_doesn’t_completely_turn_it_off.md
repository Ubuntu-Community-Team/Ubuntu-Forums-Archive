---
title: "Shuttingdown laptop doesn’t completely turn it off!"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by ssalman on 2006-06-16
[FONT=Verdana]I had a fresh install of Dapper and it went great, but I went on changing my startup services using BUM and installed 686 kernel together with few other applications, and now my laptop will not completely poweroff when I shutdown, it goes all the way with the power down scripts but will not turn it self off, I have to press the button my self.

[/FONT]       [FONT=Verdana]This used to wok when I first installed Dapper, where would I look to fix this? What service could have affected this?[/FONT]

---

### Post by givré on 2006-06-16
Try to revert to the 386 kernel.
This kind of problem can only be due to the kernel.
Also, if the problem persist, fill a bug here [https://launchpad.net/distros/ubuntu/+filebug](https://launchpad.net/distros/ubuntu/+filebug)
Or reopen this one [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/43961](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/43961)
It seams that the problem is solve for the 386 kernel, but not for the 686

EDIT : check also that you have the latest kernel (actually 2.6.15-25) (uname-r for checking)

---

### Post by ssalman on 2006-06-18
Thank you givre, it was due to the kernel, i386 kernel worked fine, I can live with this kernel just fine, thanks.

---

