---
title: "find processor usage?"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by RyanZec on 2008-03-01
On window you can find out the percentage of the processor being used and what application are using by going to the task manager, does a simliar feature exist on unbuntu 7.10?

---

### Post by jan quark on 2008-03-01
```
top
```
in terminal

---

### Post by ./. on 2008-03-01
System > Administration > System Monitor.

This performs a similar function to Windows Task Manager.

---

### Post by drubin on 2008-03-01
```
sudo ps -ef
```

Gives you a list of the running processes

---

### Post by herbster on 2008-03-01
You can also use htop, which is a more advanced version of top as mentioned above. Probably can be installed by doing

```
sudo apt-get install htop
```

Then running htop. If you like GUI, use gnome-system-monitor.

---

