---
title: "how do i force a package to install???"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-08-13
it seems i have a version that is accepted so i need to install another version.If i try to remove the package it wants to also remove about 20 other  packages as well..Mainly alot of my media players

The following packages have unmet dependencies:
  libfaac-dev: Depends: libfaac0 (= 1.24clean-0ubuntu4) but 1.24+cvs20060416-0.1 is to be installed


i need to install libfaac-dev but i can't cause i have libfaac0 1.24+cvs20060416-0.1 installed

So i need to remove that package and install the 1.24 clean version

---

### Post by Fass on 2006-08-13
```
dpkg --force-help
```

That will output help about the force attributes. The dpkg man page is more detailed.

---

### Post by jISh on 2006-08-13
Sometimes you can't upgrade packages without breaking others, you might have to wait until an update version is in the repositories or for the release of Edgy.

---

