---
title: "Quod Libet Uninstall HELP"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by shagey36 on 2007-01-02
hey everybody...i kinda got myself in a wierd situation here
i installed quod libet from the package manager and all was well until i found out that there was a later version of quod libet available that was not accessible from the package manager....so i uninstalled the quod libet i already had and attempted to install the later version but that install kept on failing
i wanted to revert back to the quod libet that i initially had (from the package manager) so i deleted all pieces of quod libet that i could find and reinstalled it from the package manager
now i cant run quod libet at all...i figure itll work if i completely remove it and reinstall it.... so how would i go about completely uninstalling every piece of quod libet remaining on my system?

oh and if it helps...in my applications menu quod libet is listed but it doesnt work (because the majority of it is already uninstalled

---

### Post by SyvanX on 2007-01-02
Did you attempt to install from source? If so you could remove the newly installed version by going into the source directory and trying:

```
sudo make uninstall
```

You might want to try using aptitude to reinstall the Quod Libet.

```
sudo aptitude reinstall quodlibet quodlibet-ext quodlibet-plugins
```
(if you did not install the plugins or extensions, you can remove those from the reinstall command)

---

### Post by hugmenot on 2007-01-02
you can delete all the stuff that is returned by 

locate -r /usr/local/.*quodlibet

---

### Post by shagey36 on 2007-01-03
ok i uninstalled it and reinstalled it...now when i try to run it i see

Traceback (most recent call last):
  File "/usr/bin/quodlibet", line 288, in ?
    import locale, gettext, util
ImportError: No module named util


any ideas?

---

