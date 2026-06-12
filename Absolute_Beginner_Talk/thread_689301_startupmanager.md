---
title: "startupmanager"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by tomor on 2008-02-06
I'm having problems with starting startup manager. I'm receiving this error:

tomor@tomor:~$ startupmanager
/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:48: RuntimeWarning: tp_compare didn't return -1 or -2 for exception
  from gtk import _gtk
ImportError: could not import atk
ImportError: cannot import name Object from gtk


Help appreciated

---

### Post by Cypher on 2008-02-07
Did you install the 'startupmanager' package from REPOS or install it manually?

---

### Post by jan quark on 2008-02-07
install startupmanager through the synaptic package manager,

the needed dependencies will be installed automatically with it.

---

