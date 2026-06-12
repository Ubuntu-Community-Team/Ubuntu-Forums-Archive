---
title: "Removing file from root directory...?"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2006-05-13
I have managed to browse to the location of the file, but do not know the commands to actually remove the file... Also do I need to go to that actual file, or just the directory?

(xpti.dat needs to be removed from /usr/lib/mozilla-firefox/components)

---

### Post by IYY on 2006-05-13
from anywhere:

```
sudo rm /usr/lib/mozilla-firefox/components/xpti.dat
```

or go to the directory, and then:

```
sudo rm xpti.dat

```

---

### Post by Papa-san on 2006-05-13
Thanks!

Who woulda figured it would be that easy. I guess I keep trying to complicate things too much!

---

