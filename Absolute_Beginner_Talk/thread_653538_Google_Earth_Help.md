---
title: "Google Earth Help"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by Ajay Ramaseshan on 2007-12-30
I have tried installing Google Earth on Ubuntu 7.04 with Intel x-64 desktop but after installing it gives this error on the terminal.....

Xlib:  extension "GLX" missing on display ":0.0".

And when I double click the desktop icon it says it is unable to detect the graphics card... and says the driver for the graphics card has not been installed but it runs on Windows Vista...

Could you please tell me  suggestion??

---

### Post by taurus on 2007-12-30
You first need to install a driver for your graphic card to enable 3D first.  What kind of graphic card is it anyway?

---

### Post by lisati on 2007-12-30
Forget about it working on Windows being a reliable guide - Ubuntu requires its own version of Google Earth which won't work on Windows (and vice versa) - just because it works with one OS on your system, it doesn't automatically follow that you can get it working on the other without doing some tinkering.

Check out enabling accelerated graphics on your system - it can be found in the "Restricted Drivers" option of the System->Administration menu.

---

### Post by Ajay Ramaseshan on 2008-01-02
I checked the Restricted Drivers manager under System ->Administration it shows only one driver Intel(R) PRO/Wireless 3945 Network Connection Driver for Linux Nothing else is displayed how do I get the graphics driver...??

---

### Post by The Cog on 2008-01-02
We can't tell you that until you tell us what card you have. Posting the output of the command
**lspci**
would be useful.

---

### Post by zhouxing on 2008-01-03
1. Download latest Google Earth Linux
2. Copy it to your homefolder
3. Open Terminal
4. type: chmod +x GoogleEarthLinux.bin
5. type: sudo ./GoogleEarthLinux.bin

wola, you should be able to install and run Google Earth now, provided your have proper display driver for 3D acceleration installed.

You can use Envy to install your display card driver before running Google Earth.

---

### Post by hyper_ch on 2008-01-03
It's better to add the Medibuntu repos and get Google Earth from there than doing a manual isnmtall.

---

