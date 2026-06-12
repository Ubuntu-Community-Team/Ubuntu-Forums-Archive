---
title: "pkg-config - adding new package?"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by Ben Sprinkle on 2007-01-02
```

/home/user/Desktop# g++-4.1 a.cc `pkg-config gtkmm-2.4 --cflags --libs` Package gtkmm-2.4 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtkmm-2.4.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtkmm-2.4' found

```
I installed gtkmm, how do I add it to the pkg-config list?

---

### Post by apoth on 2007-02-12
```
sudo aptitude install libgtkmm-2.4-dev
```

Should do the trick.

---

