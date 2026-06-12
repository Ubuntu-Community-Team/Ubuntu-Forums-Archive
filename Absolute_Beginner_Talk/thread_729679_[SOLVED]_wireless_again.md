---
title: "[SOLVED] wireless again???"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by kamitsukai on 2008-03-20
Ok i've had a post which solved this problem..([http://ubuntuforums.org/showthread.php?t=728870](http://ubuntuforums.org/showthread.php?t=728870)) and i got a solution but it appears to only be tempoary as when i restart i have to do it again so is there anyway to make these commands stick?

```
You need after installing ndiswrapper have to done the following commands in a terminal

sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m

See ndiswrapper when you do?

lsmod

to edit the file

sudo gedit /etc/modules

Think it is kate not gedit in kubuntu
```

---

### Post by kamitsukai on 2008-03-20
and what doi have to edit in the file?

---

### Post by adult swim on 2008-03-20
add
```
ndiswrapper
```
to the end of the file and save it

---

