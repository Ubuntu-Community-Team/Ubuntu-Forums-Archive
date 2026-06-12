---
title: "having a problem wiht ndisgtk"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by endlessurf on 2007-10-30
I tried using synaptic and .deb from the web site.  But I keep getting this error.  I 'm trying to figure out what is going wrong.  I got the wireless card I am using now to work with gutsy but I am having problems with fiesty.

@carputer:~$ sudo ndisgtk
Traceback (most recent call last):
  File "/usr/bin/ndisgtk", line 309, in <module>
    NdisGTK()
  File "/usr/bin/ndisgtk", line 111, in __init__
    self.setup_driver_list()
  File "/usr/bin/ndisgtk", line 140, in setup_driver_list
    self.get_driver_list()
  File "/usr/bin/ndisgtk", line 168, in get_driver_list
    driver_name = p.search(line).group()[:-1]   # strip trailing space
AttributeError: 'NoneType' object has no attribute 'group'

---

### Post by youthforlinux on 2007-10-30
Did you install ndiswrapper-utils-1.9 and the other dependencies?

---

