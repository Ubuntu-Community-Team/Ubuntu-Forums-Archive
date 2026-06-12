---
title: "xterm - can't open display"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by sgargabonzi on 2007-05-03
Hi all, 

I can't figure out why I receive an error when running the command xterm. I have tried seting the env variable DISPLAY to many values like for example 127.0.0.1:0.0   or 127.0.1.1:0.0  or localhost:0.0 etc etc. 

Infact I am working on my local laptop and I checked already the file /etc/hosts . 

The error is ```
xterm Xt error: Can't open display: 127.0.0.1:0
``` or whatever the value of the DISPLAY variable is. 

What is the issue?

Sgarga

---

### Post by sgargabonzi on 2007-05-03
forgot to say that I exported the variable DISPLAY :
```
 DISPLAY=127.0.0.1:0.0; export DISPLAY  
```

and checked if it is showing when running the command env  ... and it is there. But still having the issue.

---

### Post by sgargabonzi on 2007-05-03
anyone has a guess what the issue might be?

---

