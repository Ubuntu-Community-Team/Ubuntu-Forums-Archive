---
title: "Adding new connection"
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by AtinLango on 2006-03-08
In my Ubuntu setup, under System/Administration/Networking/Connection, there is no option for 'Add'. Tere are only 'Properties, Ativate, Deactivate'. Yet the Help says there is 'Add' option.

How do I add a new connection?

---

### Post by swamytk on 2006-03-08
The help manual talks about plain GNOME Network settings tool. But the application what you use is Ubuntu customized one. Instead of manually adding, connections tab should list down your network devices automatically. Is it doing it properly?

---

### Post by AtinLango on 2006-03-08
No. It is not listing my usb modem and wifi.

Swamytk, this is my age old problem if you remember about the usb Huawei wireless ETS2077 modem. I recall you are the one who suggested that I try using ndiswrapper. I tried it and it seemed to have installed the driver from windows properly. In Ubuntu, when I type "ndiswrapper -l", the driver is listed as present.

Now I want to add the new connection but it is not listed. Even my wifi (which I also use in windows) is not listed.

---

### Post by swamytk on 2006-03-08
did u try iwconfig command? can u see your network detected. If it is detected, you can install gtkwifi from [http://sourceforge.net/projects/gtkwifi](http://sourceforge.net/projects/gtkwifi). It is a nice front end for configuring wifi networks.

---

### Post by AtinLango on 2006-03-08
Let me clarify.

I mentioned the wifi as a by the way. Afterall I only use the wifi when I go to a hotspot. Thats very rare. But I still need it detected.

My everyday use is with the USB wireless modem.  I hope there is no confusion here between wifi and wireless modem.

---

