---
title: "A few big problems regarding printing and logging out"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by SSB on 2007-04-12
First off, I hooked up my new printer the other day - a Canon Pixma MP600 to be precise. Ubuntu detects it fine and it registers as the proper printer, it selects the MultiPASS C2500 model in the list, though, and picks the bjc600 driver. With it, I can print.. but it only takes up about 1/4 of the page, maybe a bit more. Choosing different drivers either does the same thing or prints the proper size with one color and other colors on the broken size.

Second, logging off, restarting, or anything involving restarting the x server makes my system just fart and die. The monitor goes dark and into power saving mode and I have to turn off the computer to get it working right. I don't know what info you need for this.. I'll provide anything.

---

### Post by Legionox on 2007-04-13
About your printer problem visit [http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP600](http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP600) and I hope you can find some help there and have you tried reconfiguring your x-configuration file using ```
sudo dpkg-reconfigure xserver-xorg
```

---

