---
title: "[SOLVED] 1 thing preventing me from removing windows forever"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by nothingspecial on 2008-02-07
I have a sony vaio PCG-8Y3M laptop with ubuntu/vista dual boot. The only thing stopping me removing windows all together is that I can't open the cd/dvd drive in ubuntu, ie the eject button dosen't work.
 If I want to play a cd ,dvd ect.... I have to restart, boot windows, press eject,  insert the cd, restart and boot ubuntu.
 Anyone got any ideas. Thank you in advance.

---

### Post by PeterJS on 2008-02-07
Does soft ejecting work?

Open a terminal and run:
```

eject /dev/cdrom

```

---

### Post by nothingspecial on 2008-02-07
Goodbye windows !

---

### Post by spiderbatdad on 2008-02-07
```

eject /dev/cdrom
``` save that in a text file called ejector
```
chmod a+x ejector
```

then right click on desktop and create a custom launcher for your panel...bingo an eject button.

---

### Post by nothingspecial on 2008-02-07
No such file or directory????????

---

### Post by spiderbatdad on 2008-02-07
artificial intelligence is no match for genuine stuipdity

---

### Post by nothingspecial on 2008-02-07
Don`t know, sorry

---

