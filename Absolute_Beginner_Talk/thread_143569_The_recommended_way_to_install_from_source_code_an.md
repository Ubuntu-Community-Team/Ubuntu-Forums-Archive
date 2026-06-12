---
title: "The recommended way to install from source code and yet managed by package system?"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-03-12
Suppose I download the source.tar. What is the recommended way to install from the source code and yet manageable by the aptitude package system?

One method I read of is to install (.configure, make, checkinstall) with the help of checkinstall package and then manually install the deb package created with dpkg.

Is there a better method?

Thanks !

---

### Post by %hMa@?b&lt;C on 2006-03-12
checkinstall is really the only way

---

### Post by skymt on 2006-03-12
Yes, checkinstall is the only way, but it's not hard at all. You don't even have to manually install the .deb, it does that for you. The only manual bits are moving readme files to a directory called doc-pak (that way they get installed under /usr/share/doc, not essential, but useful), and answering a couple questions (name and description of package).

---

