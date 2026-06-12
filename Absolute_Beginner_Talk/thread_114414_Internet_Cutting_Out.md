---
title: "Internet Cutting Out"
date: 2006-01-08
forum: Absolute Beginner Talk
---

### Post by jbmalone on 2006-01-08
Lately, my internet has just been cutting out at random times.  All of the lights on my modem and router are flashing as normal.  I know the fix to the problem is to just reset the modem and the router then restart, but I don't know.  This seems stupid.  I hate having to restart my computer every single day, especially when I am in the middle of stuff.  Is there anyway to see if Linux is reseting my ethernet card or something that is causing my connection to cut out.

---

### Post by Original Brownster on 2006-01-08
[QUOTE=jbmalone]Lately, my internet has just been cutting out at random times.  All of the lights on my modem and router are flashing as normal.  I know the fix to the problem is to just reset the modem and the router then restart, but I don't know.  This seems stupid.  I hate having to restart my computer every single day, especially when I am in the middle of stuff.  Is there anyway to see if Linux is reseting my ethernet card or something that is causing my connection to cut out.[/QUOTE]

Hi,
Well you could monitor server assigned settings, packets received /transmitted via the 'ifconfig' command. Also 'netstat -rn' shows you routing and gateway info.

looking before and after the problem may shed some light.
Have you changed anything or started using any new piece of software lately? maybe a p2p program?
I had a router that would become overloaded by the number of connections it was trying to handle due to a p2p programs settings. This would freeze and require a reset of the modem, just an idea.

if after resetting the modem / router you cannot connect to the internet and your using server assigned ip / dns for your comp. you could try using the 'dhclient' command to request a new ip. If this works it would surely point to either the modem or router as the culprit.

Regards

---

### Post by jbmalone on 2006-01-08
Thanks for your help.  I am going to take a look at that stuff.  I thought it might have been Firestarter/Azureus so I am going to take a look at it.  I had a similar problem when I was running Windows about 6 months ago, so I'll see.  I think maybe running a certain amout of torrents messes it up.

Jacob

---

### Post by Terry of Astoria on 2006-01-08
I don't think you should have to restart your computer every time you resart the router. It should just pick up where it left off after the router reboots. Unless you have to acquire a new IP address via DHCP, in which case there's a faster way to do it. In the network preferences you can probably do it in gnome, but someone will know the proper command . . . 
   Anyway if you're using azureus, you probably will want to set a static IP for your computer so that you can have the router forward the port azureus uses for bittorrent to your computer's (static, local) IP address (for instance 192.168.1.104). That way your torrents should go faster.

---

