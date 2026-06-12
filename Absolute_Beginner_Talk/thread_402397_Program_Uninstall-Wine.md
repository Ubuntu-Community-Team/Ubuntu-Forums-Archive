---
title: "Program Uninstall-Wine"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by owerio on 2007-04-05
Hello. How do we uninstall the programs that we installed via wine ? Is there a command?

---

### Post by LJM on 2007-04-05
Someone I know is wondering the same thing. 

In her case, the program she'd like to get rid of is EAC (Exact Audio Copy). The question is how to remove it completely, including the configuration files (registry files?), so that it can be reinstalled from scratch to see if some problems get fixed that way.

Thanks in advance!

---

### Post by david_kt on 2007-04-07
> **LJM said:**
> Someone I know is wondering the same thing. 

In her case, the program she'd like to get rid of is EAC (Exact Audio Copy). The question is how to remove it completely, including the configuration files (registry files?), so that it can be reinstalled from scratch to see if some problems get fixed that way.

Thanks in advance!

It depend whether or not your program includes uninstall program. Navigate to the folder of your program, for example:

~/.wine/drive_c/Program Files/Your program

If you see uninstall program (for example uninstall.exe), just run it to uninstall.

DK

---

### Post by miggols99 on 2007-04-07
I use a program called wineXS. You can download it here:

[http://tsx.nl/index.php?p=winexs]("http://tsx.nl/index.php?p=winexs")

---

### Post by rai4shu2 on 2007-04-07
Another thing you can do is navigate here in Nautilus/Konqueror/Thunar:

~/.local/share/applications/wine/Programs

Then if you find an uninstaller, you can double-click on that.

---

