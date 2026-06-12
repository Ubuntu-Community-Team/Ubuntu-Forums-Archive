---
title: "My short patience span....."
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by tartarian on 2006-04-12
OK, I've been pretty much solidly working at this problem for days, and I am not renound for my vast attention span!

This is my laptop and its wireless card [here]("http://support.packardbell.com/uk/item/index.php?i=spec_WirelessMiniPCILAN_Billionton&ppn=PB17C00101")
I've disabled the ethernet and modem options on Networking and configured the settings on the wireless (ra0). They are definatley correct. When I click  on the icon at the top right corner of my screen it says connected  but not recieving and data and the strength is at 0%

Please help, It will be so much easier if i can get on the net..... ](*,)

---

### Post by xXx 0wn3d xXx on 2006-04-12
[QUOTE=tartarian]OK, I've been pretty much solidly working at this problem for days, and I am not renound for my vast attention span!

This is my laptop and its wireless card [here]("http://support.packardbell.com/uk/item/index.php?i=spec_WirelessMiniPCILAN_Billionton&ppn=PB17C00101")
I've disabled the ethernet and modem options on Networking and configured the settings on the wireless (ra0). They are definatley correct. When I click  on the icon at the top right corner of my screen it says connected  but not recieving and data and the strength is at 0%

Please help, It will be so much easier if i can get on the net..... ](*,)[/QUOTE]
Ndiswrapper ?

---

### Post by tartarian on 2006-04-12
Whats Ndiswrapper?

---

### Post by xXx 0wn3d xXx on 2006-04-12
[QUOTE=tartarian]Whats Ndiswrapper?[/QUOTE]
[ You will need the windows drivers for your wifi card to make it work.](http://ubuntuforums.org/showthread.php?t=81461&highlight=wireless+cards+working)

---

### Post by tartarian on 2006-04-12
Ye i have them, but its an .exe file. when I try to run it in ubuntu it says file cannot be read...

---

### Post by taurus on 2006-04-12
Actually, you use ndiswrapper to install a driver, <filename>.inf, for your wireless card, not the .exe file...

---

### Post by xXx 0wn3d xXx on 2006-04-12
[QUOTE=tartarian]Ye i have them, but its an .exe file. when I try to run it in ubuntu it says file cannot be read...[/QUOTE]
Install wine and then run it and it will extract it to the .wine folder > driver_c > and then usually cabs in your home directory. Make sure to check show hidden files to be able to see the .wine directory.

---

