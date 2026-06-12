---
title: "Ubuntu /proc/cpuinfo mishap"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by tom12519 on 2006-07-10
These two commands were issued almost immediately after each other, and the same happens every time (first time it reports the correct spped, then it reports the false one from thereon until a new terminal is starter).
[[IMG]http://img442.imageshack.us/img442/5809/screenshot39qa.th.png[/IMG]](http://img442.imageshack.us/img442/5809/screenshot39qa.png)

---

### Post by Jason_25 on 2006-07-10
Try

```

sudo /etc/init.d/powernowd stop

```

and run the command again.  If the CPU is still throttling, check your bios.

---

### Post by tom12519 on 2006-07-11
That worked perfectly thanks, but what does that do?

---

### Post by scxtt on 2006-07-11
you can do a **man powernowd** to read a bit about it ... seems to me that your processor only operates at full speed when needed (instead of full power all the time) ... this generally is used to keep laptops cooler ...

nice "SHIT" folder, btw ... ;)

---

### Post by tom12519 on 2006-07-11
Why, thank you, so it's sort of like cool'n'quiet... It's just that if I wanted to overclock I'd want to know what speed it was going at...

---

