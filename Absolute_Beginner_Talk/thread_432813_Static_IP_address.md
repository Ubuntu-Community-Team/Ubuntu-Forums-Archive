---
title: "Static IP address?"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by DrtBikDave on 2007-05-04
How do you set up a static IP address in Feisty. I am doing it for utorrent.

---

### Post by vanadium on 2007-05-04
Network Icon - Manual configuration. However, whether you can have a static IP address depends on your provider. If you have an internet account whith a static IP, then you will have obtained your IP number from your provider.

---

### Post by dannyboy79 on 2007-05-04
first, go to a terminal and type in

ifconfig -a

and jot down the ip address

(if you don't have a router I am not sure what to tell you to put for the gateway? you might need to call your isp?

then go to 

system, admin, networking
and then click on the interface that you want to make static. and fill in the blanks. you will need to know your dns servers ip addresses IF you have a router which doesn't properly forward dns requests. BUT first just try to only fill in the static ip you would like to use, then fill in the net mask with 255.255.255.0 and put the ip address of your router for the gateway OR get the gateway from your ISP?

and that's it.

OR, there is another way IF you have a router which can "reserve" an IP address for a certain MAC address. It'll be within the administration for your router if you have one. Look for static dhcp settings or MAC address or IP address reservation. sometimes it's under the "attached devices" section, you should see the ip that you ubuntu has currently, then look for a place to tell the router to always give that ip to that computer everytime. and this way it will always receive the same ip from the router.

---

### Post by Linux_oid on 2007-05-04
**GUI configuration**

System>Administration>Network>

Ubuntu starts 'network admin' task, asks password for administration task, opens 'Network Setting' window.

'Network Setting' lists all your networks 'Connections' (Wireless, Wired, Modem over here). 
Highlight 'Connection' you need to configure and click 'Properties'.
Now you should have 'Setting for interface  eth0 (can be ath0 or ppo0)' window opens.
'Connection Setting'>Select 'Static IP address' and manually enter 'IP address:', 'Subnet mask:', and 'Gateway address:'.
Click OK. 
Make sure: 
1.  'Network Setting'>'General'>has   'Host name:' and 'Domain name:' information.
2.  'Network Setting'>'DNS'>has 'DNS servers' address(s) entered.
Click 'Close'.

That's it.

---

### Post by SyL on 2007-05-04
Either you want a IP static for your local network (you need it for create a rule, port mapping in your local network  ...), then like vanadium said just you can configure it through the network config GUI.
Or you want a IP static for your internet connection, then there is some free dynamic DNS provider like [http://www.dyndns.com/](http://www.dyndns.com/)

---

### Post by DrtBikDave on 2007-05-05
Ok, Feeling a little dumb here. First of all My router is a Linksys (WRT54G) I am hooked up through an Intel gigabyte ethernet connection Built into my motherboard. I have this set up in windows XP. Will I be able to configure my network settings to work through the same port or should I open another port?

---

### Post by SyL on 2007-05-05
> **DrtBikDave said:**
> Ok, Feeling a little dumb here. First of all My router is a Linksys (WRT54G) I am hooked up through an Intel gigabyte ethernet connection Built into my motherboard. I have this set up in windows XP. Will I be able to configure my network settings to work through the same port or should I open another port?

Not sure to understand what you mean.
Do you want to map a port from your router to your desktop in order to use torrent properly?
If so you just have configure your local IP (of your desktop) as static and add a rule in your router (all request coming to this port are going tothisstaticip:onthesameport).

Hope that i get it right.

---

### Post by DrtBikDave on 2007-05-05
OK thanks guys, I finally got it. The only thing that was being left out by your suggestions was To add a ip address and a alias under the host tab in my network settings.

---

### Post by dannyboy79 on 2007-05-07
> **DrtBikDave said:**
> OK thanks guys, I finally got it. The only thing that was being left out by your suggestions was To add a ip address and a alias under the host tab in my network settings.

You asked us how to make a static IP, I specifically state, 

"and jot down the ip address

(if you don't have a router I am not sure what to tell you to put for the gateway? you might need to call your isp?

then go to 

system, admin, networking
and then click on the interface that you want to make static. and fill in the blanks"

and then you say I forgot to tell you that you needed to fill in the IP. WOW, that's being pretty ungrateful!! Should we have to tell you to wipe your ___   after you use the bathroom? I suggest next time you be a little more appreciative instead of saying something that just isn't true. Also, the alias isn't required, it's merely an option. Glad you got it working.

---

### Post by orbister on 2007-11-04
I think that's a little mean. You told him to fill in the IP address in the connection info, but he's now talking about entering it under the hosts tab. Which is completely different.

---

