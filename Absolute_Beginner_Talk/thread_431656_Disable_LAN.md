---
title: "Disable LAN"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by Dog walker on 2007-05-03
Hi,

Quick question... can anyone tell me if it is possible to disable a network connection in Ubuntu?

Something I always used under XP was the single mouse click to either enable or disable my LAN connection to my wireless modem/router. I'm always paranoid, but I liked this as added security when I'm away from the PC.

Can I do anything similar (preferably quick (1 or 2 clicks)) from Ubuntu?

Many thanks,
Ken.

---

### Post by dergringo on 2007-05-03
Find the Network icon in your panel and RIGHT click it. Disable "Enable Networking".

[IMG]http://img19.imageshack.us/my.php?image=abcoa3.png[/IMG]

greetings

Philipp

---

### Post by sc30317 on 2007-05-03
Type "sudo ifdown eth0" for wired or type "sudo ifdown eth1" for wireless to take down your network card.  To get it back going again, simply type "sudo ifup eth0" for wired and "sudo ifup eth1" for wireless.

---

### Post by Bachstelze on 2007-05-03
How do you know his interface is eth0 or eth1 ?

---

