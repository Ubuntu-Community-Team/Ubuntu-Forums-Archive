---
title: "System failed to start the X server..."
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by dorogavtsev on 2007-08-29
System failed to start the X server (graphical interface).

I cannot remember exactly what did I change... how can I start automatic reconfiguration to the initial conditions.

---

### Post by w4ett on 2007-08-29
From the command line type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select "vesa" as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:

```
startx
```

This will get you to a GUI desktop.

---

### Post by dorogavtsev on 2007-08-29
tnxs, mate :-)

---

