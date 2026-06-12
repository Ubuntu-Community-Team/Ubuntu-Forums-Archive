---
title: "Missing Man Pages"
date: 2006-03-14
forum: Absolute Beginner Talk
---

### Post by beej101 on 2006-03-14
How do I figure out which package a man page comes with?  In my Ubuntu install I find when I man page certain commands/system calls they're not installed for example listen() or bind()

Thanks!

---

### Post by heimo on 2006-03-14
manual pages for system calls are in manpages-dev package, which is not installed by default (as you noticed), so run:
```
sudo apt-get install manpages-dev
```

It's easy to find packages using this search:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by beej101 on 2006-03-14
although i used synaptic, thanks for telling me about manpages-dev... awesome! \\:D/

---

