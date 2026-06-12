---
title: "Booting Help"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by reviveL on 2008-03-30
I was updating my Ubuntu (200 updates) over night and this morning I came down to check it out and I find my computer completely frozen on a black screen. 

I turn the computer off manually and attempt to boot in to Ubuntu through GRUB. All I find is that Ubuntu is stuck on:

> Starting up ...
-

I've waited about 10 mins for it to load, but I just end up turning off my computer and booting it in Windows.

---

### Post by lswest on 2008-03-30
what happens if you boot to the failsafe boot (second entry of GRUB), does it boot?

---

### Post by reviveL on 2008-03-31
Theres just a long list of words and it also doesn't boot. I tried running a command line on the kernel replacing quiet splash with 

> noacpi nolapic nodma all_generic_ide

This line only worked once, which was the first time i tried it. Every other time I tried running this command it just gets stuck on some part about configuring some PCI thing.

---

### Post by dstew on 2008-03-31
If you get to the grub menu, can you boot an older kernel? And, are you sure that recovery mode doen't boot? It won't get you a graphical interface, just a command line. Do you get a command line with the recovery boot? If so, the system is running, you might need only to reconfigure it.

---

### Post by reviveL on 2008-03-31
Yes there is a command line in recovery mode.

---

### Post by dstew on 2008-03-31
What happens if, on the recovery mode command line, you enter```
startx
```

---

### Post by reviveL on 2008-04-01
I fixed the problem. I found out the problem was GRUB so I tried reinstalling it with the live CD and it works again. It appears that this boot problem only happens if the computer is manually turned off.

---

