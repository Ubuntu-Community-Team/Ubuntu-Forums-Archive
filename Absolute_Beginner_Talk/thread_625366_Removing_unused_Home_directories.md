---
title: "Removing unused Home directories"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by justanut on 2007-11-27
Hi there... not sure if this has been posted before, but how do you delete unwanted folders in /home left over from obsolete profiles? The profile has already been deleted.

I've tried sudo rmdir --ignore-fail-on-non-empty folder
Doesn't work... the delete option doesn't even come up on the Places viewer on Ubuntu.

Btw, i'm on 7.10

Help would be appreciated! Thanks

---

### Post by qpieus on 2007-11-27
try in a terminal```
sudo rm -r /home/*username* 
```
this should remove the directory and it's contents.

---

