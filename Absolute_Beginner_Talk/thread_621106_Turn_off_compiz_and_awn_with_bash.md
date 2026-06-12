---
title: "Turn off compiz and awn with bash"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by helino on 2007-11-23
Hi, 

when I play games and use some programs I have to turn off compiz (and thereby AWN) for compabality issues. Could someone help me with a bash script that does two things:

1. Turns off compiz and AWN before the application is launched (I know how to launch the application myself)

2. Turns on compiz and AWN after the application is closed

I guess that number 2 is the hard part, but only number 1 would be great if someone could help me with.

Thanks for a great community, nice weekend to you all!

---

### Post by hyper_ch on 2007-11-23
Do you know what commands to use to turn on/off Compiz?

---

### Post by helino on 2007-11-23
Google is my friend :)

I have to run this to turn it off, and run it to turn it on. It's almost what I wanted, close enough:

```
#!/bin/bash
#toggle between compiz and metacity

if ps ax | grep -v grep | grep -v defunct | grep "compiz.real"> /dev/null
then
killall avant-window-navigator;
killall compiz.real;
metacity --replace &
else
compiz --replace &
avant-window-navigator &

fi

```

I added a nice button to my toolbar that works perfect

---

