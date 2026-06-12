---
title: "How do I find out what Microproccesor I have?"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by EleFlameMax on 2008-02-07
Pretty self explanatory. Is there like a terminal command I have to use?

---

### Post by bitterbug on 2008-02-07
```
dmesg | grep CPU
```

---

### Post by kpkeerthi on 2008-02-07
Also...
```
cat /proc/cpuinfo
```

---

### Post by yaknowwat on 2008-02-07
First tab of the System monitor

System > Administration > System Monitor

or pop open the terminal and put in
```
gnome-system-monitor
```

to start it if you can't find it.

Otherwise you can use the commands above.

---

### Post by Rocket2DMn on 2008-02-07
Or even another alternative, 
```
sudo lshw -class processor
```

---

### Post by maniac_X on 2008-02-07
I can confirm all the above methods work as I have just done them all for kicks :lolflag:

I like Rocket2DMn's method best though because it told me I might have a little room to try some overclocking on my cpu :)

---

