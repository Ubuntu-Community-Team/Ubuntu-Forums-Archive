---
title: "my cd for my WiFi card dosnt work on linux"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by Laptop1 on 2007-01-03
my cd for my WiFi card dosnt work on linux so basically am i screwed wifi wise?](*,)

---

### Post by riven0 on 2007-01-03
What's your wireless card model? You may have to install ndiswrapper...

---

### Post by Laptop1 on 2007-01-03
its a belkin model no. fsd7010

---

### Post by riven0 on 2007-01-03
Alright, can you post the results of iwconfig? Go to the terminal, (Applictions >> Accessories >> Terminal), then paste this and give me back the result:

> iwconfig

---

### Post by aberry5555 on 2007-01-03
the easiest way is to type in "sudo synaptic" and bring up the package installer. Then find yourself ndiswrapper. This program "wraps" your windows drivers (the ones on your cd, though you might want the newest ones off of the manufacturer's website) and uses them in linux. Once you have ndiswrapper installed, restart and then run it and look on the cd for a ".inf" file somewhere, or download them from the net. It might be, though, that the manufacturer provides linux drivers online, if so download those and use them, as they will work slightly better than the wrapped version.

---

### Post by davidcourney2002 on 2007-10-21
Belkin Wireless G Card and Ubuntu 6.06
I have a really old Thinkpad that I want to use as a print server

I have a Belkin Wirless G 7010 ver:5100 and I didn't / could find the right .inf file for NDISWRAPPER. 
I am running ubuntu 6.06 and i just did the following:
I went to /etc/modprobe.d/
"sudo vim blacklist"
added "blacklist bcm43xx" to the bottom of the file
I didn't blacklist auth_pci or auth_hal like other posts have suggested.
I tried blacklisting them and it didn't work so i de blacklisted them but left bcm43xx blacklisted.
I restarted the computer and configured the network
I dont know why or how it worked but it did so give it a try
You have to mess with network setting for a while and create a location but then it works on boot.
This took me a whole day to figure out......
__________________

---

