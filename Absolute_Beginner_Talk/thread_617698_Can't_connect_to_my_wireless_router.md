---
title: "Can't connect to my wireless router"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by tartarian on 2007-11-19
Heya!
I've tried looking through a number of threads but none seem to be helping. 
I've just upgraded to gusty and i'm trying to get my wireless working. 
I've installed ndiswrapper and my wireless reciever (belkin FSD7050 usb) seems to be working and recognised. 
When I scan for networks I get all the ones in my immediate area, I just can't seem to connect to them, even when I briefly turn the wep encryption off. 
I've tried using the command 
```

sudo iwconfig wlan0 essid WANADOO-3EB4 ap XX:XX:XX:XX:XX key open 

```
and it doesn't give me any errors , but when I try to ping my router I get: 
```

From 169.254.6.90 icmp_seq=2 Destination Host Unreachable

```

Can anyone suggest what I can do?
Thanks!!!
=]

---

### Post by reckless2k2 on 2007-11-19
try this, change your SSID to something general like "test" or something like that and broadcast it. then turn off WEP or anything other encryption. now reboot and see if you wifi card can detect the network. 

i had an issue with a belkin router/device that was buggy and i had to have the SSID broadcasting. i just set MAC filtering for security and was fine. 

just test the network open to see if you can connect as a process of elimination.

---

### Post by tartarian on 2007-11-19
Thanks for your help :)
I gave that a try and had no luck. The test network came up when I scanned for it, and it worked when I inputed the details with sudo iwconfig but when I tried to ping my router it says the same message. I had a look on my router out of interest and it says that my wireless usb is connected (I compared the hardware adresses)
Argh!!!
So close yet so far lol

---

### Post by reckless2k2 on 2007-11-20
are you able to connect in the gui? i was just wondering why you were using the cli. i think you have to put the mode as well from cli. i haven't done the cli in so long. haha. i do know the last command is sudo ifup to bring the interface up though. if you are getting a 169.xx.xx.xx address to me means you are not connected.

---

### Post by tartarian on 2007-11-20
Yeah I tried using the gui and it didn't work, but I've just put my /etc/network/interfaces file back to default and now the gui's started scanning and picking up my surrounding networks. It just doesn't connect to them :(

I found something really odd though. When I run ifconfig I get three wireless devices when I only have one plugged in. I get wlan0 wlano:ava and wmaster0 (and this one has a ridiculously long hardware address)

And ideas what they are?
Because I get error messages about wmaster0 when i run dhclient wlan0

Thanks :)

---

