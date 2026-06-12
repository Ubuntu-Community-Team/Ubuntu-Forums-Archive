---
title: "13-feb linux headers update turn my laptop in chaos!"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by Dbugger on 2008-02-12
What happened?? I just updated the latest linux-headers today (13-feb) and after the grub, the screen turns green and then i can get to the desktop but i get no sound!

Help!

---

### Post by spiderbatdad on 2008-02-13
Try this: ```
asoundconf list
```

the result should be something like:
[B] Names of available sound cards:
I82801CAICH3[/B]

Then run  ```
asoundconf set-default-card Result
```  where Result is the result from the first command.
In my case: ```
asoundconf set-default-card I82801CAICH3
```


Then reboot.

---

