---
title: "Kismet &amp; ndiswrapper"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by jbrevik on 2007-12-06
Im currently using my NETGEAR WG111T and unfortunately there is no Linux drivers for the device so I was forced to use ndiswrapper. Now I know that Kismet cant be used for devices that have to have ndiswrapper driver management. Is there any other alternatives to use besides kismet? I've tried to run netstumbler in wine but it cant see the device.

---

### Post by daimaru on 2007-12-06
airodump (aircrack suite) or wellenreiter, but i dont know if they will work with your card or ndiswrapper, just get yourself a atheros chip card like a proxim orinoco. thats assuming you want to use packet injection :) the intel based cards work too with a patch

---

### Post by jbrevik on 2007-12-06
The wg111t does use the atheros chipset. Thanks I will try those

---

### Post by daimaru on 2007-12-06
thats weird normally your card should use the "madwifi" drivers automatically if it has atheros chip. well at least mine does, but hey i really dont know that much about it.

---

### Post by daimaru on 2007-12-06
i'm assuming you did edit your kismet.conf file right... entering the madwifi,aht0 stuff ?

---

### Post by jbrevik on 2007-12-06
Yea I did that but when I actually run kismet I get the following output

#FATAL:  Unable to create VAP: Operation not supported
#FATAL:  Unable to create monitor-mode VAP
#WARNING: wlan0 appears to not accept the Madwifi-NG controls. Will attempt to configure it #as a standard Madwifi-old interface. If you are using madwifi-ng, be sure to set the source #interface to the wifiX control interface, NOT athX
#FATAL: Unable to find private ioctl 'get_mode'
#[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}

This is the config entry source line:

**[source=madwifi_b,wlan0,madwifi]**

When I actually modify the source to use the madwifi_ng, I get this output

[B]FATAL: Unknown capture source type 'madwifi_ng' in source 'madwifi_ng,wlan0,madwifi'
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}[/B]

Im wondering if the driver for the wg111t need to actually be there. A driver not used by ndiswrapper.

---

### Post by daimaru on 2007-12-06
EDIT: this only applies if your ifconfig output only lists the ath0 device if you do the command too often you'll have ath1 or ath2 there too, so stop them the same way airmon-ng stop athX etc

i use source as madwifi-ng 
and to set the device into monitor mode you have to use 

```
airmon-ng start wifi0
```as it says with the wifiX thing. if your device already started just type 
```
airmon-ng stop ath0
```that should destroy your wifi0 and ath0 device after that you can reenable it by the airmon-ng start wifi0 option. 

this is what i do to get kismet to run ( i have the same source as you do xept for madwifi-ng, .... ) 
```
airmon-ng stop ath0
ifconfig wifi0 down
airmon-ng start wifi0
```you can use airmon-ng start wifi0 <channel> for a specific channel you want to use.

---

### Post by jbrevik on 2007-12-06
I did try that just now. This is what came out

[B]Interface       Chipset         Driver

wlan0           Unknown         ndiswrapper (MONITOR MODE NOT SUPPORTED)
 (monitor mode disabled)[/B]

I may just have to bite the bullet and get an adapter that can use LINUX drivers and dont have to be configured with ndiswrapper.

Thanks for you help though!!

---

### Post by daimaru on 2007-12-06
[@jbrevik]("http://ubuntuforums.org/member.php?u=448306")
hey dont give up, i really suck at that part (wireless stuff) so maybe someone else here on the forum can help you. but if you want to buy a card that does support monitor mode, tell me, because that was exactly my problem when i was looking for a card to use with kismet and all that stuff. 

edit:
so if it helps i bought a 
proxim orinoco 11b/g gold (model: 8470-WD) 
with packet injection i can crack my WEP in less than 2 minutes.
hope that helps. but there might be way better cards out there, and i only know that this one does work, but not if its really good.

---

### Post by jbrevik on 2007-12-06
Did some research and found out that eventhough the wg111t uses the atheros chipset, monitor mode is not supported for the usb adapters. There are driver patches available for the wg111t v1 but not for the wg111t v2, which is what I have. 

There is a bright side to this though. I've been running Ubuntu for almost 2 years now, and this is the first driver issue I have come across. Amazing!!!

Cheers!!

---

### Post by daimaru on 2007-12-06
nice to hear that you had so little trouble, but if you do want to use that monitor mode and i am assuming that you want to crack your neigbours wep key (no of course your own) than you will have to get a new card.  i can only say its fun :)

---

