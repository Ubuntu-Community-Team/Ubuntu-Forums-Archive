---
title: "Resolution Problem."
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by anoopyadav on 2007-08-26
HI! I just installed ubuntu 7.04 2 days ago & everything works fine. But my screen resolution is stuck at 1024x768. I'm using an acer 3680 laptop & the lcd has a native resolution of 1280x800.
I already tried using 915resolution as some threads suggested but as soon as I restart the resolution is back at 1024x768:(. Please help.

---

### Post by angryfirelord on 2007-08-26
You have to edit your xorg.conf.
Open gedit:
```
sudo gedit /etc/X11/xorg.conf
```
Scroll down to where you see *Section "Screen"*
You should see the word Modes with different resolutions. Add "1280x800" in front of each of them and make sure to put that first in line. Ex: Don't do:
```
"1024x768" "1280x800"
```
This will cause 1024x76 to be used first. Instead, do:
```
"1280x800" "1024x768"
```
Remember to add that for each of the Modes, not just the first one.

Save and exit gedit. Logout and log back in.

Now, if for some reason you really mess up your xorg, you can always run this nifty command:
```
sudo dpkg-reconfigure xserver-xorg
```

---

