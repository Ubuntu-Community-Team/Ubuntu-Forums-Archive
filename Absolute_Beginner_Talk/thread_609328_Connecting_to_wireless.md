---
title: "Connecting to wireless"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by WillW on 2007-11-10
I have recently installed 7.1 on my Dell 1501. I do not know how to connect to wireless through Linux, as this is my first time ever using it. I see that people are having all sorts of troubles with wireless and some people connect flawlessly. I would like to assume that everything is working fine and that I just do not know how to use Ubuntu yet. 
I saw on another posting that to connect to wireless one would go to the administrative menu and select networks. Here I am led to a window that has the three options for connecting, wireless, wired and modem. When I click on the wireless icon it gives me the four tabs. Under one of these tabs I can see where the wireless network I am trying to connect to is displayed. When I click on it it asks me for the IP address. There is an IP address listed next to the network name so I try entering that one and then it asks me for an alias before I can click ok. I enter the name of the coffee shop and click ok, but I am not connected to the network. I have ran through this procedure over and over and no where do I see a button that says CONNECT. 
Am I missing something here, I am only used to Windows environment. I would like to think that everything is working fine and I just don't know how to connect. 
Thanks in advance for any advice.

---

### Post by SpiritIsReality on 2007-11-10
howdy
I'm not much good at wireless but I try to follow along,

try these
lspci
sudo lshw -C network
dmesg | grep eth
that's a shift key and \ key for the | between dmesg and grep eth.
in the terminal one at a time and then post the info here so guys in the know can have a 
look at it.
That is, Applications > Accessories > Terminal
type in lspci and tap enter key.. Copy and paste that into a post here.
same routine with the next two. Somebody might ask you to run others, or ?
What those commands do is tell us if the wireless chip is recognized, and if so, what it is.
I'm probably missing a command or two. But we can walk along.
trails

---

### Post by Pioneer5000 on 2007-11-10
Go   System --> Administration --> Restricted Drivers
Update the drivers or make sure they are enabled one should be called something like Firmware for Broadcom thats the one you need to make sure is on. If you can connect to the net through ethernet/ usb for a while then do so as you will need to d/l a file for the driver once you have d/l this file it should activate the wifi. You will need to reboot. After rebooting make sure the icon at the top right says you are connected to wireless if not click on that icon and then select the wireless connection and hopefully it should work. I have the same laptop as you Dell Inspiron 1501 and thats all i did to get it working update the Firmware for Broadcom thing then reboot and then click on the connection icon in the top right and then select your wireless connection and it should work.


Good Luck.

---

### Post by Giradman on 2007-11-10
**Will W.** - I'm 'brand new' to Ubuntu (running on an older IBM laptop w/ wireless) - after installing the OS, it connected w/ my 'wireless' router immediately (I was actually astounded!); now on a weekend trip to the NC mountains @ a resort that offers 'wireless' in the room - but I followed the same steps that you discussed; first I went to the same 'Network Settings' window mentioned and unchecked the 'wireless' box indicating my home network - once done, I clicked on 'Properties', enabled roaming, and set the DHCP to automatic - suddenly the 'local' network was found and functioned - still being new to this OS, I'm not sure exactly if this is the right way to approach this situation but it did work w/o  goin' into the Shell, which I still need to learn much more about - give it a try - can't do any harm - good luck! :)

---

