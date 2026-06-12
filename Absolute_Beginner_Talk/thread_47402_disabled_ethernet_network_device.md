---
title: "disabled ethernet network device"
date: 2005-07-08
forum: Absolute Beginner Talk
---

### Post by sempsteen on 2005-07-08
hi guys! i'm totally new to linux environment. 2 days ago i downloaded (k)ubuntu both live cd and install images. i tried live cd and everything worked fine (included internet). and that big moment came and i formated my windows xp system to change with (k)ubuntu. during installation under "configuring the network with DHCP" title i get an error says cannot autoconfigure network. i manually did it. after installation i logged in with my username and password and started immediately discovering. everything was so simple that nothing confused my mind. but when i started web browser and type an url i realize that there wasn't any internet connection. i opened control center i look for the network configuration thansee that my ethernet device was disabled. i tried to configure it with both dhcp and manually but it didn't worked. i know all the settings from windows xp (ip, getaway, subnet..). what i did wasn't enough to work that card. now i'm writing to you with knoppix live cd. by the way i'm downloading ubuntu 5.04. please help me for this problem. my ubuntu download will end 2 hours later and i don't want to come across such a thing again :(

---

### Post by poofyhairguy on 2005-07-08
[QUOTE=sempsteen]hi guys! i'm totally new to linux environment. 2 days ago i downloaded (k)ubuntu both live cd and install images. i tried live cd and everything worked fine (included internet). and that big moment came and i formated my windows xp system to change with (k)ubuntu. during installation under "configuring the network with DHCP" title i get an error says cannot autoconfigure network. i manually did it. after installation i logged in with my username and password and started immediately discovering. everything was so simple that nothing confused my mind. but when i started web browser and type an url i realize that there wasn't any internet connection. i opened control center i look for the network configuration thansee that my ethernet device was disabled. i tried to configure it with both dhcp and manually but it didn't worked. i know all the settings from windows xp (ip, getaway, subnet..). what i did wasn't enough to work that card. now i'm writing to you with knoppix live cd. by the way i'm downloading ubuntu 5.04. please help me for this problem. my ubuntu download will end 2 hours later and i don't want to come across such a thing again :([/QUOTE]

Please tell more about your hardware:

Do you use a router? Do you have a cable modem or DSL? What network card do you have?

PS: Ubuntu is easier for new users...good call...

---

### Post by sempsteen on 2005-07-08
i connect to the internet through CNet ADSL Ethernet Router. the product page is:
[CNAD804-NF](http://www.cnet.com.tw/product/cnad804-nf.htm) [http://www.cnet.com.tw/product/cnad804-nf.htm](http://www.cnet.com.tw/product/cnad804-nf.htm). I dont know the ethernet card model or chipset. It is a standart 10/100Mbps network card and worked both in windows xp and knoppix live cd. By the way ubuntu 5.04 image download has finished and i started to install it. The same problem "network autoconfiguration failed" occured in the same title "configuring the network with DHCP". again i did it manually and fill the inputs like this:
IP Address: 10.0.0.14
Netmask: 255.0.0.0
Getaway: 10.0.0.2
Name server address: blank

these settings are form windows xp. whenever i shutdown the computer i will find the network card and write down the address here. thanks for your interest and sorry for my english.

---

### Post by sempsteen on 2005-07-08
ok i found my network card, it's CNet (DAVICOM DM9102AF chipset). Davicom's web site is [here](www.davicom.com.tw) but there isn't any product page for this card. for CNet the product page is [here](http://www.cnetusa.com/product/specs/nics_pro200.htm)

---

### Post by sempsteen on 2005-07-08
i searched, searched and searched for the solution and only found similar problems :(. finally i installed another network card with a via chipset and everything gone well. now i am writing to you from ubuntu :). helloo worldddd!

---

### Post by poofyhairguy on 2005-07-09
[QUOTE=sempsteen]i searched, searched and searched for the solution and only found similar problems :(. finally i installed another network card with a via chipset and everything gone well.[/QUOTE]

Thats my favorite way to fix hardware problems in Ubuntu.

---

