---
title: "Mouse Probs"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by sphinxcs898 on 2006-03-30
My pointer is stationary.. What do I do? I have to access the applications thru keyboard..

---

### Post by sn123 on 2006-03-30
welcome to the forums, please provide more information abt your system configuration and the problem. 
a) Do you have a laptop or a desktop?
b) Was the mouse never working or it stopped working recently.
c) If yes to stopped working recently, any recent changes to system configuration or kernel upgrades?

Also, open a command terminal and copy the output of the following commands:
```

$ cat /proc/bus/input/device

```
if the above command doesn't run replace "device" with "devices" (sorry I am not on Ubuntu currently so cannot check myself which one is correct).

Output of last 60 lines from X's log file```

$ tail -60 /var/log/Xorg.0.log

```
and finally, the xorg.conf file
```

$ cat /etc/X11/xorg.conf

```

Hopefully, somebody should be able to help you out based on the above information.

Good luck,
S

---

