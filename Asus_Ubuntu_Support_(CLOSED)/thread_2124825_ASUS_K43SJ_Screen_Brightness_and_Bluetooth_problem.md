---
title: "ASUS K43SJ: Screen Brightness and Bluetooth problem"
date: 2013-03-12
forum: Asus Ubuntu Support (CLOSED)
---

### Post by techbuntu27 on 2013-03-12
I had installed Ubuntu 12.04 LTS on this netbook: [http://www.asus.com/Notebooks_Ultrabooks/K43SJ/](http://www.asus.com/Notebooks_Ultrabooks/K43SJ/) and yes my problem is all about the "Screen Brightness" and "Bluetooth" which is not working.

FIRST, everytime I boot my netbook the screen Brightness is always bump up to its full settings. I've already adjusted brightness settings (ubuntu settings) and also the Fn keys for adjusting brightness is working properly. But when the netbook display dim (dim screen after 10 mins) and I again use the netbook the screen brightness is on its full settings again and yes this annoys me a lot, because I keep on adjusting the screen brightness each time I switch on my netbook.

SECOND, the Bluetooth doesn't work, I mean the icon is there and when I turn it ON, it's then labeled as ON. But when I see the properties it says it's OFF and when I try to detect it using my phone. It doesn't recognize my netbook so I know something is wrong.

So guys, I hope you can help me with this problem. I use Linux because it's cool and I really love it the first time I'd used it. But this problem that I'm having right now makes me feel bothered. I hope you can assist me with this. Thanks.

---

### Post by daveb3 on 2013-03-17
> **techbuntu27 said:**
> SECOND, the Bluetooth doesn't work, I mean the icon is there and when I turn it ON, it's then labeled as ON. But when I see the properties it says it's OFF and when I try to detect it using my phone. It doesn't recognize my netbook so I know something is wrong

HI, does your bluetooth work in windows??? i dual boot windows 8 x64 and ubuntu 12.10 on an ASUS K55A laptop and in windows task manager on the performance tab it lists cpu, disk, BLUETOOTH, network. it always says bluetooth is disconected and grays it out as an option. i think the bluetooth driver in windows is installed as default and the same in ubuntu so it gives me an icon and which is why i have it listed in win task manager and in ubuntu i too can turn bluetooth on and make it visable but i DONT ACCTUALLY HAVE BLUETOOTH ON MY LAPTOP so i need to use a dongle. ive read the info on asus support site and i DONT have bluetooth builtin to my laptop... maybe yours is the same???

---

### Post by Mr.BS on 2013-03-24
Don't know about the BT, it says optional on the Asus link you provided....? My K53SJ doesn't have BT.

The brightness problem also depends on which desktop you use (Unity, gnome-shell etc.) but you can try the tips in this thread:
[http://ubuntuforums.org/showthread.php?t=1875982&page=3](http://ubuntuforums.org/showthread.php?t=1875982&page=3) and then the part where you must edit etc/rc.local

Since this is for the K53V (but works on my K53SJ) you might try this first in a terminal:
```
echo 300 | sudo tee /sys/class/backlight/intel_backlight/brightness
```

In 12.04 this solved the brightness problem but it kinda returned when i updated to 12.10...:(

---

