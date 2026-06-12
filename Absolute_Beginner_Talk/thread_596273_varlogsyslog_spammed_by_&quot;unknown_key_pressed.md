---
title: "var/log/syslog spammed by &quot;unknown key pressed"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by Sim777 on 2007-10-29
I'm getting spammed by following message

```
Oct 29 10:59:57 sim-laptop kernel: [ 2084.302456] atkbd.c: Use 'setkeycodes e00d <keycode>' to make it known.
Oct 29 11:00:30 sim-laptop kernel: [ 2110.844754] atkbd.c: Unknown key released (translated set 2, code 0x8d on isa0060/serio0).

```
I search other threads, but they show different key...can anyone assist me what's causing it and how to fix/stop it?
[http://ubuntuforums.org/showthread.php?p=669419&posted=1#post669419](http://ubuntuforums.org/showthread.php?p=669419&posted=1#post669419)
[http://ubuntuforums.org/showthread.php?t=117482](http://ubuntuforums.org/showthread.php?t=117482)

---

### Post by philinux on 2007-10-29
Odd stuff - check this out

[http://www.linux-on-laptops.com/forum/showthread.php?t=3326](http://www.linux-on-laptops.com/forum/showthread.php?t=3326)

---

### Post by Sim777 on 2007-10-29
Bah, I should've searched on google too. Looks like he uses same laptop as I. 

But it give me more questions. What is "e00d" key? 

Suggestions in that thread tell to disable key by "setkeycodes e00d 0" or reconfig keyboard.

How can I reconfigure keyboard? I don't see that option in GUI

---

### Post by philinux on 2007-10-29
Sounds like more googling then :lolflag:

---

### Post by Sim777 on 2007-10-29
> **philinux said:**
> Sounds like more googling then :lolflag:

Har har har ;)


dpkg-reconfigure console-setup

I'll be back...

---

### Post by Sim777 on 2007-10-29
And now I can't boot, console or regular,.. sigh....:(

---

### Post by Sim777 on 2007-10-29
so...google is not helping here


If I boot to recovery, I get constant spam with same message as in my first post. If I go into regular, it gives me following (copied by pen...)

```

check root = bootarg cat /proc/cmdline or missing modules, devices: cat /proc/modules ls /dev
ALERT /dev/disk/by -uuid/72a550ld-cd34-46ef-a263-dfb1d40a39-6f does not exist
Dropping to a shell! 





```

weak....

---

### Post by Sim777 on 2007-10-29
I really don't get it. All of my searches come without any success. ......am I the only one that faced this problem ....ever. ......I would like to keep my existed ubuntu that took me a long time to 'get it going as I want it'

---

