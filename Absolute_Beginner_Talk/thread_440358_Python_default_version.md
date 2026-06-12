---
title: "Python default version"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by Kazur on 2007-05-11
Hello there!

I am trying to install panda3d on Ubuntu 7.04. First I tried to install 3 different .debs for older ubuntu (there is no deb for 7.04). When that didn't work, I tried to compile it from the source, but since I have never compiled anything before, It didn't work either. I read at panda3d.com's forums that I needed python 2.4 to install the old debs. I have python 2.4 and 2.5, so the only thing I think I need to do is to change my default python version to 2.4 instead of 2.5.

Do you know how I do that? :confused: 

Thanks for replies!

---

### Post by Bachstelze on 2007-05-11
```
ls -l $(which python)
```

What does that output ?

---

### Post by Kazur on 2007-05-11
This:
lrwxrwxrwx 1 root root 9 2007-04-19 19:04 /usr/bin/python -> python2.5

---

### Post by Kazur on 2007-05-12
Bump?

---

### Post by Luiz Rocha on 2007-05-14
I ran into the same problem, although with a different application. A quick google pointed me to this page [1].

The quick & dirty hack is to edit the /usr/share/python/debian_defaults, changing the default version arg to python2.4 and then modify /usr/bin/python symlink to point to python2.4 instead to python2.5.

As the author points out, this is somewhat of a hack, so you assume responsibility if things start behaving strangely. It worked for me.

I believe there must be an easier way to do it, but that's what I found.

[1] [http://progprog.com/articles/2007/04/14/fun-with-feisty-and-python-2-5](http://progprog.com/articles/2007/04/14/fun-with-feisty-and-python-2-5)

---

### Post by Kazur on 2007-05-14
Thanks, I will check that out.

---

