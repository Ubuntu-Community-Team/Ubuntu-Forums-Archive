---
title: "Python cannot find module 'gnome.applet'"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by bff7755a on 2007-04-22
Hi all.

I wrote a simple GNOME application on Python, but when I try to execute it I have

```
mutex@ibm:~/src$ python ./pysample.py 
Traceback (most recent call last):
  File "./pysample.py", line 7, in <module>
    import gnome.applet
ImportError: No module named applet

```

It it helps:

```
mutex@ibm:~/src$ locate gnomeapplet
/usr/lib/python2.4/site-packages/gtk-2.0/gnomeapplet.so
/usr/lib/python2.5/site-packages/gtk-2.0/gnomeapplet.so
```

---

### Post by Mr. Picklesworth on 2007-08-19
Yes, it seems gnome.applet has been replaced with gnomeapplet, and for some reason there are absolutely no articles on it and every forum / mailing list thread regarding it (anywhere) appears to be empty.
The only articles I have found are either from 1999 or 2004, which are both too old :(

help(gnomeapplet) in Python is the best help I have found so far.

Does anyone know of a current and good (commented) example or tutorial on this topic?


Edit:
[This here](http://ubuntuforums.org/showthread.php?t=496185) (post #3, by Quikee) looks helpful, but is not very in-depth.

---

### Post by zecarioca on 2008-02-11
I can't find any reference material either, and I'm having lots of problems figuring out about things like setup_menu()... If you find anything about it please let me know!

---

