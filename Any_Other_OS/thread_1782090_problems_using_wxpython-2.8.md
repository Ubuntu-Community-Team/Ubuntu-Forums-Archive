---
title: "problems using wxpython-2.8"
date: 2011-06-14
forum: Any Other OS
---

### Post by mentaaal on 2011-06-14
Hi guys, I am hoping some clever soul can help me out with this problem and I hope nobody minds me posting this question on this site. I am using linux mint x64 "julia" which i believe is based around ubuntu maverick. I am trying to use wxpython 2.8 for use in a project but I cannot. I have it installed ok including wxlib 2.8 but in a python interpreter when I try to import wx I get the following error traceback:


```
greg@Lappy ~ $ python
Python 2.6.6 (r266:84292, Sep 15 2010, 16:22:56) 
[GCC 4.4.5] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import wx
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/__init__.py", line 45, in <module>
    from wx._core import *
  File "/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 14813, in <module>
    from _gdi import *
  File "/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/_gdi.py", line 4, in <module>
    import _gdi_
ImportError: /usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/_gdi_.so: symbol _ZTV14wxGraphicsPath, version WXU_2.8 not defined in file libwx_gtk2u_core-2.8.so.0 with link time reference
>>> 
```I have trawled the internet for the past few days and cannot find a solution to it although many people have reported similar issues. I have tried reinstalling/uninstalling wxpython 2.8 and the associated libwx but to no avail. I would like to use this version as then I can use wxGlade to design a front end. 

Please note also that uninstalling wxpython 2.8 and using 2.6 allows me to use wxpython no problem.

P.S. the wxpython version I have installed according to synaptic is 2.8.12.

Thanks in advance

---

### Post by Perfect Storm on 2011-06-14
Moved to Other OS/Distro Talk.

---

### Post by zacktu on 2011-06-14
Go to the freenode server on IRC and join #wxpython.  I think that folks there will have answers to a more specific question such as yours.  Robin Dunn, who wrote wxPython in Action, is often there..  There are also several wxpython groups at groups.google.com.

---

