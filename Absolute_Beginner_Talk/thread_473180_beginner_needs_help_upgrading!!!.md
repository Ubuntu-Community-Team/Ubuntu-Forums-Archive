---
title: "beginner needs help upgrading!!!"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-06-13
Ok, im trying to update version 6.10 to version 7.04 and i get this message after the upgrade starts:

"The upgrade aborts now. Your system could be in an unusable state. A recovery will run now (dpkg --configure -a).

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.
installArchives() failed"


Any suggestions????

---

### Post by locke.dragon on 2007-06-13
there's already a thread about this.  please don't post twice.  if you must, just do a simple
> 
bump

post.

cheers!

---

### Post by zvacet on 2007-06-14
Edgy must be up-to-date if you want to do upgrade.

```
sudo aptitude update
```

After this try again.

---

