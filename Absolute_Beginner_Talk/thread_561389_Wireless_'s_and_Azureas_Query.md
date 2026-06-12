---
title: "Wireless ?'s and Azureas Query"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by MysticEdge on 2007-09-27
Hullo there folks? How is everyone doing today.

Two quick questions.

First of all, I am running a Netgear WG511T Wireless internet adapter, I have the latest drivers for it from Netgear, however they are in .exe format. I should mention that at the moment Linux is running the AR5212 802.11abg NIC drivers for this card, and they are working to a certain extent. However I'm not getting any signals over 50% even when the wireless router is within inches of the laptop.

With that said, I figured one solution to the problem might be to install the proper drivers from Netgear. So I downloaded the exe, extracted the inf, placed it into a Ndiswrapper Driver folder in my Home folder, and then I ran the Windows Wireless Drivers application under the System>Administration tab, and selected the INF file from the netgear drivers folder, and when I try to install them it says that the hardware is not present. Could this be because Linux already identified it, and is running what it thinks are the right drivers? Or is it something else? Maybe I need to run it from the terminal? I'm not sure. So would it help to uninstall the drivers the Linux is currently using, and then trying to reinsert my wireless card and try installing the netgears drivers then? Or is something else wrong?


So that is my first question, my second is much simpler.
I tried running Azureas, and when I tested out the default port setting it gave me a NAT error. I've tried researching other ports to use, but I'm stuck, and Azureas won't connect, so I can't download any torrents. The same problem happened in Bittorrent.

What to do? Could this problem be caused by the previous issue? I don't know, I don't know.

Thanks for the support guys.

---

### Post by Skerit on 2007-09-27
Well, I'm fine thanks! Had a bit of a slow day at work, got stuck at this presentation which lasted 3 hours instead of half an ho... Oh, ok, that's not the point :)

Euhm, first of the 2 don't have anything to do with each other, at least not that I know of. You must open the correct port on your router (I've had a few routers now, it cna mostly be done under "virtual servers") 

There you need to open up a port on your router and direct it to the ip adres of your computer on your network. The moment you open this up it'll work like a charm and your speed will rise considerably ...

Now, regarding your drivers, I haven't ever actually used the gui, however if it says that it doesn't find the hardware, it's probably just doing that; not finding the hardware. It doesn't matter if you already installed another driver for it. Are you certain it's the correct driver? There usually are an entire collectin of different drivers in 1 pack, at least on windows.

---

### Post by MysticEdge on 2007-09-27
> **Skerit said:**
> Well, I'm fine thanks! Had a bit of a slow day at work, got stuck at this presentation which lasted 3 hours instead of half an ho... Oh, ok, that's not the point :)

Euhm, first of the 2 don't have anything to do with each other, at least not that I know of. You must open the correct port on your router (I've had a few routers now, it cna mostly be done under "virtual servers") 

There you need to open up a port on your router and direct it to the ip adres of your computer on your network. The moment you open this up it'll work like a charm and your speed will rise considerably ...

Now, regarding your drivers, I haven't ever actually used the gui, however if it says that it doesn't find the hardware, it's probably just doing that; not finding the hardware. It doesn't matter if you already installed another driver for it. Are you certain it's the correct driver? There usually are an entire collectin of different drivers in 1 pack, at least on windows.

Hey mate, thanks for the reply,

Ok, so I want to try opening the port from the router for my laptop, but I don't know how to do this.

What is the process of going about this?

---

### Post by nickpaton on 2007-09-27
1st problem.

You need to use madwifi which comes pre-installed in the Feisty linux-restricted-modules-2.6.20-(15) 16-generic kernel.
I would suggest you uninstall ndiswrapper (via Synaptic) and then have a look at [this post]("http://www.stchman.com/ath_drv.html") which may be of help.
It does seem to be difficult for some people to install the wg511t on Feisty, and I would suggest you do a forum search using wg511t and madwifi for further ideas.

2nd problem.

It sounds like you are not port forwarding properly.  This means that in Azureus under Tools >  Connection > Incoming TCP Listening Port and make it, say, 65100.  Do the same for UDP Listening Port.

Save.

Close and restart Azureus.

Access your modem router, and in the Firewall section open ports 65100 to 65105 (I tend to open a couple more).
If you're not sure how to do this post back the model of your router.  

Oh and in answer to your question, I've spent the day getting Alsamixer to work with a Creative 5.1 Live! card :) - not as bad as the Winfast PVR2000 TV card which has almost got me beat :(

---

### Post by MysticEdge on 2007-09-27
No, I am not sure how to do that, the modem router is....

2Wire Homeportal 1000HW

---

### Post by nickpaton on 2007-09-27
I don't know the router but here goes...
Connect the PC to the router using an ethernet cable, and make sure you can access the internet etc - you may need to reboot the PC.

Access the router configuration screens via by typing its IP address into your browser. 

If you do not know its IP address post the results of the following terminal commands:

```
ifconfig
```

```
route
```

If you do know how to access your router config screens, go to [this]("http://www.2wire.com/imgs/pages/221.jpg") one.

You may also want to have a look at [this]("http://www.2wire.com/imgs/pages/203.jpg") screen too.

There's not a lot of information on their site for opening a port on the firewall, but see if you can work something out.
In the meantime post back with any questions and I'll continue to research this.

---

### Post by nickpaton on 2007-09-27
[This HOWTO]("http://support.2wire.com/cgi-bin/twowire.cfg/php/enduser/std_adp.php?p_faqid=488&p_created=1054337698&p_sid=_XxRoNMi&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9NDYmcF9wcm9kcz0mcF9jYXRzPSZwX3B2PSZwX2N2PSZwX3NlYXJjaF90eXBlPWFuc3dlcnMuc2VhcmNoX25sJnBfcGFnZT0xJnBfc2VhcmNoX3RleHQ9cG9ydCBmb3J3YXJkaW5n&p_li=&p_topview=1") on the 2Wire site describes how to open ports in the firewall.

Get back to me if there's any probs in the last couple of posts.

---

### Post by stoer on 2007-09-27
Hi,
Throw my 2 pence worth in....
You guy's ever heard of Portforward.com, lovely site. 
Lists a huge amount of routers and explains how to set up "port forwarding".
Pretty straight forward explanations, pretty much any idiot can follow them  -  i know I did ;)

[http://portforward.com/routers.htm](http://portforward.com/routers.htm)

It lists the 

2wire 1000hw

and the linked page leads you through a guided process

[http://portforward.com/english/routers/port_forwarding/2wire/1000hw/1000hwindex.htm](http://portforward.com/english/routers/port_forwarding/2wire/1000hw/1000hwindex.htm)

List of programs  " you are forwarding ports for"  to chose from....

Azureus is listed,

The following linked page....

[http://portforward.com/english/routers/port_forwarding/2wire/1000hw/Azureus.htm](http://portforward.com/english/routers/port_forwarding/2wire/1000hw/Azureus.htm)

tells you how to adjust the settings in Azureus
and in your router.  Lots of straight forward and easy to follow pictures.


Hope this helps, 
(used it myself for Azureus - but with a different router, worked a charm.)

---

### Post by nickpaton on 2007-09-27
Hey Stoer - great page and answers everything!

Cheers M8!

---

