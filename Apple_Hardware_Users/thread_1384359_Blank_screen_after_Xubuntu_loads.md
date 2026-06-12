---
title: "Blank screen after Xubuntu loads"
date: 2010-01-18
forum: Apple Hardware Users
---

### Post by redmac2010 on 2010-01-18
:sad:my imac g3 power pc **[COLOR=#ff0000]screen[/COLOR]** goes **[COLOR=#ff0000]blank[/COLOR]** and the power button goes orange after Xubunto loads, but the computer is still running, how do I fix this problem, if you have any information please be very spesific I have no idea what im doing so include all steps, thanks to anyone who posts

(if this helps the computer makes the drum roll noise if I hit enter but the **[COLOR=#ff0000]screen[/COLOR]** still stays **[COLOR=#ff0000]blank[/COLOR]**)

(xbuntu version -xubuntu-8.10-alternate-powerpc)
(system informaiton...
(powerPc G3 266MHz/512k catche/32mb/6gb HD/24x CD-ROM/rage Pro/6MB SGRAM)

---

### Post by linuxopjemac on 2010-01-18
at the blank screen try to get into a console (CTRL-Command-F1) and then change the Xorg.conf file. 

```
sudo nano /etc/X11/xorg.conf
```

make a simple file like this:
```

Section "Device"
Identifier "Configured Video Device"
BusID "PCI:0:18:0"
Option "UseFBDev" "true"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
HorizSync 58-62
VertRefresh 75-117
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
EndSection
```

If it doesn't work change the 18 to 16 in
BusID "PCI:0:18:0"

---

### Post by linuxopjemac on 2010-01-18
after that, you need to restart X. I think Xubuntu uses XDM ? I am not sure, please someone else here ?

either;

```
sudo xdm restart
```

or 

```
sudo gdm restart
```

---

### Post by redmac2010 on 2010-01-18
it was sudo gdm restart

---

### Post by linuxopjemac on 2010-01-18
did it work ?

---

### Post by B_Free on 2010-01-18
You only have 32 mb of ram. This is one of the problems. You should have at least 256.

---

### Post by linuxopjemac on 2010-01-18
I could have told you, stupid that I didn't see it. Add RAM, it's cheap nowadays.

---

### Post by redmac2010 on 2010-01-18
linuxopjemac you are a genius it worked the first time ever that i have been able to see whats happening on my computer thank you so much, i had to use 16 instead of 18 in BusID and use sudo gdm restart, it popped right up, now the only thing is it tells me that i am running in low graphics mode and if i chose anything other than run Ubuntu in low graphics mode this time only it will revert to the old non functioning blank screen settings, I am just happy that its mostly working now :D but if u have any other info on how to fix the low graphis issue i would greatly apreciate it ,
 
thanks again

---

### Post by linuxopjemac on 2010-01-18
You need to add more RAM to a minimum of 256 Mb. I would add the maximum, which is 512 Mb, so 2 times 256 Mb, see [here]("http://eshop.macsales.com/item/Other%20World%20Computing/100SO256168L/"). If you are low in budget, you can buy the minimum [here]("http://eshop.macsales.com/item/Other%20World%20Computing/100SO128168/").

---

### Post by redmac2010 on 2010-01-18
also nothing will open after i log in the desktop icons disapear and when say i go to places administrator documents the box will open for a second then ge replaced  with a box labled" thunar" and then all boxes will close , also when i shut down the computer it just goes to the xubuntu blue screen and stays there never changeing is this normal?

---

### Post by linuxopjemac on 2010-01-18
this is not normal. I don't know if it has anything to do with your amount of RAM. Another problem could be your PRAM battery. You have to correct time with an NTP server. If after you installed extra RAM, you still experience problems, even if your PRAM works fine, I would recommend Debian Lenny. It simply works.

---

