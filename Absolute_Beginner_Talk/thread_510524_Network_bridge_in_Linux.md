---
title: "Network bridge in Linux"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by fidde88pven on 2007-07-26
Hello!

Im using ubuntu 6.10 to make a Network bridge.


Its like this, (the cards are found and working) I want computers behind my eth0 to access internet/network trough wlan0, but I cant get it to work, tried bridge-utils and stuff... Should the cards have static or DHCP ip?

BTW I would like the computers behind the eth0 to get their ip from my router on the other side of wlan0, is this possible?

Thanks if anyone can help me...

---

### Post by mattze on 2007-07-26
hey,

my setup is just the other way but perhaps it works nervertheless.

my desktop-pc is connected via cable to my laptop, which works as a gateway to my internet router.

what i did is install ipmasq and dnsmasq and then use firestarter to share the internet connection. (it's just a iptables frontend)
it looks like this:

desktop:                                                 
ip: 192.168.2.34 (static)                                                         
gateway: 192.168.2.7        
     |
cable
     |
laptop:
192.168.2.7 (static)
192.168.3.100 (dhcp) 
    |
wireless
    |
router
in case anyone wonders why i do this: my desktop-pc has no WPA support.

does this help you?

---

### Post by fidde88pven on 2007-07-27
Thanks i will try that... But doing it with BRCTL is a little more... My way... Does firestarter let through all traffic? Like network etc...

If somesone wants to help me more ive done a picture that shows what i want to get...

[IMG]http://dvab.flum.be/Helpme.jpg[/IMG]


thanks MVH fredrik

---

