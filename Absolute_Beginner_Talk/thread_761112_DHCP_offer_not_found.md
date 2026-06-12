---
title: "DHCP offer not found"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by Argentwyrm on 2008-04-20
New user here. Did a complete install of Ubuntu 7.10, which went smoothly. The problem is, it can see the household wifi, signal strength good (5 bars of 5). I tried manual config, entered WEP key, and cycled many times. No dice. I get DHCP offer not found... then "sleeping."

Interestingly, the drivers were recognized by Ubuntu without issue. 

So I try a direct cable connection. I have a dual-boot laptop that made that swap without any problems, and was online in moments. The desktop can't find anything. Re-enabled the ethernet and still nada. Rebooted, still no Internet.

I went back to the wifi, which at least registers that there's one there. But I'm at a loss. I have read this forum and several others out there, and from what I can tell, it has to do with the WEP versus other types of encryption. 

Does anyone have suggestions for the novice user? Once it's online, I'm set to try several other things, and I really *like* Ubuntu. 

So to recap:  :confused:
eth0 does not find Internet connection by wire
wlan0 reads network but won't allow connection
error for wlan0 reads "No DHCP offer"

Thanks!

---

### Post by hariprs on 2008-04-20
1) Did you try configuring static IP?
2) Is DHCP server working properly in your Wifi?

---

### Post by Argentwyrm on 2008-04-21
Thank you for the reply. I had not configured static IP. Several notes on some help forums indicate that I would have to do that each time I wanted to connect my Ubuntu system. 

I do have DHCP working on the router, and the laptop has no problems at all. It's just the desktop that recognizes wifi signal but won't accept it. I have been to many forums including this one, and gone through some of the how-to guides for internet connection. It's mystifying.

I will use static IP if I must, but since this will be a computer for others in the family, teaching some of them how to config static IP is far more trouble than it's worth, for them. :\

Still pushing for an all-linux household...

---

### Post by sdennie on 2008-04-21
Is it possible that you've configured your router in such a way as to deny DHCP requests from any MAC address that you haven't explicitly enabled?

---

### Post by Argentwyrm on 2008-04-22
I doubt it very much, since it will accept any (other) direct ethernet connection without key, and any other wifi with key. I've brought friends in and they've just plugged in directly, no auth needed. I have added my extended family's comps to wifi just by finding the network and entering the key. 

So... Still stumped except that most of the forums still seem to indicate a hangup around WEP versus WPA.

I'll keep digging into the how-tos. Maybe I missed something. I'm still very, very new to Linux.

---

### Post by bumanie on 2008-04-22
With gutsy, there was an issue in the early days with ipv6 stopping some getting internet connection, including myself. I could only get connection by opening firefox and typing about:config in the address bar. Then type ipv6 in the filter. On the line that appears, right click and then in the drop box, left click toggle to change the value to true. Log out and see what happens.
It may not work, but it's worth a try. You can reverse the process if it doesn't help by following the steps back to toggle and changing the value back to false.

---

### Post by Argentwyrm on 2008-04-22
Not quite working. So close!

I followed the instructions, and yes, ipv6 had been disabled with false value. I enabled it with true. I logged out, then back in, and it was still set at true, but no Internet connection.

Histogram reads strong connection.
IPV6 at TRUE
Passphrase entered (WEP key)
Home page set to easy and fast site (google)
Attempt to resolve page: failed
Passphrase re-entry requested after a few seconds.

Passphrase re-entered. Accepted.
Strong connection to local network.
No connection to web site.
Again, passphrase requested.

*Wonders if there's some kind of auto-reset somewhere that is kicking in, and why*

Thank you for the help thus far, am learning a lot in the process!

---

### Post by schmildo on 2008-04-22
We should forget about the wireless connection if it's giving us grief. Let's get your wired ethernet up and running first, and then we can play with wireless. Its important to determine if the network itself is functional, then we can play with the evils of wireless.

Plug the ethernet cable in, configure whatever networking GUI you have to use the wired connection (usually eth0) for DHCP and go the the console and type:
**. /etc/init.d/networking restart**
Don't forget the '.' at the start.
This will restart all your networking bits and bobs.
Later on, if you want to broadcast a request for an IP via DHCP, but don't want to restart everything, if you go to the console and type:
**dhclient eth0**

you'll get something like this:
> 
**eeepc-schmildo:/home/user>** dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 9380
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Setting lan4 interface ath0 metric to 10
Listening on LPF/eth0/00:1e:8c:7c:dd:f0
Sending on   LPF/eth0/00:1e:8c:7c:dd:f0
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
The  mac address for your eth0 card should be listed.(write it down incase you need it on the router later, and make sure you only have one network interface... yes i've spent hours troubleshooting only to realise i'd plugged it into a different ethernet port)

I always get impatient, if you get as far as 3 broadcasts as I have above, just hold CTRL+C to stop it, because there must be a problem if the DHCP server (your router i presume) hasn't responded yet. If this is your current pickle, then type:
**ifconfig eth0**
and get the current IP address of your network card ( you may need to run dhclient and wait for the program to give up and sleep before this happens). The ip address you'll have will be 169.254.x.x or something, that's just the DHCP client's way of saying "I dunno what address i'm supposed to have so i'll call myself john doe number 1" If you then access the router (make a note of its IP address too) via your laptop and hunt around, you might find (depending on your model) an ARP table, or somesuch, which basicly shows what devices have connected to the router recently. If you do find the ARP table, and it's missing your mac address, then it's possible you'll need to get some linux nerd to help with your network card's drivers. If however you do see your mac address there, then your router is studiously ignoring DHCP requests from your PC, and you'll need to check your router's DHCP configuration/mac address filtering or security.
  If you do manage to get an ip address assigned by DHCP, then you are nearly done. Make yourself feel good by typing:
**ping** *<router's ip address>*
and watch the ping results come in. (CTRL+C to stop them)
Then ping 74.125.19.147 or 203.21.20.20, if that fails then you have a security issue on your router you need fix.
  If pinging those IP addresses works, then:
**ping [www.google.com](www.google.com)**
  If that fails then you have a DNS problem, they are easy to fix too, but i wont go into it here, except to say that if your dns is failing, you can still type IP addreses in your browser, so I always keep one of google's IP's handy, like the one above. (74.125.19.147)

------------

If after all of that your ethernet connection is working then goodo. Restart your PC and check that the connectivity functions on reboot, if not, then make a note of what steps you need to correct it and post them for further assistance.

Rock on brothers.

---

### Post by Argentwyrm on 2008-04-24
It worked! *dances*

The wire finally works, due to the reset command string. I will worry more about the wifi when I have some other things running, but first things first. 

Thank you to all replies, as I learned in the process of setting these things up. The forum is extremely useful and welcoming.

In the future I'll migrate a Dell Inspiron from WinXP to Ubuntu, and that promises to be a bit hairier, so I have a lot of studying to do.

Thanks again!

---

