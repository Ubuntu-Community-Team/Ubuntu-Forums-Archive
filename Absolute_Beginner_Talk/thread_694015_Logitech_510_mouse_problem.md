---
title: "Logitech 510 mouse problem"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by Joor on 2008-02-11
I cant get my forward and back buttons to work in firefox..very annoying . What can I do ?

---

### Post by LowSky on 2008-02-11
here is how to get all the buttons working on your mouse

in terminal type 

```
sudo gedit /etc/X11/xorg.conf
``` make sure X11 is capital X

then edit the mouse portion to this

```
Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "false"
Option "Buttons" "7"
Option "ButtonMapping" "1 2 3 6 7"
EndSection
```

---

### Post by Joor on 2008-02-11
that didnt do anything

---

### Post by jusmai77 on 2008-02-11
I have a similar problem, I have a Logitech LX7, my back button opens a link in a new tab, my forward button does the same thing as my right click button.  not too major of an issue but does anybody know how to change it to make those buttons navigate forward and backwards in the firefox browser?

---

### Post by Cew27 on 2008-02-11
it is possible follow the above steps and then search the forums for mouse setup and you will find more help

---

### Post by Joor on 2008-02-11
Do I have to reboot ubuntu before it work ?

---

### Post by Cew27 on 2008-02-11
oh yeh and download im wheel and set it to startup its in the repositories

---

### Post by Joor on 2008-02-11
> **LowSky said:**
> here is how to get all the buttons working on your mouse

in terminal type 

```
sudo gedit /etc/X11/xorg.conf
``` make sure X11 is capital X

then edit the mouse portion to this

```
Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "false"
Option "Buttons" "7"
Option "ButtonMapping" "1 2 3 6 7"
EndSection
```

This works after I reboot the PC !
Thanks alot :)

---

### Post by jw5801 on 2008-02-11
All it needs is a log out and log back in again, this restarts X (the graphical environment) so that it can read it's new configuration file!

---

### Post by jusmai77 on 2008-02-15
after reboot now it works for me too

---

