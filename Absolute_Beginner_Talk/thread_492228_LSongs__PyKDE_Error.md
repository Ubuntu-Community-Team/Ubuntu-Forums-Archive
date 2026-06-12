---
title: "LSongs / PyKDE Error"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by kaaaaahle on 2007-07-04
Hi, i've been using Ubuntu for a while and haven't come across any errors to where i would need to make a post in a forum, but i can't seem to find the solution to this problem.

I've been trying to install LSongs to use my Dell DJ with, and it's been nothing but a roundabout pain in the ***, having to install SIP and all sorts of modules for python.

One package i've been trying to install is PyKDE because when i try to run LSongs, i get the following error:

> Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/Lsongs/lsongs", line 20, in <module>
    from kdeemul import *
  File "/usr/lib/python2.5/site-packages/Lsongs/kdeemul.py", line 6, in <module>
    from kdecore import *
ImportError: No module named kdecore


which is fine because i know all i have to do is install the PyKDE package which has the kdecore module with it. unfortunately, when i try to install the PyKDE package:

> xxxx@xxxx:~/Desktop/PyKDE-3.16.0$ sudo python configure.py
Password:

     PyKDE version 3.16.0
           -------

Python include directory is /usr/include/python2.5
Python version is 2.5.1

sip version is 4.6 (4.6.0)

Qt directory is /usr/share/qt3
Qt version is 3.3.7

PyQt directory is /usr/share/sip/qt
PyQt version is 3.17 (3.17.0)

gcc version 4.1.2
concatenating files

Error: Couldn't locate KDE3 include directory (/usr is KDE base)

If reporting errors, paste all of the output above into your


does anyone know how to fix this KDE3 error? or does anyone have a better way to install LSongs without all this stupid crap?

---

