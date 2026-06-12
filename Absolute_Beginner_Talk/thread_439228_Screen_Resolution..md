---
title: "Screen Resolution."
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by Don1500 on 2007-05-10
Am I missing something? The highest resolution on the screen under Ubuntu is like looking through a kehole compaired to my windows screen. My Laptop can take vurtually any of the resolutions supplied by Ubuntu and then some, I am running 1440X900 in windows and can't find that in setup for Ubuntu. Any help?

Thanks in advance.

---

### Post by pizzutz on 2007-05-10
easiest way is from the terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

follow the prompts, and it will allow you to select which screen resolutions appear in the drop box.

alternately, you can manualy modify the entries in /etc/X11/xorg.conf

Standard disclaimer: backup your /etc/X11/xorg.conf file before making any modifications.

---

### Post by annda on 2007-05-10
also make sure that you have the drivers for your graphic card installed. what is your card and which driver are you using?

---

### Post by Don1500 on 2007-05-10
Found it! Thanks to all.

---

