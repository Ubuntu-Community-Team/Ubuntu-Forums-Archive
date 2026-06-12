---
title: "My computer won't show Ubuntu graphically"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Stuki on 2007-06-13
Topic says it all... 
It starts Ubuntu 7.04 just fine but when you are supposed to login then a error message comes up an reports that it won't show the graphic display.

System Specs.

Intel Pentium III 833 MHz
512 MB RAM
Some Intel graphics controller (integrated)

---

### Post by Inxsible on 2007-06-13
What is the exact error (if any) that you get?
 
Did you install the server edition as opposed to the Desktop Edition?

---

### Post by Stuki on 2007-06-13
The error is:

"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem"

---

### Post by Inxsible on 2007-06-13
What graphics processor  do you have on your machine?
 
Give us your system specs

---

### Post by Stuki on 2007-06-13
check the first post...

can't say exactly what I have, but I'll have to look...

---

### Post by Stuki on 2007-06-14
Intel Pentium II @ 833 MHz
512 MB RAM
Intel 82815 Graphics Controller

---

### Post by Outrunner on 2007-06-14
What did you do before this started happening? Try reconfiguring your xserver
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Stuki on 2007-06-14
YAY!! It's working... Thanks!

---

