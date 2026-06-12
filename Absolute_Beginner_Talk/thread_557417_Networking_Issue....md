---
title: "Networking Issue..."
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by Spenshire on 2007-09-22
I just built a new computer and have XP and Ubuntu dual-booting on it just fine.

My issue is that I can not connect to the internet at all in Feisty and apparently have no connection even though I have an ethernet cable plugged in and it works fine when running XP.

I am using a GIGABYTE GA-P35-DS3R motherboard and heard that there might be some issue with that and Ubuntu in regards to network connections.

Any and all help you can give would be fantastic, and explain things out in the simplest possible form if at all possible, I have done VERY little work on Linux before, so I know next to nothing about it.

---

### Post by agurk on 2007-09-22
From [http://ubuntuforums.org/showthread.php?t=459459](http://ubuntuforums.org/showthread.php?t=459459):
[quote=lifishing]Gigabyte P35 DS3R motherboard works fine with Feisty.
There is an easily fixed problem with on board network card though. For some reason, some boards has NIC deactivated by default. Linux driver doesn't know how to activate it. You need go to BIOS, in the Integrated Peripherals, choose "On board LAN ROM", enable it. This will activate the card. Once your card is activated, this option can be safely turned off again.
Another thing is when you install Windows XP, it can deactivate the NIC when shutting down. Just set "Wake-on-lan after shutdown" to be enabled in Windows driver configuration will solve the problem
See [http://gentoo-wiki.com/HARDWARE_RTL8168](http://gentoo-wiki.com/HARDWARE_RTL8168) for detail.[/quote]

Hope that helps.

---

### Post by Pumalite on 2007-09-22
[http://www.comptechdoc.org/os/linux/usersguide/linux_ugbasicnet.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugbasicnet.html)

---

### Post by colino on 2007-09-22
May I suggest the start of your search:

[http://www.google.com/search?q=realtek+8111+driver+linux&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=realtek+8111+driver+linux&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)
[http://www.giga-byte.com.tw/Support/Motherboard/Driver_Model.aspx?ProductID=2543](http://www.giga-byte.com.tw/Support/Motherboard/Driver_Model.aspx?ProductID=2543)
[http://ubuntuforums.org/showthread.php?t=467757&highlight=realtek+rtl8111%2F8186b](http://ubuntuforums.org/showthread.php?t=467757&highlight=realtek+rtl8111%2F8186b)

From the last one it appears the driver is the r8168, and is apparently supported in Linux.  So the next question is what isn't working... can you open a terminal and at the prompt, enter the command: 

$ ifconfig

and report the results?

---

### Post by Pumalite on 2007-09-22
Also:
lspci

---

