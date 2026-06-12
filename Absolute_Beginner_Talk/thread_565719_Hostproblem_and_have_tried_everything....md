---
title: "Hostproblem and have tried everything..."
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by Captaingracekidd on 2007-10-02
Hi, I have seen loads of threads here on how you fix a hostproblem. I accidently deleted my hostname. I have tried everything from changing the /etc/hosts in recovery mood to sudo chmod commands. Nothing works! ](*,) Cant access my internet, upgrade or install.

Im very much a newbie so please describe as thorough as possible.

Thanks... I love ubuntuforums. \\:D/

---

### Post by SpiritIsReality on 2007-10-02
howdy
about 2/3 down this page, under the heading network configuration files.
should be some help there.
[http://aboutdebian.com/network.htm](http://aboutdebian.com/network.htm)
buds
edit: if there's not much to lose, a quick reinstall would do?

---

### Post by dwhitney67 on 2007-10-02
I believe the host name resides in /etc/hostname.  Try this:

[FONT="Courier New"]$ sudo echo *myHostName* > /etc/hostname[/FONT]

where you substitute *myHostName* with the appropriate name that you want.

At a minimum, your /etc/hosts file should have an entry like this:
[FONT="Courier New"]
127.0.0.1       localhost.localdomain localhost[/FONT]

---

