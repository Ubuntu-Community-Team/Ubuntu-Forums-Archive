---
title: "internet connection shareing with firestarter on 7.04"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by 900donuts on 2007-05-13
this has to by my second or third time trying to get help with this
i basically need to know how to share my internet connection on feisty with a windows machine 

my current set up

internet---|dsl modem|---|linux box|----|hub|---|windows box| 

what i have tried
*enabling internet sharing in fire starter
*enabling dhcp(or what ever its called)server in fire starter
*telling the windows box its going through a gate way
at this point i try to make it work
result: the windows box can't establish the connection, fire starter says something about ethx not being ready,and despite the linux box saying it has a connection it cannot access the internet

what have i been doing wrong?:confused: 
how do i make this work?:confused:

---

### Post by Bob535 on 2007-05-16
I'm having the exact same issue.

Firestarter seems to work fine, but as soon as I enable one of my eth connections set with a static ip to share from, my linux box loses its internet connection, although ipconfig still shows it having the same ip.

Setup as such:

Linux 
eth0 - onboard nic - non-functional
eth1 - PCI NIC - Using to share out to LAN
wlan0 - Internet access to the outside world.

Windows XP - just always says network cable unplugged.

I installed firestarter, and as it says in the help file I set up eth1 with a static ip of 192.168.0.1 and subnet of 255.255.255.0 with a blank gateway. 

wlan0 is still just set to dchp.

If eth1 is enabled at boot, or enabled later. The internet will not work until it is disabled and the computer is rebooted. Not even /etc/init.d/networking restart will get it to function after disabling. 

The windows machine at all times just lets me know the cable is unplugged ( checked the cable and it is fine )

Any further information, just ask and I will post.

---

### Post by eks on 2007-06-14
Any of you guys got a solution to your problem?

I'm having the same issue and would be interested in a solution...

Btw, 900donuts, you can try connecting the dsl modem and both computers to the hub, and turn on the DHCP server on the modem. It would be the quickier solution. (Which I can't afford because my modem does not have DHCP server, damn d-link...) :(


eks

---

