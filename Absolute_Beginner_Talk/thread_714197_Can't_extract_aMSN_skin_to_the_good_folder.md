---
title: "Can't extract aMSN skin to the good folder"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by VoXoM on 2008-03-03
I tried extracting an aMSN skin to the amsn skin folder but this error appeared.

tar: aMSN Live-1.0: Cannot mkdir: Permission denied

---

### Post by owbizi on 2008-03-03
Try using the same command with *sudo* before it.

Or, alternatively, change permissions of that file:
$ chmod 777 nameofthearchive

And then extract it.

---

### Post by VoXoM on 2008-03-03
> **owbizi said:**
> Try using the same command with *sudo* before it.

Or, alternatively, change permissions of that file:
$ chmod 777 nameofthearchive

And then extract it.

What would be the command with sudo if the name of the archive is aMSN_Live-1.0.tar.gz located on the desktop, and if the skin folder is located in usr/share/amsn/skins?

---

