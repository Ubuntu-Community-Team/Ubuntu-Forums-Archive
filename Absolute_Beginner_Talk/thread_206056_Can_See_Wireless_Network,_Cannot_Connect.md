---
title: "Can See Wireless Network, Cannot Connect"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by shoot2kill on 2006-06-29
hey.. i had trouble configuring my wirelesss network card, but after following a few tutorials, i got it working, i can now see other networks...

however, after entering the correct network keys... etc.. i cannot connect...

it says connecting for bout 20 seconds, then says connection failed.. please help

---

### Post by x64Jimbo on 2006-06-29
More information is needed. Tell us about your network. Are you using WEP, WPA, WPA-PSK, or WPA2? If it's WEP, how many bits of encryption? Do you have your router set to "shared" instead of "open" authentication? That last one's a doozie. I'd recommend looking into that first.

---

### Post by shoot2kill on 2006-06-29
im new to all of this networking....

i am using 128 bit WEP on my router with ASCII password...
not sure about ubuntu, it just says network WEP - shared key.. (dont know about bit)

my network is just a PC running ubuntu, conected Ethernet to Router, which is connected to internet... my laptop (this system) wants to be wireless to the router...

both router and laptop are set to shared key (dont know what this means)

need anymore info?

thanks

---

### Post by shoot2kill on 2006-06-29
**bump**

---

### Post by ovimunt on 2006-06-29
Hi,

First of all, what computer have you got and what WiFi card? This question is not vital so I'll try to help you out but I might get it wrong. 

Anyway, in Ubuntu right click on your network icon and choose Properties. In the window that opens click on Configure. Now you should see the list of your network adapters. Check if your wireless adapter is active. If so, click on Deactivate then on Properties.

A new window will open where you need to fill in your network details.

*Network name (ESSID)*    This is self explanatory.
*Key type*                           Click on the tab and you should be able to choose     between ASCII and Hexadecimal. In your case choose ASCII.
*WEP Key*                           Type in your key.

*Configuration*                    I suppose your network is set for DHCP (Dynamic Host Configuration Protocol) so choose this option from the tab.

Now click on OK and Activate your wireless. This should sort it out.

 If this doesn't work I think I know the problem but I will need more details about your configuration before I can help further.

---

### Post by topcat37 on 2006-06-29
I have to use an open network to connect. Any wep or wpa and my laptop won't connect. I've only been using ubuntu for 2 weeks and it's great, but I know there are a few bugs. Wep and Wpa seem to be among them. I'm sure i'll get it fixed eventually.   Here is a  good place to start : [http://www.ubuntuforums.org/showthread.php?t=125150](http://www.ubuntuforums.org/showthread.php?t=125150)   this thread might help you.   Good Luck!

---

### Post by shoot2kill on 2006-06-29
[QUOTE=ovimunt]Hi,

First of all, what computer have you got and what WiFi card? This question is not vital so I'll try to help you out but I might get it wrong. 

Anyway, in Ubuntu right click on your network icon and choose Properties. In the window that opens click on Configure. Now you should see the list of your network adapters. Check if your wireless adapter is active. If so, click on Deactivate then on Properties.

A new window will open where you need to fill in your network details.

*Network name (ESSID)*    This is self explanatory.
*Key type*                           Click on the tab and you should be able to choose     between ASCII and Hexadecimal. In your case choose ASCII.
*WEP Key*                           Type in your key.

*Configuration*                    I suppose your network is set for DHCP (Dynamic Host Configuration Protocol) so choose this option from the tab.

Now click on OK and Activate your wireless. This should sort it out.

 If this doesn't work I think I know the problem but I will need more details about your configuration before I can help further.[/QUOTE]

LOL.. done all that, a few times... still not working...

for the other ost, them drivers on that page are for a different card

my compputer is a Comaq Presario R3000 with Broadcom Wireless Card

---

### Post by ovimunt on 2006-06-29
No need to LOL, just tryin' to help. If you don't need it then don't ask questions, ok?

Is your Broadcom a 4318?

I know there are 2 way to install this card so did you use the WIN64 driver on *ndiswrapper* of did you get the firmware for the Ubuntu native Broadcom driver?

---

### Post by shoot2kill on 2006-06-29
[QUOTE=ovimunt]No need to LOL, just tryin' to help. If you don't need it then don't ask questions, ok?

Is your Broadcom a 4318?

I know there are 2 way to install this card so did you use the WIN64 driver on *ndiswrapper* of did you get the firmware for the Ubuntu native Broadcom driver?[/QUOTE]

the LOL was nothing to do with ur help, just the thought of changing all the settings again... i am more than grateful for your help, believe me..

my card is a Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)

to install the driver i followed the info on guide that didnt use ndiswrapper (beause i tried this and didnt work) but i not too sure which other method i used...

