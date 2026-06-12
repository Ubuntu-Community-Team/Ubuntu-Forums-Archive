---
title: "backup"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by squrl on 2006-12-29
I made a tar backup it is in  /root directory.  What should the command line look like to get this restored to the original location preserving the permissions.


Thanks

---

### Post by d1337 on 2006-12-31
Holidays are sometime rough on the help thing...

[This Link]("http://ubuntuforums.org/showthread.php?t=35087") (Thanks Heliode) may do the trick for you.   ```
tar xvpfz backup.tgz -C /
``` would probably do the trick, but the article is a good read nonetheless to insure that you've got a grasp on where you are at and who you are :).

HTH,
d1337

---

