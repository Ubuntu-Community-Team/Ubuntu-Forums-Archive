---
title: "No GUI in Ubuntu Studio"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by billybandawe on 2007-12-02
I have an ATI Radeon x1650 and just finished installing Ubuntu Studio. When I booted into it, I got no graphical interface. It booted straight into the command line. I read forums for this and tried the suggested commands, but nothing works. I even tried reinstalling, but nothing. is it my graphics card, or is it that I messed up installation?
Thanks for your help.

---

### Post by jken146 on 2007-12-02
What happens when you do ```
startx
```?  Post the output if it doesn't work, also post the output of ```
cat /etc/X11/xorg.conf
```

---

### Post by ilrudie on 2007-12-02
Try 
sudo apt-get install fglrx
sudo aticonfig --initial
sudo aticonfig --overlay=Xv
reboot

---

### Post by MetalMusicAddict on 2007-12-02
Make sure you piked the "Desktop" task during the install.

---

