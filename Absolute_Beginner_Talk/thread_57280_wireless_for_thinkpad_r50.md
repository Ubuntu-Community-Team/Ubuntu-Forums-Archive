---
title: "wireless for thinkpad r50"
date: 2005-08-15
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2005-08-15
Hey everybody, 
Just installed ubuntu hoary on my thinkpad R50.  When I log on, it tells me that it could not locate a network and gives me a choice of "try again" or "continue" to log on.  I click continue and try to see if I can go online but no luck.  When I was using windows xp pro, i was able to use someone else's cable connection using my wireless but now with ubuntu I am unable to.

Help would be appreciated

---

### Post by mattpist on 2005-08-16
hey, i used to have a thinkpad t23 with ubuntu on it... i had the same problem with my orinoco gold card.

im assuming you're using a pcmcia wireless card. so, first, make sure your card is compatible with linux. if it's not, you might have some luck using ndiswrapper and your windows drivers. i dont know much about this, so you'll have to search the boards.

second, one of the things i noticed was that when i installed ubuntu if i had my pcmcia wifi card plugged in during the installation, i wasn't able to use my wifi card at all after installation. it's a bug i guess. make sure your wifi card is NOT plugged in when you install ubuntu, and during the install select "configure network later". when you boot into ubuntu, just plug your card in and it should work... you might have to open the network settings panel and "activate" the eth1 or whatever your wifi card is, and put in what the ssid is of the network you're connecting to.

---

### Post by poofyhairguy on 2005-08-16
Look at this wikipage:

[https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29)

---

