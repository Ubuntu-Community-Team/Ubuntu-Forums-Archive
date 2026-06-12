---
title: "amount of ram etc"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by firefly123 on 2006-03-13
Hi
Is there any way of displaying your computer info  ie. ram,:)  processor etc

---

### Post by kaamos on 2006-03-13
Applications->Accessories->Terminal

lspci
cat /proc/cpuinfo
cat /proc/meminfo
sudo lshw

That sould get you started. :)

---

### Post by aysiu on 2006-03-13
If you're using Gnome, try Alt-F2 and ```
gnome-system-monitor
```

Otherwise, you can try Applications > Accessories > Terminal ```
top
```

---

### Post by jjf on 2006-03-13
If you want to constantly monitor those things, install gdesklets with Synaptic.  It allows you to place little "widgets" on your desktop that monitor that sort of stuff.  I use gdesklets to monitor HD space, RAM usage, and wifi connection.  Since I like having the system monitor handy, I added it to my gnome-applets.  R-click on the top bar and click "Add to Panel," find System Monitor.  It has a cool little icon that tracks processor usage.

---

### Post by Brunellus on 2006-03-13
there's also gkrellm which is available out of the universe repositories

---

### Post by firefly123 on 2006-03-13
[QUOTE=Brunellus]there's also gkrellm which is available out of the universe repositories[/QUOTE]
cheers all, thank you:-D :-D :-D :-D \\:D/ :-({|=

---

