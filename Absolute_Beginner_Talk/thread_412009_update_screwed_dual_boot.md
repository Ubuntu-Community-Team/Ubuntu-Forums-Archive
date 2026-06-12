---
title: "update screwed dual boot"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by Shabutie on 2007-04-17
so i updated last night, it said it needed to restart for something, but it was late so i just turned it off... today when i go to turn it on, theres no windows option in grub, just two ubuntu options.  i go into menu.lst and sure enough somehow the xp entry got deleted and ubuntu replicated itself... also, somehow my su password got reset or something because its not working now either so i don't know where to begin... please help!

---

### Post by Cypher on 2007-04-17
I also recently updated my system to the latest Kernel which required a reset but my XP dual-boot option did not disappear. Anyway, you can easily add the XP boot option back by modifying the menu.list file and entering the following info:

```
title Windows XP
	rootnoverify (**hd0,0**)
	chainloader +1
```

You would want to change the hd0,0 to point to the right HD and partition on which you have XP installed.

Secondly, as far as SU goes, since you can login, why not just do a "sudo su" and get root access?

Regards

---

### Post by Razorback on 2007-04-17
Same thing happend to me:

[http://ubuntuforums.org/showthread.php?p=2454894#post2454894](http://ubuntuforums.org/showthread.php?p=2454894#post2454894)

except I changed:

title Microsoft Windows XP Home Edition
root (hd1,0)
makeactive
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

---

