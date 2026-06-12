---
title: "[SOLVED] wine not working"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by axemurder785 on 2007-08-21
i installed wine and the wine-dev packages, but when i double click on an exe file it still says 

"Cannot open /media/cdrom0/LAUNCHER/installer.exe: No application suitable for automatic installation is available for handling this kind of file." please help!

---

### Post by Vadi on 2007-08-21
I don't know why, but it won't open .exe via wine by default.

What you want to do instead is click Applications - Accessories - Wine File. Then browse for that .exe file, and open it.

---

### Post by TeaSwigger on 2007-08-21
Try opening a terminal and type:

```
wine /media/cdrom0/LAUNCHER/installer.exe
```

---

### Post by axemurder785 on 2007-08-21
it dosen't say wine file under accessories. :(

---

### Post by wormser on 2007-08-21
If the problem is not opening by default then right click on the .exe go to properties then the open with tab.

---

### Post by axemurder785 on 2007-08-21
> **TeaSwigger said:**
> Try opening a terminal and type:

```
wine /media/cdrom0/LAUNCHER/installer.exe
```

ok that made wine work but is there a way to make it the default exe launcher??? :confused:

---

### Post by cookies on 2007-08-21
> **axemurder785 said:**
> ok that made wine work but is there a way to make it the default exe launcher??? :confused:

[[img]http://img381.imageshack.us/img381/8066/gray12uj0.th.png[/img]](http://img381.imageshack.us/my.php?image=gray12uj0.png)

If wine isn't there click Add, click custom command and type wine.

---

### Post by axemurder785 on 2007-08-21
> **wormser said:**
> If the problem is not opening by default then right click on the .exe go to properties then the open with tab.

ok, it isn't under the open with tab. can i type 

"wine"

in the "open with - use a custom command" thing?

---

### Post by axemurder785 on 2007-08-21
> **cookies said:**
> [[img]http://img381.imageshack.us/img381/8066/gray12uj0.th.png[/img]](http://img381.imageshack.us/my.php?image=gray12uj0.png)

If wine isn't there click Add, click custom command and type wine.

ok that works!

---

### Post by Vadi on 2007-08-22
If the problem is solved then, please click 'Thread Tools' on top and select 'Mark thread as solved'.

---

