---
title: "xserver doesn't start"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by DougW on 2006-09-03
I've just upgraded my monitor to a ViewSonic VA902/VA902b and now the xserver does not start on boot. Can I fix the problem without having to reinstall ubuntu? If so will someone please help me?

---

### Post by Omnios on 2006-09-03
Anyways as another viewsonic user there monitors are impressive.
As for your problem either start in recovery mode of command prompt where the xserfver will not start and use
```

sudo dpkg-reconfigure xserver-xorg

```

 This will start a turtle like graphics xserver graphical configuration editor where it should auto detect you monitor. It also configs keyboard and mouse.

---

### Post by Omnios on 2006-09-03
Anyways as another viewsonic user there monitors are impressive.
As for your problem either start in recovery mode of command prompt where the xserfver will not start and use
```

sudo dpkg-reconfigure xserver-xorg

```

 This will start a turtle like graphics xserver graphical configuration editor where it should auto detect you monitor. It also configs keyboard and mouse.

---

### Post by ispmarin on 2006-09-03
Probably the screen refresh rate is wrong for your new monitor. You can fix this in several ways. First, search for the Vertical and Horizontal frequencies for your monitor. With this in hand, do a 

sudo dpkg-reconfigure xserver-xorg

and enter the frequencies that you have found. The other way (that I prefer) is to open as root (or with sudo) the file

sudo vi /etc/X11/xorg.conf

Search for the "Monitor" section, and edit the frequencies ranges that are there.

Hope it helps.

---

### Post by DougW on 2006-09-03
You suggestions don't seem to be working. Do I need to save this file somehow? I get to the end and it dumps be back to the prompt.

---

### Post by DougW on 2006-09-03
I've followed your advice and the program autodected my monitor however when I restarted xserver refused to start. Do I need save the configuration file? The program just dumped me back to the prompt. Your help is much appreciated.

---

### Post by macdo on 2006-09-03
Start X. 
```
startx
```

If that doesn't work, try a reboot:
```
sudo reboot
```

---

### Post by DougW on 2006-09-03
When I use startx I get a '(ee) no devices detected' error.

---

