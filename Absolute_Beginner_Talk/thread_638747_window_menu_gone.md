---
title: "window menu gone"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by mD3m4r415 on 2007-12-12
hello,
in another post i asked how to remove the [_] [O] [X] from the top of windows... i have now done it accidentally not even meaning to, and i do not know how to reverse it!!! i have no windows borders at all... please help!
thank you

---

### Post by Valok on 2007-12-12
The person in this thread is was having similar problems.  You should be able to find the solution to your problem in there.

This will help if you use Compiz Fusion, if you don't then we can search for other topics with other solutions

---

### Post by aktiwers on 2007-12-12
Will this command fix it?
```
compiz --replace
```?

If so, remember to add it to startup if it resets after reboot.
System > Prefs > Sessions, there add "compiz --replace" as a new item.

---

### Post by billgoldberg on 2007-12-12
If you can't find how to do it, you could always use emerald for the windows borders.

just letting you know.

---

### Post by flamelab on 2007-12-12
Try (before installing emerald ) 

```
metacity --replace
```

Emerald wants a similar instruction

```
emerald --replace
```

---

### Post by mikecomua on 2007-12-12
```
gconf-editor
``` Now navigate to: apps>metacity>general. On the right double click 'button_layout'Delete that & type > 'menu:minimize,maximize,close'

---

### Post by philinux on 2007-12-12
[http://ubuntuforums.org/showthread.php?t=633322](http://ubuntuforums.org/showthread.php?t=633322)

---

### Post by locky28 on 2008-02-22
> **flamelab said:**
> Try (before installing emerald ) 

```
metacity --replace
```


Cheers man, I lost my close min and max buttons playing with emerald and then list the title bar altogether! This command put everyting back to normal :)

---

