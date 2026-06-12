---
title: "Xwindow doesn`t work after instalation"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by LCC on 2006-07-11
I have installed Ububtu 5.10 elf for x64 and after isntaling Ububtu when I first restart the PC a message of error apears saying that something is wrong with the xwindow, i still can use the code lines(wich I don`t know), do I have to install the driver for the graphic card or anything like that and if so how do I do it in the code line??? Thanks

AMD 64 X2 
Asus A8N-SLI Deluxe Nforce4
1024 mb ram
ATI Radeon Xpress 800 256mb
80 gb and 300 gb HDD
2 gb of swap/ 20gb home

---

### Post by Dr. Nick on 2006-07-11
from the command line run 

**sudo nano /etc/X11/xorg.conf**

look at the device section on the driver line, what does it say?

If it doesnt say "vesa" then change it to "vesa" then ctrl+x to save then type

**startx**

and see what happens

---

### Post by LCC on 2006-07-13
Thanks man for the help, but for some reason I couldn`t get it to work with the sudo nano /etc/X11/xorg.conf, it was easier with 


    sudo dpkg-reconfigure xserver-xorg

and then changing from ati to vesa, now I`ll try to update to the newest version.

---

