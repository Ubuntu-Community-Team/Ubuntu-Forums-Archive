---
title: "how to disable mouse wheel click?"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by Mouseball on 2007-07-27
Just installed Kubuntu 7.04, now everytime i push in the middle mouse button (happens accidentally a lot) it tries to change the page on me or search the web for random phrases. its very irritating. Anyone know how to disable this entirely?

---

### Post by tomcheng76 on 2007-07-27
may be delete the line "ZAxisMapping 4 5" in Section "InputDevice" of /etc/X11/xorg.conf
then press ctrl alt backspace

---

### Post by Mouseball on 2007-07-27
Still very new to linux. how should i edit this file? I tried using vi but it told me it could not open the file for writing.

---

### Post by tomcheng76 on 2007-07-27
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.27.7.2007.BACKUP
sudo gedit /etc/X11/xorg.conf
```

---

### Post by Mouseball on 2007-07-27
sudo: gedit: command not found

---

### Post by avik on 2007-07-27
Use sudo nano /etc/X11/xorg.conf.  Enter your password, edit the file, and press Control-x to save and exit.  The sudo tells the computer to run nano as root, which gives you permission to write to the file.

---

### Post by Mouseball on 2007-07-27
nvm, found something on kubuntu IRC
Thanks for your input :)

---

