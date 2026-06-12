---
title: "Ubuntu sees I have wireless, but can't connect to my network"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by dmorand on 2007-07-15
Ubuntu sees that I have wireless when I go into my network settings. I see that it's setup for Roaming mode. I have a Compaq laptop with a Broadcom 802.11 b/g inside the laptop. When I try to connect to my network it doesn't connect. I'm using WPA-PSK encryption on my router.  Do I need to change it to WEP encryption or anything?  I can use the wired ethernet fine, but I'd rather use my wireless because then I can roam around my house.  

Is there something special I need to do when configuring the wireless settings?  Also, I don't see any wireless networks in range, but in XP I see 7 or 8 at all times.  Does ubuntu not detect wireless networks well or something?

---

### Post by Jamie Jackson on 2007-07-15
Please post the output of:

```
lspci | grep -i broadcom
```

Thanks,
Jamie

---

### Post by dmorand on 2007-07-15
Ok here it is:

03:00.0 Network Controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PIC I card (rev 01)

That means Ubuntu sees it right?

---

### Post by dmorand on 2007-07-15
Here's the steps I take to connect:

1.  Connect to Other Wireless Network
2.  Enter in my network name
Wireless Security: WEP 64/128 bit HEX
Authentication: Open System

I enter in my key from my router, but I don't get a connection

---

### Post by Jamie Jackson on 2007-07-15
Yeah, Ubuntu knows what you've got, but it doesn't know exactly what to do with that card out of the box. 

Assuming you haven't started modifying config files according to other HowTos, etc., [this]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") should work well for you.

Let me know how it goes.

---

### Post by dmorand on 2007-07-15
Thanks Jamie, that guide worked like a charm.  I'm now posting this message from my wireless network!!  Thanks!!!!!!

---

### Post by ConsumingFire783 on 2008-04-01
I'm having the exact same problem with my computer, except a bit of a different hardware setup.  I've got a Gateway MT6456 laptop.
Here's the lspci readout
05:00.0 Ethernet controller:  Marvell Technology Group Ltd Unknown device 2a08. 
 I have the drivers installed through ndiswrapper.  It can detect all the wireless networks in the area, but it can't connect to them.  Sometimes, it will show the full bars as if it is connected, but web pages fail to load.

---

### Post by Jamie Jackson on 2008-04-02
Can you ping google by IP address when it's "connected?"
```
ping 64.233.187.99
```

Or your router?
```
ping 192.168.0.1
``` (or whatever the IP# of your router is.

That would tell you whether it's DHCP or something else.

---

### Post by Crafty Kisses on 2008-04-02
Hmmm, can you get into your Wireless settings?

---

### Post by ConsumingFire783 on 2008-04-02
I tried sending a ping message, it says Destination Host Unreachable.

And yes, I am able to get into my wireless settings.

---

### Post by Jamie Jackson on 2008-04-03
> **ConsumingFire783 said:**
> I tried sending a ping message, it says Destination Host Unreachable.

And yes, I am able to get into my wireless settings.

By "wireless settings" I assume that you mean your router's wireless settings? If so, does the router you're connecting to have an IP address assigned to it? (Indidicating that *it* is connected to your ISP.)

Also, are you able to connect to the Internet when hard-wired to the router?

---

### Post by slolerner on 2008-04-03
dmorand-

i had help w/ a similar issue recently. in a terminal window (under applications>accessories>terminal) type "netstat -rn". you'll see a destination address of all zeros (0.0.0.0).. beside that is a gateway address.. that's the ip jamie asked if you could ping earlier. my apologies if you've already worked past that.

---

### Post by ichi@YUKI on 2008-04-03
I experienced the same thing a few days ago. However, my PC uses an Intel PRO/Wireless 2200BG card. It took me quite a long time to get it to work. The guide I read in the forums had something to do with ndiswrapper, and i remember that the last string of code I used to get it working was:

-sudo modprobe ndiswrapper

At first, I kept on getting fatal errors, but my wireless card managed to work when I tried this code again after reboot. From the threads i've read, the 'iwconfig' output can also be useful. Why don't you try entering 'iwconfig' in your terminal and post the output. :)

---

