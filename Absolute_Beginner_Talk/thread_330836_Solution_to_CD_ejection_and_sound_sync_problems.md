---
title: "Solution to CD ejection and sound sync problems"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by DavidJE13 on 2007-01-03
I'm posting this for future reference, since I've had these problems for a long time and just found the fix;

Problems:

1) Music CDs are ejected seemingly randomly while playing
2) Sounds are 1/2 second out of sync in games

Solution:
Install the libsdl1.2debian-all package (Applications->Add/Remove->Advanced - find libsdl1.2debian-all in the list and mark for installation, then click apply)

(Note that this will automatically uninstall the libsdl1.2debian package)

Also note that some people say this fix doesn't work for them. If it doesn't work for you, take a look at this bug page for some variations:
[https://launchpad.net/ubuntu/+source/libsdl1.2/+bug/37774](https://launchpad.net/ubuntu/+source/libsdl1.2/+bug/37774)

---

