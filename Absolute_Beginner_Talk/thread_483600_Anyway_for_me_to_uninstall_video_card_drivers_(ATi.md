---
title: "Anyway for me to uninstall video card drivers? (ATi)"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by inferiorjon on 2007-06-24
i had the restricted drivers installed and then i thought maybe the closed source drivers would help me out and get increased performance but i ended up dropping from 80fps to 3.5fps... 

i have an X1600pro so i guess i should have expected complications... but anyway, is there a way for me to uninstall these drivers?? please let me know! thanks :)

---

### Post by overdrank on 2007-06-24
> **inferiorjon said:**
> i had the restricted drivers installed and then i thought maybe the closed source drivers would help me out and get increased performance but i ended up dropping from 80fps to 3.5fps... 

i have an X1600pro so i guess i should have expected complications... but anyway, is there a way for me to uninstall these drivers?? please let me know! thanks :)

Hi I believe you answered your own question. Just enable the restricted drivers again under system, Admin, restricted driver manager.

---

### Post by inferiorjon on 2007-06-24
i already tried doing that and i just got a pop up that said "Your hardware does not need any restricted drivers"

ahhhhhhh!!!

---

### Post by overdrank on 2007-06-24
> **inferiorjon said:**
> i already tried doing that and i just got a pop up that said "Your hardware does not need any restricted drivers"

ahhhhhhh!!!

Hi if you use the keys ctrl.atl,F1  this will take you to the terminal then login and use the command sudo dpkg-reconfigure -phigh xserver-xorg this will configure your xorg and get you back to the desktop.

---

### Post by anon32 on 2007-06-24
If your framerate dropped to 3.5fps after installing fglrx (the proprietary driver), likely, the issue is that the 3d acceleration is not working and you are running on a software engine. Please open a terminal (applications -> terminal or system -> konsole) and run "glxinfo | grep direct" (without the quotes).

 If it says yes, then you should remove the drivers by uninstalling the "xorg-driver-fglrx" package and then modifying the file /etc/X11/xorg.conf (with a text editor - e.g. "gksu gedit /etc/X11/xorg.conf"), replacing all entries of "fglrx" with "ati".

If it says no, please let us help you get your drivers setup right.

---

### Post by inferiorjon on 2007-06-25
with "sudo dpkg-reconfigure -phigh xserver-xorg" i ahve no idea what i'm doing and with "glxinfo | grep direct" it says:

jon@jonsBBQ:~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

i guess i need you guys to guide me? and btw thank you for your time, i really appreciate it :)

---

### Post by inferiorjon on 2007-06-25
i need help :(

---

