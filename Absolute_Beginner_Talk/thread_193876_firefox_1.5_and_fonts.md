---
title: "firefox 1.5 and fonts"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by nip37 on 2006-06-10
I'm using ubuntu since two months, i installed breezy badger 5.10 first and was using  mozilla firefox that came with it, in breezy badger i upgraded the firefox to version 1.5 and found out it doesnt shows urdu fonts correct so i roled back to the breezy badger default firefox, now i have upgraded breezy badger to ubuntu 6.06 LTS and default browser is firefox 1.5 and again the same problem it does not shows urdu fonts correctly, i mean i can read pages easily but it is not the real font, i can use urdu fonts with all other programmes like gimp, open office but cant see them in firefox, how can i fix this, so i dont have to roleback again :(

---

### Post by bollix47 on 2006-06-10
Anything [here]("http://forums.mozillazine.org/viewtopic.php?t=345780&highlight=urdu") or one of the links there help?

---

### Post by noumaan on 2006-08-23
nip37 its a [known bug]("https://launchpad.net/distros/ubuntu/+bug/54091"). A temporary way to resolve this bug in dapper is by adding following line:

MOZ_DISABLE_PANGO=0 

in /etc/environment

---

