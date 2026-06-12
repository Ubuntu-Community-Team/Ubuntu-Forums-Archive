---
title: "lost wlan0 again..."
date: 2006-03-14
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2006-03-14
:confused: 
I am not sure why I get these results:
```
john@laptop:~$ sudo ndiswrapper -l
Password:
Installed ndis drivers:
bcmwl5  driver present, hardware present
john@laptop:~$ sudo modprobe ndiswrapper/bcmwl5
FATAL: Module ndiswrapper/bcmwl5 not found.

```

It seems that my understanding of how these relate isn't clicking...

OK , all I did was ```
 sudo modprobe ndiswrapper 
```
and it's back... (but it immediately kills my eth0 connection, even though wlan doesn't work...) This may be because they are both marked 'active'?!?

I lost my wlan0 in network configuration utility, and don't understand why. I am backtracking towhere I lost it, and am going to see if my 'notes' work for me...

---

### Post by Papa-san on 2006-03-14
In 'network' I de-activated the eth0, rebooted, and it came up with both active, but neither functional... OOps, I didnt' change the default... brb

---

