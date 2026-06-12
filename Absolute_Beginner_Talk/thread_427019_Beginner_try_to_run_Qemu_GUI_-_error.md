---
title: "Beginner try to run Qemu GUI - error"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by darkworld on 2007-04-29
Trying to run Qemulator-0.3.2 but get error:

root@dark-desktop:/home/dark/qemulator/Qemulator-0.3.2# ./setup.py
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

gtk and/or glade is not installed - exiting...

checked install file and i have all the dependancies. Python, pygtk2, libglade2.

So is it the Xlib thingy thats wrong? sorry i know little but not everything about linux. Any help much appreciated.

---

### Post by littletux on 2007-09-13
Hy darkworld

can you post your output from  
dpkg -l

and a aditional question

Did you run qemu-gui as root or as user? 


Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

(this message you had, can be from running as root)

---

