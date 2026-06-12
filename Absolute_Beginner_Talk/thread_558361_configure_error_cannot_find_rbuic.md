---
title: "configure: error: cannot find rbuic"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by ChompTheMan on 2007-09-23
Hi there.  I am trying to install Knfo from source and after installing the necessary libraries and dev tools I get this when it is checking for ruby directories while configuring

"checking whether Korundum is installed... no
checking for rbuic... no
configure: error: cannot find rbuic (part of the QtRuby package)"

What else do I need to install?

Thx

---

### Post by jordanmthomas on 2007-09-23
Forgive me if this is a dumb question, but have you looked for the qt - ruby development package in synaptic?

---

### Post by jw5801 on 2007-09-23
```
~$ rbuic
The program 'rbuic' can be found in the following packages:
 * libqt0-ruby1.8
 * libqt0-ruby1.8-qt4
Try: sudo apt-get install <selected package>
```
Try installing those two packages and see what happens!

---

### Post by jordanmthomas on 2007-09-23
For the record, unless you know that you want qt4, don't choose the qt4 option.

---

### Post by ChompTheMan on 2007-09-24
Thank you jw5801.  I didn't know you could do that in the CLI, that's really handy.  I didn't know if I wanted qt4, so I didn't get it.  It finished configuring but now there is a problem when I enter make.  But I'm tired now so I'll worry about that tomorrow. :)

---

### Post by jw5801 on 2007-09-24
Well post the error back here and we shall help you out! The most common one you'll encounter when compiling can be fixed with ```
sudo apt-get install build-essential
``` if you haven't done that already.

---

