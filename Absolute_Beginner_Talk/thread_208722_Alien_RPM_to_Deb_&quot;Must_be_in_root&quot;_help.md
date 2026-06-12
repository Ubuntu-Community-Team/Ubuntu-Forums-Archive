---
title: "Alien RPM to Deb &quot;Must be in root&quot; help"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by battleroyalex on 2006-07-04
Whenever I try to convert a .rpm file to .deb I get this error

**Must run as root to convert to deb format (or you may use fakeroot).**

what should I do?

---

### Post by MaximB on 2006-07-04
run the sudo command before the alien...
sudo alien yourfile.rpm
you still going to need a password

---

### Post by battleroyalex on 2006-07-04
ah I actually downloaded something called fakeroot typed that in then ran the alien console line and that worked too

---

### Post by MaximB on 2006-07-04
and it didn't ask you for your password ?
please pose the link and name of this program

---

### Post by battleroyalex on 2006-07-04
seach for "alien" in the package manager and install it

then type fakeroot

it will log you into something like root@username: and no it didn't ask for a password

---

