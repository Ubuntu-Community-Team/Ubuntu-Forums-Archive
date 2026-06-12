---
title: "Swap partition keeps getting corrupted. Ubuntu crashing frequently."
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by Charco on 2007-03-01
Yesterday I asked how to activate my swap:
[http://www.ubuntuforums.org/showthread.php?t=371522](http://www.ubuntuforums.org/showthread.php?t=371522)

It turns out that every time I activate it, it gets corrupted after about 2 reboots.

[[IMG]http://img80.imageshack.us/img80/4527/screenshotdevhdbgpartedmx9.th.png[/IMG]](http://img80.imageshack.us/my.php?image=screenshotdevhdbgpartedmx9.png)

Is this a hardware problem? What do you think? Please help!

---

### Post by STREETURCHINE on 2007-03-01
I think you need to create an extended partition around your swap.that should stablize it

---

### Post by Charco on 2007-03-01
Thanks for the reply! But I'm sorry, I'm not sure what that means could you elaborate please?

---

### Post by STREETURCHINE on 2007-03-01
sorry it took so long to get back having power failures here,

just ignore my previous post it seems that it is wrong. lol
it must have sorted it self ou when i repartitioned again so cant help you there 

i googled your problem did not find a cure just enough to know my assumption was wrong

---

### Post by bodhi.zazen on 2007-03-01
format the partition as swap

Under gparted, umount /dev/hdb3

Format it as "linux-swap"

Then, again in gparted, right ckick on the swap partition and choose swapon

8)

---

