---
title: "additional modprobes"
date: 2005-11-11
forum: Absolute Beginner Talk
---

### Post by barcode on 2005-11-11
What is the correct ubuntu method of adding additional modprobes? I need to add the following sometime during boot as some kernel modules don't seem to be being loaded at the moment. Here is what I would do manually:


modprobe bttv i2c_hw=1 card=0x68
modprobe dvb-bt8xx
modprobe nxt6000

---

### Post by tonym on 2005-11-11
Install the modconf package from universe then "sudo modconf".

---

### Post by Lambert on 2005-11-11
You can open this file

```
sudo gedit /etc/modules
```

and add each module you want to load at boot.

---

