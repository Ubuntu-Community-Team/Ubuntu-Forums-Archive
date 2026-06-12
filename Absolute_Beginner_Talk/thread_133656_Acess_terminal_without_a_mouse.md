---
title: "Acess terminal without a mouse?"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by kc0rtg on 2006-02-20
I am new to linux and i have asked for help in another area to get my serial mouse to work.  I was told by someone that i need to edit my "xorg.conf" file from a terminal.  Is there a way i can get to the terminal without using a mouse?  And also, am i able to edit files if i boot from the live CD?  Or will i have to do an install on the hard drive?

---

### Post by carlosqueso on 2006-02-20
you should be able to get into a terminal by pressing Ctrl+Alt+F1 without using a mouse.  However, if you are using a live CD, you'll have to edit the xorg.conf every time you use the CD.  If you install to the hard drive, you only need to do it once.

---

### Post by aysiu on 2006-02-20
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nano /etc/X11/xorg.conf
```

---

### Post by kc0rtg on 2006-02-24
yes, ctrl-alt-f1 worked.  Thank you all for the replies :)

---

### Post by Iowan on 2006-02-25
I presume you discovered that CTRL-ALT-F7 (or just ALT-F7) takes you back to the desktop.

(Happy hamming from zero-land)

---

