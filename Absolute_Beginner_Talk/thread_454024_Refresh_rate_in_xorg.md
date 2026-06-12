---
title: "Refresh rate in xorg?"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by ithuwakaga on 2007-05-25
Can someone tell me how to modify the refresh rate in the /etc/X11/xorg.conf file?  I'd appreciate it.

A bonus to someone who could also give me a run down on how to work the xorg file itself.

---

### Post by DerArzt on 2007-05-25
Im not sure what you mean by work the xorg, so my guess is how to edit it? 

just go to a terminal and type 
```
sudo gedit /etc/X11/xorg.conf 

```

its just a long text file

find the section "Monitor" there should be something called i think VertRefresh. that should be ur refresh rate.

---

### Post by Smu on 2007-05-25
Try this:

1. Ctrl + Alt + F1
[I]This will open upp a non-graphical session. To get back to the gnome-desktop and your current session -> Ctrl + Alt + F7
[/I]
2. Login
3. sudo dpkg-reconfigure xserver-xorg
4. fill in the information of your monitor
5. Ctrl + Alt + F7
6. Ctrl + Alt + Backspace (restart x) 


Worked for me when I had problems with my monitor...

---

