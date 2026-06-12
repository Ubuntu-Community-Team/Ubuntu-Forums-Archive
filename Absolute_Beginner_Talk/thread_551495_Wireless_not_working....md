---
title: "Wireless not working..."
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by lespaul_rentals on 2007-09-15
My first installation of Ubuntu/Kubuntu went just splendid.  I could connect to the wireless network just perfectly.

However, ever since I started with a fresh install of Ubuntu, I haven't been able to connect to any wireless network.  I can see all my neighborhood WiFi networks as well as my private WLAN but I can't join any of them.

Yes, I have enabled wireless networks in the Network Manager, and tried disabling Ethernet connections as well.  I have no idea why it isn't working this time around.

---

### Post by pactpc40 on 2007-09-15
which wireless card are you using? What type of computer?

---

### Post by lespaul_rentals on 2007-09-16
WLAN card: Toshiba PA3171U-1MPC
Laptop: Toshiba Satellite A15-S157

I'm using Ubuntu 7.04.

---

### Post by pactpc40 on 2007-09-16
Toshiba is generally support by Ubuntu.  However you may try to look for a windows drivers,,, then use ndiswrapper to install it. Use terminal and try something like the below. Also Ubuntu forums has a lot of articles concerning wireless cards. Good luck...


sudo apt-get install ndiswrapper-utils

sudo ndiswrapper -i  (i command to install you windows driver) also ndiswrapper has help files

sudo ndiswrapper -m

sudo modprobe ndiswrapper

---

### Post by lespaul_rentals on 2007-09-19
Thank you for your wonderful help.  I hope this works!

EDIT: I have searched the web far and wide for the driver, but I can't seem to find it.  Do you know of a site that has old drivers?

---

### Post by pactpc40 on 2007-09-21
Is there nothing on the OEM website? Maybe under support and downloads? did not look to far but try browsing here...
[http://sdd.toshiba.com/main.aspx?Path=8100000000220000000100006598000000E7/810000000C58000000010000659C00002C36](http://sdd.toshiba.com/main.aspx?Path=8100000000220000000100006598000000E7/810000000C58000000010000659C00002C36)
good luck.

---

