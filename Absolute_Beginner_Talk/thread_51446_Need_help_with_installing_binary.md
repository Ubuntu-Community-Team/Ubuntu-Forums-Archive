---
title: "Need help with installing binary"
date: 2005-07-24
forum: Absolute Beginner Talk
---

### Post by KrisDwyer on 2005-07-24
```
kris@dwyernpayne:~/Desktop$ sudo dpkg -i xmms_1.2.10+cvs20050209-2_i386.deb
Selecting previously deselected package xmms.
(Reading database ... 58180 files and directories currently installed.)
Unpacking xmms (from xmms_1.2.10+cvs20050209-2_i386.deb) ...
dpkg: dependency problems prevent configuration of xmms:
 xmms depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 xmms depends on libgtk1.2 (>= 1.2.10-4); however:
  Package libgtk1.2 is not installed.
dpkg: error processing xmms (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
xmms

```

Help! what is libglib1.2? i know what gtk is...

---

### Post by poofyhairguy on 2005-07-24
Why are you installing xmms that way? Is it a special version?

[http://packages.ubuntu.com/hoary/libs/libglib1.2](http://packages.ubuntu.com/hoary/libs/libglib1.2)

There is the package you need. Please install it using synaptic...install xmms the same way if you can....

[https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29](https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29)

---

### Post by KrisDwyer on 2005-07-24
[QUOTE=poofyhairguy]Why are you installing xmms that way? Is it a special version?

[http://packages.ubuntu.com/hoary/libs/libglib1.2](http://packages.ubuntu.com/hoary/libs/libglib1.2)

There is the package you need. Please install it using synaptic...install xmms the same way if you can....

[https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29](https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29)[/QUOTE]
 what 'about that gtk one, can you link me to that also?

---

### Post by poofyhairguy on 2005-07-24
[QUOTE=KrisDwyer]what 'about that gtk one, can you link me to that also?[/QUOTE]

Ya:

[http://packages.ubuntu.com/hoary/libs/libgtk1.2](http://packages.ubuntu.com/hoary/libs/libgtk1.2)

But that one has a lot of dependencies so it will be harder to install by hand.

---

