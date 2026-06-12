---
title: "Using &quot;sudo halt&quot; instead of shutdown?"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by Romanus81 on 2007-08-26
When I shutdown the normal way, through the button on the top right of my screen, it shuts down to a point and then says "Will Now Halt" but does nothing. I tried once typing "Sudo halt" into terminal and it shutdown completely. Is there any risk involved with my system shutting down this way?

---

### Post by Majorix on 2007-08-26
Does
```
sudo shutdown now
```
work too? If yes, use that instead.

---

### Post by Romanus81 on 2007-08-26
No, all it does is say something like "RC1 jobs sent TERM signal"
And then a command prompt (root@ubuntu:)

---

### Post by kevdog on 2007-08-26
What about
sudo shutdown -r now
??

---

### Post by aldenhg on 2007-08-26
Whenever i need to shutdown from the command line I use sudo shutdown -h now, replacing the h with an r if I want to restart.

---

### Post by Nikron on 2007-08-27
sudo poweroff

---

