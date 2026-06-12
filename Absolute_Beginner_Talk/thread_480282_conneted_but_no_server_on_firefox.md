---
title: "conneted but no server on firefox"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by craig anderson on 2007-06-21
basically my ubuntu operating system says that am conneted thro wireless but wean I click on firefox it says server not found ](*,)

---

### Post by EagleRock on 2007-06-21
That could be as a result of many issues.  Have you checked your Internet connection through another computer to see if it's a problem with the router?

Also, when you click on the Network Manager, are you connected to the right wireless network?

---

### Post by craig anderson on 2007-06-21
theres 3 computers in total at my house 2 of them have windows and 1 of them ubuntu (of course) both window computers work fine with no problems at all. And am defintly on the right network (btvoyager2100-d9) is the network ESSID

---

### Post by craig anderson on 2007-06-21
Bump

---

### Post by zero-9376 on 2007-06-21
what does connection information say, this can happen if your computer isnt getting an address from the network but is connected to the network. im pretty sure network-manager will assign a 169.x.x.x address in this case which is the same as windows limited connectivity thing.
also did you enter the essid manually or from the list, on my laptop i had to connect manually and it would then 'connect' to the network, even if the router wasn't on. i ended up unhiding my essid and switching to wpa.

---

### Post by stalker145 on 2007-06-21
I'm assuming that you don't have any sort of MAC filtering or IP reservation set up in your router... That's usually my problem. I forget that I have all that junk set up.

---

### Post by craig anderson on 2007-06-21
did a (sudo iwlist scan) in terminal and this is what came up

lo       interface doesn't support scanning

etho  interface doesn't support scanning

ra0    scan completed



                        cell 01


                        cell 02

---

### Post by craig anderson on 2007-06-22
bump

---

### Post by craig anderson on 2007-06-22
bump again

---

### Post by craig anderson on 2007-06-22
but seriously tho what do I do to fix the problem because I cilick on the 2 moniters an the top right of the screen and I then have a list of networks to choose from and wean I cilick on my network the icon changes to 2 balls and some whizzy thing going round and round and then it goes back to 2 moniters with a exclamation mark next to it 

what do I do to fix this :confused:

---

### Post by PartisanEntity on 2007-06-22
You never answered whether you use any kind of encryption or MAC address filtering on your router, it would really help if you could let us know.

---

### Post by zero-9376 on 2007-06-22
it doesnt appear as though your card is seeing your network, is your essid hidden? as I asked previously did you manually enter the essid when you were attempting to connect?

this is what i get when i do a scan

sudo iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:01:36:0A:74:C2
                    ESSID:"MYWLAN"
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Quality=54/94  Signal level=-41 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 

as you can see it gives a lot more information. perhaps you should at provide the output of lspci and we may be able to point you in the right direction for your specific card.

btw. if you are using a usb wireless the command is lsusb

---

### Post by craig anderson on 2007-06-22
:oops:

sorry

I don't have any encryption at all on my router

---

### Post by zero-9376 on 2007-06-22
if you right click on the 2 monitors and go to connection information it will tell you an address, also if you try and get an address from the command line using

sudo dhclient ra0 

on my network, if the router is out of addresses (i limit the number as a security measure) i get a DHNACK or something and no address. also can you provide the output of the command 

iwconfig

---

### Post by craig anderson on 2007-06-22
(sudo iwlist scan)

ra1              scan completed   :
                   Cell 01 -  address:  00:11::F5:04:49:D9
                   ESSID: "BTVOYAGER2100-D9"
                   Mode: Managed
                   Channel: 1
                   Encryption key: off
                   Quality:54/100     Signal level: -50 dmb  Noise level 256:  dbm

---

### Post by zero-9376 on 2007-06-22
ok what about iwconfig? can you connect to the network using network manager and then run iwconfig

are you familiar with setting up routers and networking?
if you would prefer i could continue to try and help you through IRC which may be a bit quicker?

---

### Post by quinnten83 on 2007-06-22
Check to see if you can get on any other wireless network, 
setup up your wireless without roaming by going to system, administration network. See if that works.
if not try to install wlassistant and check if that works?
I know that the first time I had to chose a network I had to insert it first into the network manager.

---

### Post by craig anderson on 2007-06-22
> **zero-9376 said:**
> ok what about iwconfig? can you connect to the network using network manager and then run iwconfig

are you familiar with setting up routers and networking?
if you would prefer i could continue to try and help you through IRC which may be a bit quicker?

whats IRC

---

### Post by craig anderson on 2007-06-22
> **quinnten83 said:**
> Check to see if you can get on any other wireless network, 
setup up your wireless without roaming by going to system, administration network. See if that works.
if not try to install wlassistant and check if that works?
I know that the first time I had to chose a network I had to insert it first into the network manager.

did what you said and gess what






[SIZE="7"]IT WORKS!!![/SIZE]

---

