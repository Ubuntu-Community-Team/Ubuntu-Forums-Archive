---
title: "uninstalling openproj"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by cjnkns on 2007-10-14
I have installed openproj which seems pretty nice so far - I plan to use it for a Project Management class next term.
But, how do I uninstall openproj? I looked in the directory where it's installed /usr/share/openproj but I can not seem to find any scripts that would allow me to do so.I was able to installit using a .deb file but if I want to upgrade it I would ike to know how to remove the current version...

Thanks,

---

### Post by Dr Small on 2007-10-14
```
sudo dpkg -r openproj
```

You could try that, since you installed it via a .deb.

Dr Small

---

### Post by cjnkns on 2007-10-14
Thanks for the reply it's much appreciated!

---

