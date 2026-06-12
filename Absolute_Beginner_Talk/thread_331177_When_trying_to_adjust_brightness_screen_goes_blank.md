---
title: "When trying to adjust brightness screen goes blank..."
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by encompass on 2007-01-04
When I try to adjust the screen brightness while in X the screen goes blank... the backlight is still on.  But the screen goes blank.  This happens while in beryl or not.
It is the intel 845 chipset on an asus a7f.  Edgy.
I can however restart X but end up losing the proper resolution.  It looses my widescreen feature because it down run the resolution915 program until I reboot.  Bummer huh?
It may be related but when I try to log out some times, it will will go black in the same way.
I can also adjust the brightness in powermanager with no blanking... the screen dimms properly.
Weird huh?

---

### Post by mykalreborn on 2007-01-04
yep pretty weird. you say you have an intel chipset? are you sure it's not an ATI or nVidia? these usually are buggy

---

### Post by encompass on 2007-01-04
hehe yeah,
here: to confirm...
```
encompass@essence:~$ lspci | grep Graph
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
encompass@essence:~$ 

```

---

### Post by mykalreborn on 2007-01-04
well i belive you.
but i'm afraid i can't help you :p

---

### Post by encompass on 2007-02-04
Bumbers....

---

### Post by mykalreborn on 2007-02-04
still haven't fixed it?
maybe it's your monitor. do you have an lcd? those things sometimes have problems. 
i'm not sure, but it's worth checking out. ;)

---

### Post by encompass on 2007-02-04
Weird enough... but it happened AFTER upgrading my bios.

---

