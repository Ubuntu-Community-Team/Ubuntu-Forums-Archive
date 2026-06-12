---
title: "Just installed... can't connect to network/internet"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by blizzy on 2007-11-17
Just installed from Vista basic to Ubuntu... How do I connect to the internet..  I type in the "network name"... and it 'searches'.. and nothing happens.

Thanks.

---

### Post by limac on 2007-11-17
click on the network icon, that should show you a couple of network connections in range. and btw did you install your wireless in when you had vista. if you did then your network name or ssid should be there. then click on it, type in the passphrase, and you are set to go!

---

### Post by blizzy on 2007-11-17
i dont see any network connections in range..... the only one is the one I added.. but when i click on it.. it goes away.. and mozilla gives me "Server no found"

thanks

---

### Post by mellowd on 2007-11-17
open up a terminal and type ifconfig. what do you see?

---

### Post by limac on 2007-11-17
yeah post back whatever you get by typing in iconfig into your terminal.

---

### Post by limac on 2007-11-17
make that iconfig ifconfig, srry.

---

### Post by blizzy on 2007-11-17
attached is a pic from that laptop

thanks again

---

### Post by blizzy on 2007-11-17
help..

---

### Post by Rev60073 on 2007-11-17
I guess you're trying to use your built-in WiFi card to connect? Try to do a search on "iwconfig" in here, it will show you examples of how to connect to a WiFi network.

If that's not the case, and you have a router at home to connect to the internet, then you need to enable DHCP to obtain an IP address. Go to System->Administration->Network and set your wired connection to "roaming mode".

---

### Post by blizzy on 2007-11-17
i have "roaming mode" on.. dont know how to enable DHCP.. here is the iwconfig attached... Thanks.

---

### Post by blizzy on 2007-11-18
bump

---

### Post by tyggna1 on 2007-11-18
plz post lspci so we know what kind of wireless card you use -- I'm guessing it's a problem with your driver.

---

### Post by blizzy on 2007-11-18
how do i get that info??

---

### Post by blizzy on 2007-11-18
i have an Acer 5000... 
Wireless stuff:   BCM4318 [Airforce One 54g] 802.11g Wireless LAN Controller

---

### Post by blizzy on 2007-11-18
bump

---

### Post by blizzy on 2007-11-18
help

---

### Post by blizzy on 2007-11-18
bumpsssss

---

### Post by tyggna1 on 2007-11-18
sorry about the slack level of posts--it's Sunday and I have a lot of church responsibilities.

Anyway,  I found a guide for setting up your card.   I was right, it is a driver problem.  The bad news is, there is no linux driver for it, the good news is that it should work with ndiswrapper.

[Here]("http://ubuntuforums.org/showthread.php?t=190177") is the guide for setting up your wireless card.   I hope this helps.

---

### Post by blizzy on 2007-11-20
that website isnt letting me install that driver :(.

thanks for the help, though

---

### Post by blizzy on 2007-11-20
bump

---

### Post by CCNA_student on 2007-11-20
I looked at you terminal output and I saw that you had the same wireless NIC I once had from Broadcom. Broadcom refuses to release the source code for the firmware on that 
wireless NIC. What I did was I bought a wireless NIC from Intel, the Intel 2915ABG for about $25 dollars. Then once you have that NIC installed you just click on the network icon in the top-right corner and you can see all wireless networks in range. This was the only way I could get my Gateway laptop to log onto a wireless network.

---

### Post by blizzy on 2007-11-20
what is a nic?.. ill google it now.. software?.. thanks for your help

---

### Post by CCNA_student on 2007-11-20
NIC stands for Network interface card, it connects you to the network.

---

### Post by blizzy on 2007-11-20
How do I install the card in my laptop.. does a panel unscrew on the bottom?

---

### Post by CCNA_student on 2007-11-20
Yes, there should be a panel that is held in place by one screw. You will the the wireless 
NIC and two wires attached to it. It probably says the name of the NIC somewhere, just so you know you are taking out the right device. It is very simple. And to connect to your network for now just use an ethernet cable.

---

### Post by blizzy on 2007-11-20
oh ok.. thanks a lot

---

### Post by PogMoThoin on 2007-11-20
BTW, Off topic, You right click, copy (or shift+ctrl+c) to copy from a terminal & then right click, paste (ctrl+v) to paste output in here.

ctrl+c= copy
ctrl+v= paste
You must press shift with these shortcuts 2 get them work in terminal as ctrl+c cancells a command in terminal.

Much easier than taking, importing & uploading pics :)

---

### Post by blizzy on 2007-11-20
Since my problem is not getting on the internet... Its impossible to be on a forum on my linux laptop...  I take a picture of the linux laptop.. and submit them so you guys can see them on this Vista laptop.

---

