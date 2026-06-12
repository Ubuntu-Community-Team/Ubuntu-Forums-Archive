---
title: "Having trouble with DHCP and wifi? Try this"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by --chris-- on 2006-11-29
I'm a new Ubuntu user and I recently installed Edgy. I was having some problems connecting via wifi. A friend of mine told me about this workaround. While it didn't answer all my wireless problems it at least got me up and running quickly.

PLEASE NOTE: It is recommended to use a supported wireless card. I started with an unsupported one and it didn't go as well. I'm using a D-Link DWL-650+. 

THE PROBLEM: Wifi would not pull down a DHCP address. Would associate with the WAP but no packets were being received. 

The workaround? Bring down the LAN interface prior to you using your wifi card. 

Make sure a profile for your wifi card is configured and ready to go. You can do this by going to System -> Administration -> Networking, highlighting your wifi card and choosing properties. make sure the card is listed as enabled. 

Bring up a terminal session via Applications -> Accesories -> Terminal. 

Type the following commands. (Please note that SUDO will ask for your password prior to executing them.)

sudo ifdown eth0 (assuming your interface is eth0) 

Then bring down your wireless card 

sudo ifdown wlan0 (assuming your wlan interface is wlan0)

Once completed bring your wireless card back up again by typing

sudo ifup wlan0 

Voila! Instant DHCP address. It appears that my LAN interface is somehow interfering with wifi communications even when the connection is not active. 

CAVEAT: I had to disable WPA on my WAP to make this happen! I still haven't figured out how to make this work with an encrypted connection. So use at your own risk as you transmissions will be in the clear!

---

