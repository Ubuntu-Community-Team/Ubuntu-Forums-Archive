---
title: "[SOLVED] Upgrades from terminal"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Blue Sassley on 2007-10-22
I seem to not understand when I run "sudo apt-get upgrade" at the terminal on my MythTV backend server there are three packages that don't get upgraded... can someone please tell me why and if I need them? Otherwise everything is working great although Windows XP Pro is still my primary OS as I'm still learning Ubuntu

```
myth@mythtv:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  gnupg linux-image-generic linux-restricted-modules-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
myth@mythtv:~$

```

Thanks for the help,
Blue

---

### Post by Sef on 2007-10-22
> I seem to not understand when I run "sudo apt-get upgrade" at the terminal on my MythTV backend server there are three packages that don't get upgraded... can someone please tell me why and if I need them?

They are being held back for some reason.  Once they are ready then they will be released.

---

