---
title: "New Modem problems w Comcast"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by texastrey1836 on 2007-12-27
I am absolutely green on all of this stuff, but before my "upgrade" with Comcast, I was running cable internet, through my linksys wrt54g, and was having no problem whatsoever. Today, the "technician" showed up and hooked up a new modem (with VoIP) and now I get no internet at ALL on my desktop, which runs Ubuntu Gutsy Gibbon. 
I spoke with Comcast and they were no help; I called Linksys, and they wouldn't help; then I called Comcast back, and one of their techs tried for over an hour to try to get it to work. Nothing worked. Does anyone have any ideas?
We tried:
Setting the network to DHCP.
We pinged and got no response.
I've been trying to get the internet without the router, just straight into the desktop.
I do have internet, because the cable works fine on my Apple laptop. It's the desktop with Ubuntu that won't work.
Thanks.
Trey

---

### Post by spiderbatdad on 2007-12-27
try:  ```
sudo dhclient eth1
```  please. assuming you have ethernet cable plugged in.

---

### Post by wormser on 2007-12-27
Are you still using the WRT54G router?  You should leave it in why we trouble shoot.  First shutdown your computer fully.  Then start it and try the following commands.  Post what happens on each.

```
ifconfig
```
```
sudo dhclient
``` 
```
ping 192.168.1.1  (router's address)
```
```
ping 4.2.2.2
```
```
ping google.com
```

---

### Post by russell.h on 2007-12-27
Are you connecting via wireless or wired?

---

### Post by texastrey1836 on 2007-12-30
OK Here goes. Sorry it took a couple of days to get back on, and thanks for everyone's help.

**sudo dhclient eth0**: couldn't find it

**ifconfig**
eth0   link encap: ethernet HWaddr 00:07:E9:4F:80:92
inet addr:192.168.1.104 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::207:e9ff:4e4f:8092/64 Scope: Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets: 103
TX Packets:153 (No errors, dropped, overruns,etc.)
colleisions: 0 txqueuelen: 1000
RX bytes:12104 (11.8 KB) TX bytes: 20356

lo:ink encap: local loopback
inet adr:127.0.0.1 mask:255.0.0.0
inet6 addr:::1/128 Scope Host
UP RUNNING LOOPBACK MTU:16436 Metric :1
RX packets: 0
TX Packets:0
RX bytes 0 TX bytes 0

**sudo dhclient**:there is already a pid file/var/run/dhclient.pid with pid 5823
killed old client process, removed PID file

**Pings**: To router were good
To 4.1.1.1: No return
To google.com No return

Trey

---

### Post by wormser on 2007-12-30
It looks like you are getting a DHCP ip address from the router and can ping the router.  Try putting the router's IP address in Firefox.  Are you able to log in?  If you can then the problem seems to be with the router.  If that is the case then I would recommend resetting the router.  Unplug the cable modem, reset the router (in the back, hold down for 10 seconds) plus unplug it and turn off your computer.  Then plug the cable modem back in, the router and turn your computer back on.  Post your results and we can go from there.

---

### Post by texastrey1836 on 2007-12-30
I did reset the router, but now i can't even get to the login page. i've got an ip address, but no broadcast address, subnet, default, etc. i'm on tech support with linksys right now
Trey

---

### Post by texastrey1836 on 2007-12-30
OK. I was online (with my laptop) and was able to reset all the settings in my linksys router. I'm still getting absolutely nothing on the desktop with ubuntu. I'm so beyond frustrated right now. Everything was working fine until I decided to "upgrade" to a new internet/phone/cable bundle, just trying to save money. Then the tech decided to completely destroy everthing. Ugh.
Trey

---

### Post by wormser on 2007-12-30
I take it that you still cannot ping via ip and domain or access the router's admin page in Firefox.

Did you reset the router by pressing the reset button in the back?  Try setting up a static ip address.  Use 192.168.1.99 or any IP that will be out of your DHCP range.  Just click on the network icon in the notification area> manual configuration> highlight Wired connection> Properties> uncheck Enable roaming mode and enter in the detail.

---

### Post by Bufke on 2007-12-30
I had the exact same problem with Comcast when I got voip.  Just call them and explain the problem, they will do something and then it will work.  I don't know what the problem is but it must be something with them.  I'm not pleased at all with Comcast, they forgot to install the voip modem battery and just left their junk all over my basement.

---

### Post by texastrey1836 on 2008-01-02
Here's an update:
I tried changing the IP address and there was no joy on that front. I'm currently on hold with Comcast trying to fix the problem, but I dont hold out much hope. The wireless router is working, as I am able to use it to print wirelessly through my Apple laptop. I'm about to chuck the whole system and start over from scratch. This is driving me bonkers.
Trey

---

### Post by Lynn Scott on 2008-05-14
So who or what department did you contact at comcast?  I contacted them via a live chat session and there response was that they don't support Linux and I couldn't get past there.

---

### Post by Lynn Scott on 2008-05-15
So I got a hold of someone at Comcast who helped.  The formal answer is Comcast does not support Linux.  The tech on the phone did give me the following solution.  Given the following:

1.  Comcast cable modem with voice (voip), cable, and internet.
2.  A Linksys 4 port router with wireless support connected to the cable modem.
3.  A Ubuntu Linux box wired connected to the Linksys router and not able to obtain a DHCP address.

Solution:

1.  Leave everything connected (not imparative).  
2.  Shutdown the Ubuntu box.
3.  Unplug the power from the Linksys router.
4.  On the back of the cable modem, find the reset switch (by the ethernet port) and press it until the cable modem resets.
5.  Wait for all the green lights to come back on.  All except the data link light will come back on.
7.  Plug the Linksys router's power back on.
8.  Start the Ubunut system.

The above steps worked for me after trying everything else I could think of.

---

