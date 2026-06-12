---
title: "Questions about updating Ubuntu"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by iamthemicrowave on 2007-12-11
My update manager doesn't automatically tell me when there are new updates, even though I have it set to check daily.  I always have to manually open the the update manager.

Also, could someone please explain me the difference between
sudo aptitude update
sudo aptitude upgrade/safe-upgrade/full-upgrade

What am I updating when I run these commands?

One more question :)  How do I modify and edit /etc/sudoers?  I have opened and modified it with visudo, but how do I save changes?

---

### Post by LaRoza on 2007-12-11
> **iamthemicrowave said:**
> 
One more question :)  How do I modify and edit /etc/sudoers?  It says I have no applications that can open the file.

use "visudo", it is the only way.

---

### Post by OffAxis on 2007-12-11
```
sudo aptitude safe-upgrade 
```

ONLY updates installed packages. If there are any new dependencies they won't be downloaded nor installed.

```
sudo aptitude full-upgrade
```
will download and install all dependent packages.

and "upgrade" has been deprecated.

---

