---
title: "terminal window went blank"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by tehmanwhos0ldtheworld on 2007-11-20
hello guys im new in ubuntu

after a few hours of use my terminal window went blank

heres a screenshot

[http://img516.imageshack.us/img516/8121/screenshotta6.png](http://img516.imageshack.us/img516/8121/screenshotta6.png)

thanx in advance

---

### Post by Dr Small on 2007-11-20
> **tehmanwhos0ldtheworld said:**
> hello guys im new in ubuntu

after a few hours of use my terminal window went blank

heres a screenshot

[http://img516.imageshack.us/img516/8121/screenshotta6.png](http://img516.imageshack.us/img516/8121/screenshotta6.png)

thanx in advance
Have you tried restarting the system or X ?

---

### Post by tehmanwhos0ldtheworld on 2007-11-20
yes,didnt help:(

---

### Post by tehmanwhos0ldtheworld on 2007-11-20
anyone plz?

---

### Post by tehmanwhos0ldtheworld on 2007-11-21
sorry for the bump but i need help

---

### Post by Paul820 on 2007-11-21
Do you have desktop effects enabled?

---

### Post by dwhitney67 on 2007-11-21
It looks as if the terminal application hung, and thus would not refresh.

I discovered today how to create an undesirable delay in launching gnome-terminals... while troubleshooting a network issue, I commented out this line out within the */etc/hosts* file:

```
127.0.1.1       myHostName.hsd1.wa.comcast.net.    myHostName
```

Bad mistake!  After I commented out that line, Gnome took almost a minute to launch a terminal.  If I commented it back in, within a few moments, the multiple terminals that I requested earlier would all start popping up.  Apparently Gnome, which I believe depends on an ORB (Object Request Broker), is sensitive to the localhost's networking environment.  Anyhow, I learned a little something today.  :-)

---

### Post by tehmanwhos0ldtheworld on 2007-11-21
thanx guys i just solve the problem by reinstalling the nvidia driver :)

---

