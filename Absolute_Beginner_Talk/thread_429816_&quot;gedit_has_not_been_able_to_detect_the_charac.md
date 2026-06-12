---
title: "&quot;gedit has not been able to detect the character coding.&quot;"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by OscarL on 2007-05-01
I try to install a downloaded driver for my graphic card but I get an error message. What to do?

Could not open the file /home/oscar/Desktop/NVID…nux-x86-1.0-9755-pkg1.run.

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

---

### Post by taurus on 2007-05-01
Wait a second.  That file is a binary meaning you suppose to run it to install it on your machine, not to open it with gedit.  What are you trying to do, exactly?

---

### Post by Perfect Storm on 2007-05-01
Seems you're trying to open the script file with gedit....
Well, I don't know which guide you're following, but you shouldn't open it with gedit.

---

### Post by OscarL on 2007-05-01
well, I just downloaded it and double clicked it. I just want to install the driver.

---

### Post by taurus on 2007-05-01
If you want to install nVidia driver for your graphic card, you need to do

Applications -> Accessories -> Terminal
```
sudo /etc/init.d/gdm stop
cd ~/Desktop
chmod 755 *.run
sudo ./NVIDIA-linux-x86-1.0-9755-pkg1.run
```
Then, you probably need to modify your /etc/X11/xorg.conf to use "nvidia" driver instead of "nv" or a generic driver in there right now.

Otherwise, use envy to install nVidia driver for your graphic card.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

