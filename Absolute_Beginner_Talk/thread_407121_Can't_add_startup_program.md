---
title: "Can't add startup program"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by dr.silly on 2007-04-11
I want checkgmail to start. I go to sessions startup and add the command 'checkgmail' I know this is it because i tried entering it in the command line. When I reboot it doesn't start and it disappears from the startup programs

---

### Post by pirothezero on 2007-04-11
type this in terminal 

sudo chown yourusername /home/yourusername/.config/autostart/

[http://ubuntuforums.org/showthread.php?p=2439172#post2439172](http://ubuntuforums.org/showthread.php?p=2439172#post2439172)

---

### Post by Jeremiah478 on 2007-04-16
Thanks, I was having the same problem with AWN.

---

