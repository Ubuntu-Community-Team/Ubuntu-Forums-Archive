---
title: "kde gui problem"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2007-05-10
I am using kubuntu 7.04. Whenever i start any GUI program , i get the following error 

> ejaz@ejaz-desktop:~$ kate
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

 

after this error the program starts.
Please tell me what is this error and how to get rid of it?

---

### Post by deepwave on 2007-05-10
You can safely ignore that error.  Its the X just whining about some sort of input device.  I used to get those error messages all the time.

If you want to look at your /etc/X11/xorg.conf, and look for any unused input devices.  You could probably comment out those sections out (like the wacom tablet stuff).

---

### Post by u04f061 on 2007-05-10
There is another problem with KDE GUI. Whenever I launch QT designer , The system logs me out. so i am unable to use QT Designer.

---

