---
title: "Configuring Optical Mouse(Serial to PS2)"
date: 2005-12-09
forum: Absolute Beginner Talk
---

### Post by arunmvishnu on 2005-12-09
Hi,
   Now I am using Logitech(Ball) serial mouse. I changed my mouse configuration by editing /etc/X11/xorg.conf file 
[INDENT](For those who are a little bit more experienced with the command line (I was a bit annoyed to have to run through the whole setup and mess all my hand-written config), you can just change this manually into the /etc/X11/xorg.conf file (with nano, vi, or whatever you please), by simply changing Option Device "whateverwastherebefore" to Option Device "/dev/ttyS0" ).[/INDENT]
 But now i planed to buy a Logitech Optical Scroll Mouse(PS2). So what are the changes i needed in the /etc/X11/xorg.conf file.

---

### Post by Joe_CoT on 2005-12-09
in the xorg.conf file, change the protocol for the mouse to this:
```
Option	    "Protocol" "ExplorerPS/2"
```

change the device to this:
```
Option	    "Device" "/dev/mice"
```

add these options:
```
Option	    "ZAxisMapping" "4 5"
Option	    "Emulate3Buttons" "yes"
```

---

