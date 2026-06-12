---
title: "Macbook Pro monitor does not dim"
date: 2021-02-25
forum: Apple Hardware Users
---

### Post by garnold on 2021-02-25
I've just installed 20.04 on my MacBook Pro. Currently the display will not dim at all. I have found only one way to fix this and that is by using what I learned in this post

[https://bbs.archlinux.org/viewtopic.php?id=232317](https://bbs.archlinux.org/viewtopic.php?id=232317)

If I use the solution of typing the following into the terminal I can dim the display

```
sudo setpci -v -H1 -s 00:01.00 BRIDGE_CONTROL=0
```

Once I reboot the system this fix no longer works. Do I need to add this to some start up script? I'm quite new to Ubuntu and just starting to figure things out. Thank you!

---

### Post by QIII on 2021-02-25
Moved to Apple Hardware Users as a more appropriate sub-forum.

---

### Post by garnold on 2021-02-27
Understood. Anyone have some tips for me please?

---

