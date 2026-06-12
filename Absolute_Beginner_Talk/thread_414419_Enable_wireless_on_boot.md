---
title: "Enable wireless on boot"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by ocho on 2007-04-19
I am having some problems enabling my wireless card automatically during the boot of Ubuntu Feisty. Every time I boot, I must run the commands 
sudo depmod -a
sudo modprobe ndiswrapper
manually in order to enable wireless networking.

Is there a way to put these commands into a startup script to enable wireless automatically? Thanks in advance.

---

### Post by bobplano on 2007-04-19
run this 
```
sudo ndiswrapper -m
```

it will tell the computer to start ndiswrapper when the computer boots

---

### Post by ocho on 2007-04-19
When I run that command, it outputs "module configuration already contains alias directive." I rebooted and I once again had to run the aforementioned commands in order to get my wireless working.

I suppose it isn't a big problem, just a bit of a hassle. Any other suggestions?

---

