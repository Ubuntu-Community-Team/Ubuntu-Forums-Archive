---
title: "internet connection issues"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by nightfyre on 2007-04-24
ok, might as well bring up my second issue since i'm on. i'm using a gateway solo 5300 laptop and i can't connect to the internet. ubuntu recognizes the ethernet card, but it still won't connect. i'm guessing that i need to configure something in the connection settings, but what? i use a lan connection to access internet on my other computer, by the way.

---

### Post by Bachstelze on 2007-04-24
How is the connection configured on that other computer (static IP or DHCP) ?

---

### Post by nightfyre on 2007-04-24
static. i use earthlink, if that means anything.

---

### Post by Bachstelze on 2007-04-24
Then you need to configure it the same way in Ubuntu. Either with *ifconfig* in the command line or with whatever GUI tool Ubuntu has.

---

### Post by johnc4510 on 2007-04-24
Gui here:

System>Administration>Networking

Click on Properties, I think

---

### Post by nightfyre on 2007-04-24
ok, i'm in the settings. i found the ip adress, but i can't find the subnet mask or gateway address. where would i find those?

---

### Post by nightfyre on 2007-04-24
whoops, its dhcp. still, that let me get the ip address in, so that works. lemme check if the connection is good.

---

### Post by nightfyre on 2007-04-24
no good, still can't connect. i have the ip, subnet, and gateway all entered in.

---

### Post by tarpon_bill on 2007-04-24
You are in the right spot, you just need to make sure that the settings are identical to the computer you took out. Try a reboot and then go back to the network-properties dialog and make sure it shows "static" and the right values are entered in the manual fields.

---

### Post by nightfyre on 2007-04-24
everything's correct, but i still can't connect. does the fact that my modem was supplied by my service provider mean that the modem might be the problem? if i bypass the modem, do i have to use dialup?

---

### Post by oilchangeguy on 2007-04-24
just a thought on the modem. have you reset it since you installed ubuntu on your computer? by reset i mean turning it off, wait about 10 seconds and turn it back on. also reboot the computer. and you should be able to get online.

---

### Post by nightfyre on 2007-04-24
actually, i'd always connected to the internet with my desktop; ubuntu is on my laptop. i'll try that though.

---

### Post by nightfyre on 2007-04-24
hmmm... my modem's ethernet link light didn't even come on. apparently the connection isn't properly established. any ideas?

---

### Post by nightfyre on 2007-04-25
is there any reason why my ethernet connection would not recognize my laptop even after entering in all the settings? linux does recognize my ethernet card, so the card is not the problem.

---

### Post by oilchangeguy on 2007-04-25
if your modems lights do not appear normal, it has nothing to do with the computer. have you checked with your isp?

---

### Post by nightfyre on 2007-04-25
not yet. by that, do you mean maybe they don't support ubuntu/ my hardware? i hadn't looked at it from that angle before.

---

### Post by oilchangeguy on 2007-04-25
your isp doesn't care what os you use. maybe they are having problems in your area. maybe your modem died.

---

### Post by nightfyre on 2007-04-25
modem is definitely not dead; i'm using it right now. this is not my linux computer i'm typing on, by the way.

---

### Post by oilchangeguy on 2007-04-25
have you tried what i suggested in post #11?

---

### Post by nightfyre on 2007-04-25
yeah, no good. sorry for the hassle, this isn't exactly my area of expertise.

---

### Post by nightfyre on 2007-04-25
just in case anyone asks, yes, connect to internet through modem and use modem are enabled

---

### Post by nightfyre on 2007-04-25
please, i really want to get my laptop up and running...

---

