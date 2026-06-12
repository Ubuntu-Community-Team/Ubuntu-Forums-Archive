---
title: "Why apt-get update, upgrade and dist-upgrade"
date: 2005-07-30
forum: Absolute Beginner Talk
---

### Post by kayas80 on 2005-07-30
Hey all

Could someone please explain the difference between apt-get update, upgrade and dist-upgrade.  :???: 

Thanks

Oliver

---

### Post by heimo on 2005-07-30
Shortly and simply: update updates the information about which packages are available, upgrade upgrades packages that have newer versions available (but doesn't install any new packages), dist-upgrade updates also dependencies - and it may install new packages if dependencies have changed (it's usually used to upgrade distribution version, like from Warty to Hoary or Hoary to Breezy). *


EDIT: *) And now try to say that five times as fast as possible. ;)

---

### Post by kayas80 on 2005-07-30
[QUOTE=heimo]Shortly and simply: update updates the information about which packages are available, upgrade upgrades packages that have newer versions available (but doesn't install any new packages), dist-upgrade updates also dependencies - and it may install new packages if dependencies have changed (it's usually used to upgrade distribution version, like from Warty to Hoary or Hoary to Breezy). *


EDIT: *) And now try to say that five times as fast as possible. ;)[/QUOTE]


Excellent, thats exactly the short and simple type of explanation I was looking for. 

thanks

---