just to clarify, i can see the networks,just cannot connect to them... thats why i thought it might be something to do with the authentiation, but linux wont let me disable authentication to test it...


Thanks again for your help up to now....

---

### Post by shoot2kill on 2006-06-29
bump (small bump) :)

---

### Post by ovimunt on 2006-06-29
Well.. you might have tried this already but I can't think of something else right now. This involves the command line and a bit of trial and error.

In the terminal type

***iwconfig***

This should give you the list of your network devices. See if you note anything strange there. Check to see which interface you wireless is i.e. ***eth***X or ***wan***X where X is a number.

Now there is a way to try and force your card to connect to a certain wireless access point.

***iwlist ethX scan***

Where ***ethX*** is the actual name of the WiFi device. This should give you the list of all the networks in range and, more important the MAC address of each of the gateways. Look for you network and make a note of the ***Address*** i.e. the XX:XX:XX:XX:XX:XX hexadecimal number. This is the MAC address of your router.

Now deactivate your WiFi

***sudo ifdown ethX***

Configure your network settings manualy:

[I][B]sudo iwconfig ethX essid "Your network ESSID"
sudo iwconfig ethX mode Ad-Hoc
sudo iwconfig ethX enc off
sudo iwconfig ethX key restricted 
sudo iwconfig ethX key s:your_ASCII_key
sudo iwconfig ethX enc on
sudo iwconfig ethX ap XX:XX:XX:XX:XX:XX[/B][/I]

Where XX:XX:XX:XX:XX:XX is the MAC address of your router.

Now reactivate your WiFi

***sudo ifup ethX***

This might sort it out. If it still doesn't work then try this again but replace the line

***sudo iwconfig ethX ap XX:XX:XX:XX:XX:XX***

with

***sudo iwconfig ethX ap auto***

or

***sudo iwconfig ethX ap off***


If you still have no luck then type

***man iwconfig***

and have a good read through the manual of ***iwconfig***. Then do a bit of trial and error of your own like disabling the encription, etc.

Good luck and let me know if it worked.

---

### Post by shoot2kill on 2006-06-29
nope nothing.. same again.. and the manual was just BLAH BLAH BLAH...

i dont know if this will mean anything but on the **iwconfig**, all details were alright, xept signal strenght and signal detals wer all 0.00

but it finds the router, just cannot conect...

any way of disableing the authentication..?

---

### Post by ovimunt on 2006-06-29
[QUOTE=shoot2kill]any way of disableing the authentication..?[/QUOTE]

Well... this should do it

> sudo iwconfig enc off
sudo iwconfig key open

This disables the encription and tells the wireless that the network is open, i.e. anyone with/without a key can connect. This is pretty much equivalent with disabling authentification.

Yet, you were saying someting about signal strength being zero... Are you sure that it doesn't also say something like this.

> 
eth0      IEEE 802.11b/g  ESSID:"Ender"  Nickname:"Broadcom 4318"
             Mode:Managed  Frequency=2.442 GHz  Access Point: ***Invalid***


I am particularly refering to the ***Access Point: Invalid*** part.

---

### Post by Gaute65 on 2006-06-29
[QUOTE=shoot2kill]bump (small bump) :)[/QUOTE]


Have you read [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")?

---

### Post by ovimunt on 2006-06-29
My wireless works so... Nope, haven't read that page yet. I did bookmark it though, might come in handy, you never know. :wink:

---

### Post by shoot2kill on 2006-06-30
hi.. about the "access point invalid".. no it actually says...
> Mode:Managed  Frequency:2.462 GHz  Access point: Not-Associated

still need help.. :(

also the enc off and key open, didnt work, i get message

unrecognised wireless request "off"
unrecognised wireless request "open"

---

### Post by shoot2kill on 2006-06-30
OMG... dont ask me how, but i have sorted it.. i was just going over older posts ^ ^ ^ and entered all of the details again, and it worked... 

sorry, dont know what i did to get it working.. :( but it working anyway.... :)

thanks again to evryone who helped me....

--i happy now--

---

### Post by Shaymus22 on 2007-04-05
> **ovimunt said:**
> Well... this should do it



This disables the encription and tells the wireless that the network is open, i.e. anyone with/without a key can connect. This is pretty much equivalent with disabling authentification.

Yet, you were saying someting about signal strength being zero... Are you sure that it doesn't also say something like this.



I am particularly refering to the ***Access Point: Invalid*** part.

Mine says that the Access Point is invalid!  Besides that, all of the details of my problem are exactly the same as that of the starter of this thread...I even have a BCM4303 802.11b Wireless LAN!  I'm running 6.06 if that helps at all.

---

### Post by Shaymus22 on 2007-04-05
bump for great justice

---

