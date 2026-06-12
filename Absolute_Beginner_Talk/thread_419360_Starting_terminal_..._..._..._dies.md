---
title: "Starting terminal ... ... ... dies"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by xplodersuv on 2007-04-22
I just started using Ubuntu (pretty new to Linux in general) and when I try to start a terminal it doesn't work.  An item in the taskbar shows up saying "Starting Terminal" for about 10 seconds and then it disapears, but no terminal shows up.  

So 2 questions:

1.  Where should I be looking for an error message?
2.  How do I do a restore?  I noticed this happened after I enabled dual monitors, but I can't disable them without opening a term!  (I used nvidia's gui)

---

### Post by Ziox on 2007-04-22
use the simple terminal : xterm

hit alt+f2 and enter xterm

then you can start gnome-terminal and see the error messages

---

### Post by lamalex on 2007-04-22
are you able to go into a real terminal? not an xterm? (control + alt + f1) also try editing your hosts file (/etc/hosts) and to the first line 127.0.0.1 localhost add your host name so it's like 
127.0.0.1 localhost <hostname>
127.0.1.1 <hostname>
this speeds things up sometimes and might fix your problem on its own.

---

