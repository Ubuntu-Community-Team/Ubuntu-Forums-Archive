---
title: "need help installing buffalo wireless card for x64"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by believeinjake on 2007-06-11
I'm a complete nooby at unbuntu or linux peroid, I have a buffalo wireless card modelg-125 im trying to install on my computer, running unbuntu x64 the controllor has it as a broadcom bcm 4318... not sure what that means...bottom line is it doesnt seem to be working or if it is working i cannot find my wireless network? Is there anything im missing? how can i tell if it is even working at all? is there a package i need to install? thanks.

---

### Post by matthewboh on 2007-06-13
It should be supported with the bcm43xx driver that comes with Feisty Fawn (7.04).  Try going to /etc/network/interfaces file and comment out everything except lo - here's what mine looks like

> auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

Best way to edit the file (because of the security) is to go into a terminal session and type

> sudo gedit /etc/network/interfaces

then use NetworkManager to connect - should be a terminal picture on your applications bar

Good luck

---

### Post by believeinjake on 2007-06-20
This allowed me to even have an option for a wireless connection but still no luck connecting or detecting a wireless network... im using kiwi and it doesnt scan for signals or find any.

i was using windows before this and this card worked fine so that rules out a hardware issue.

any more help would be greatly apprieciated.

---

### Post by matthewboh on 2007-06-22
Okay - could you go ahead and run ```
lspci | grep Network
``` and ```
cat /etc/network/interfaces
``` and post the output?  Also, what version of Ubuntu are your running, are you trying to connect to WEP / WPA?  And I thought Kiwi was a network management tool for Windows - what do you mean by using kiwi?

---

