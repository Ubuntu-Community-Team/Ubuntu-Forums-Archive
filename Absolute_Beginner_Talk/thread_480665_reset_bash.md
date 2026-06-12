---
title: "reset bash"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by mdecler2 on 2007-06-21
Hi. I am playing around with my bash configuration files. How do I reset bash without running bash again, or logging out and logging back in? I know there is a command for it.

---

### Post by 5-HT on 2007-06-21
You can source the files after you've made the changes.
```
. /path/to/file 
```

For your user bashrc, for example:
```
. ~/.bashrc 
```

---

