---
title: "Odd Error W/ Python?"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by chris062689 on 2008-02-28
chris@eeepc:~$ ccsm

(ccsm:6500): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 39, in <module>
    import ccm
  File "/usr/lib/python2.5/site-packages/ccm/__init__.py", line 1, in <module>
    from ccm.Conflicts import *
  File "/usr/lib/python2.5/site-packages/ccm/Conflicts.py", line 29, in <module>
    locale.setlocale(locale.LC_ALL, "")
  File "/usr/lib/python2.5/locale.py", line 478, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting
chris@eeepc:~$ 

Then when I removed some packages..
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
/usr/sbin/update-default-wordlist No wordlist elements installed.


This happened when I attempted to run conpiz config settings manager.
I'm running eeexubuntu.
I think I may be missing a C library?
What can I do to fix this?

---

### Post by es@urito on 2008-02-29
It seems that you have a problem with your locale settings.

Try this:
```
sudo dpkg-reconfigure locales
```

So you can reconfigure your locale settings.
Good luck!

---
es@urito

---

