---
title: "Help with devede"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by dangerpl on 2007-04-15
After installing devede I can't open it. I get an error saying: Failed to load modules 2. Exiting

Help? Anyone?

---

### Post by caffienefree on 2007-04-15
Try invoking it using ./devede.py from the directory?

---

### Post by zvacet on 2007-04-15
[https://help.ubuntu.com/community/DVDAuthoring]("https://help.ubuntu.com/community/DVDAuthoring")
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by tuga on 2007-05-11
Hello,

I was having the same problem as dangerpl. Then I install devede 2.13.

Now I get these errors:

(devede:11525): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Psyco not installed, the program will just run slower
DeVeDe 2.13
Traceback (most recent call last):
  File "/usr/local/bin/devede", line 123, in <module>
    locale.setlocale(locale.LC_ALL,"")
  File "/usr/lib/python2.5/locale.py", line 476, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting

Edit: Running on 7.04 amd64

---

