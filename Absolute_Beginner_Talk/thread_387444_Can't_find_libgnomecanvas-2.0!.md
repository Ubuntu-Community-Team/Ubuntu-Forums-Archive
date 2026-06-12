---
title: "Can't find libgnomecanvas-2.0!"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by xiexiehezuo on 2007-03-18
I met a problem when I tried to install a software. 

I am using Ubuntu Edgy.  The command for the installation is:
python setup.py build
python setup.py install

When I input "python setup.py buid", the error came:
Can't find libgnomecanvas-2.0! Version 2.6 or later required

I found I have a library  /usr/lib/libgnomecanvas-2.so.0. But how can I use it and install the software? Since the library is not libgnomecanvas-2.0.so.

Does anyone have any idea about this issue? Or would anyone tell me where should I ask for help. Thanks.

---

### Post by h0ax on 2007-03-18
try 
sudo apt-get update libgnomecanvas

or
sudo apt-get install libgnomecanvas

one of those might help

---

### Post by xiexiehezuo on 2007-03-18
Both don't work. But thanks, anyway.

---

