---
title: "Ubuntu @ Powerbook G4 400mhz"
date: 2010-12-12
forum: Apple Hardware Users
---

### Post by der-seemann on 2010-12-12
Hello,
after weeks of searching the net I still have this open problem...
What's about:

I'm trying to install Ubuntu (or lubuntu) to this old Powerbook [http://en.wikipedia.org/wiki/PowerBook_G4#Titanium_PowerBook_G4](http://en.wikipedia.org/wiki/PowerBook_G4#Titanium_PowerBook_G4)  with 400mhz PPC CPU.
I got it instslled and can use the terminal, but can't get the xserver running!
The problem is the display is verey sensitiv with correct resulution and frequency, if it is not OK, it will not show enything (well, some colors like northern lights :-) but nothing else )
I can login using the keyboard and hear the logon sound of gnome. but of cause i cant see anything :-(
I got no external monitor for testing.


Now the big question:
how can i setup the grafic card in the actuel version of ubuntu?
here i found some info, but it's not working anymore with 10.10
[http://wiki.ubuntuusers.de/Archiv/Apple_Powerbook_G4_Titanium](http://wiki.ubuntuusers.de/Archiv/Apple_Powerbook_G4_Titanium) 
here i found the following datas for the screen:
resolution: 1152x768 [INDENT]horizontal
    31-46  vertikal
    50-70 
[/INDENT]Thx for your help!!!
David

---

### Post by oswaldkelso on 2010-12-12
Try this one but it may be to old.

wget [http://www.rockhopper.dk/old/linux/files/xorg.conf.ati128](http://www.rockhopper.dk/old/linux/files/xorg.conf.ati128)

If that fails

[http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)

---

### Post by linuxopjemac on 2010-12-12
can you give me a link to the page of your type of Mac in everymac.com please ?

---

### Post by der-seemann on 2010-12-13
[http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_400.html](http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_400.html)
only changed RAM to 1GB and HDD to 80GB

---

### Post by linuxopjemac on 2010-12-14
```
wget http://mac.linux.be/files/xorg/powerbook3.txt
sudo mv powerbook3.txt /etc/X11/xorg.conf
```
reboot

---

