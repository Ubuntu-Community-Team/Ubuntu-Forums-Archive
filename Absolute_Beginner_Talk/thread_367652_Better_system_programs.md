---
title: "Better system programs?"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by bronevaya on 2007-02-22
hi, I just installed ubuntu and I am not happy with the system programs that came with it. For instance the network manager is horrible. It wont show my wireless card until it connects to something automaticlly, I cant pick what network to join, when it does connect it wont show the network/wireless point name


also, is there anything I can use to adjust the voltage on my laptop? (like rm clock)

---

### Post by nickoli_02 on 2007-02-22
To see your wireless card:

```
lspci | grep Network
```

A network manager for gnome:

```
sudo aptitude install gnome-network-manager
```

Ubuntu comes installed with a daemon called powernowd, which should automatically adjust CPU frequency and voltage to reduce power usage (if your CPU supports frequency and voltage throttling). There are several frequency governors for you to choose from, such as performance, ondemand, conservative, and some others. Try searching the forums or google for powernowd for information on how to set a specific governor.

---

