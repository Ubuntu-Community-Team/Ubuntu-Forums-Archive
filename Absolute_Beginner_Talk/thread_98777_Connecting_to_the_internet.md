---
title: "Connecting to the internet?"
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by Legoman on 2005-12-04
Okguys i am an absolute newby at linux and ubuntu here, but i dropped i nthe live CD and ran it ubuntu loaded without any probs and i must say very nice looking :D. However i couldnt get it to connect to the net. :( I am connecting through a cable router can anyone help out at all?

---

### Post by heimo on 2005-12-04
To get better understanding of your setup: Is your computer connected to router using network card? Is it configured (System->Administration->Networking). Do you know if it uses DHCP? Run this on terminal (Applications->Accessories->Terminal):
```
sudo dhclient
``` 
Does it "bind" you an ip address? You can check the settings by running ifconfig (on terminal), you should probably see couple devices eth0 and lo, eth0 is your first network interface card and it should have ip address (inet addr)

Please post any additional information you can give us and we'll try to help as well as we can. :)

EDIT: ipconfig -> ifconfig

---

### Post by Legoman on 2005-12-04
ok it doesnt seem to binf me an ip address :( i think i  have done somehting wrong but im going to give it another go :)

---

### Post by Freddie.Ruddick on 2005-12-04
Just for reference, it isn't ipconfig. It's "ifconfig"

---

### Post by Legoman on 2005-12-04
yes it is but i already knew that so thats ok :P

ok i wen into network and set it to DHCP instead of Static ip, and set it as configured, it would not allow me to activate it like this though :(. then i went to the terminal and did a sudo dhclient however this time it came up as this "unable to execute isbin/dhclient: input/output error" any help?

---

### Post by Legoman on 2005-12-04
ok well i found all my settings through ipconfig in windows dns ip and all of that and inputted them it still wont allow me to connect to the internet does anyone have any idea what a search domain is aswell? in configuring the network tools it is under the dns settings?

---

