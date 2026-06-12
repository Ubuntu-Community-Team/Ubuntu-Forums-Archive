---
title: "Question about xnest"
date: 2006-02-22
forum: Art &amp; Design
---

### Post by blueshome on 2006-02-22
I've to test a gdm theme so I use xnest
typing the following....
gdmflexiserver --xnest

How I can set a different screen resolution (like 800x600)

I've try with
gdmflexiserver --xnest -geometry 800x600
but seems the same

Someone can help me :-D

---

### Post by roshan.s on 2006-02-22
You can modify /etc/gdm/gdm.conf. Add the option -geometry W+H+X+Y to the line starting with Xnest=...

Note that you use the '+' character, not the 'x' character to separate the values. Also, you can leave out the X+Y and use only width and height.

Before:
```
Xnest=/usr/X11R6/bin/Xnest -br -audit 0 -name Xnest
```

After:
```
Xnest=/usr/X11R6/bin/Xnest -br -audit 0 -name Xnest -geometry 800+600
```

Also, if you're using Dapper, you shouldn't edit the /etc/gdm/gdm.conf file. You need to copy any lines you want to edit to the same section in /etc/gdm/gdm.conf-custom and change them there. This won't work pre-Dapper.

---

### Post by blueshome on 2006-02-24
Thanks roshan for the help

---

