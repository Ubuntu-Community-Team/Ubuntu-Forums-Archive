---
title: "Internet router does't re connect"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by reesy on 2007-11-22
I use a router to connect to the internet but if my father wants the internet down stairs because he is not connected to the router and uses a modem i have to disconnect it in my room when he then finishes and i re connect the cable and  the router connects but for my computer to actually work on the internet again i have to re boot. any suggestions how to get around this?

---

### Post by spiderbatdad on 2007-11-22
I believe network configurations take place during boot up, so I don't think you can get around this. Maybe is you could locate a config file of your network and copy it to your home directory, then run it as a bin/bash after you plug the cable in. I don't even know if this is possible, but it sounds like something I would try to do in your case, if I didn't want to restart in between having my cable unplugged and plugged.

---

### Post by amingv on 2007-11-22
Hi,

I had this same issue when my brother takes my USB "wireless stick", so I made a teensy weensy script and named it "connect", here goes:

```
#!/bin/bash

sudo ifup wlan0 --force [COLOR="Blue"]#replace wlan0 for whatever your card may be[/COLOR]
exit

```

Tell me how it works out for you. -Amin

---

### Post by reesy on 2007-11-23
i really am an amature when it comes to Ubuntu so could you tell me where am i meant to put that bit of code into and what to save it as :S and that probably sounds like a stupid question lol.

---

### Post by Znort_Ubern00b on 2007-11-23
[Check out this link]("http://gd.tuwien.ac.at/linuxcommand.org/wss0010.html")

it explains how to write script etc.

hope it helps.

---

### Post by ugm6hr on 2007-11-23
> **reesy said:**
> I use a router to connect to the internet but if my father wants the internet down stairs because he is not connected to the router and uses a modem i have to disconnect it in my room when he then finishes and i re connect the cable and  the router connects but for my computer to actually work on the internet again i have to re boot. any suggestions how to get around this?

Before messing around with scripts - just clarify your situation...
> 
You have a router that is connected to your ethernet port, which you use for broadband.

If you unplug the ethernet cable, and then plug it back in, your computer *connects* to the router (i.e. you can access the router's configuration webpage / ping it etc), but you cannot get on-line (e.g. to [www.google.co.uk](www.google.co.uk))

That's very bizarre, because Ubuntu configuration only manages the connection to the router - the router manages the connection to the internet (possibly via broadband modem).

If I've misunderstood your predicament - please clarify, because the solutions will be totally different.

PS:  Do you have Ubuntu (i.e. Gnome Desktop) - if so, Network Manager allows you to hot-swap ethernet cables when the power is on, so it should reconnect automatically.

---

### Post by amingv on 2007-11-23
Sorry, I always re-check my posts to see they make sense, but I often forget they may not make sense to others.
Plus, **ugm6hr** may have a point. It should work without you doing nothing else. But since you say it works after you reboot, then that kinda discards a router problem. So for clarity's sake I'll take a wild guess and ask you: do you connect your router with an USB cable or an Ethernet cable to your computer?

To be completely sure the script will be useful then you can try it before you write it. Just open a Terminal and type:

```
sudo ifup wlan0 --force
```

Of course, replacing wlan0 with your card. If it works then you can proceed to write the script:

Open **gedit** and copy in the code as I wrote it in my previous post. Save it as "connect". In the tutorial posted by **Znort_Ubern00b** you will learn how to give it executable permissions and add it to your PATH variable.
Alternatively, if you don't want to mess with PATH, you can just save it in your /home/yourname directory, and run it as ./connect or ~/connect from the Terminal.

Hope it's useful, regards. -Amin

---

### Post by ugm6hr on 2007-11-23
> **amingv said:**
> Plus, **ugm6hr** may have a point. It should work without you doing nothing else. But since you say it works after you reboot, then that kinda discards a router problem. So for clarity's sake I'll take a wild guess and ask you: do you connect your router with an USB cable or an Ethernet cable to your computer?


I didn't realise that you could connect to a *router* with USB; I thought only broadband modems can be USB, but routers and modem-routers are all ethernet (or wifi).

He mentions that his dad connects by modem, which is presumably a (potentially USB) broadband modem.

Hence my confusion, which reesy should clarify before everyone goes off on a tangent.

@reesy:
If you are not certain about your setup - answer the following questions (assuming you are in Wales):
1. Do you have ADSL or cable broadband?
2. Is the "router" connected to a separate modem (e.g. cable-modem or ADSL-modem), or does it plug directly into a phone socket (with filter)?
3. Is the "router" connected to your computer by ethernet or USB?

---

### Post by amingv on 2007-11-23
> **ugm6hr said:**
> I didn't realise that you could connect to a *router* with USB; I thought only broadband modems can be USB, but routers and modem-routers are all ethernet (or wifi).


I meant his *cable/dsl modem* up there. Thanks for the correction.
My point is, if he uses an USB modem then he may experience the same problem I had. But if he uses Ethernet then it makes no sense.
When he reboots his card renews the DHCP contract and the connection is "refreshed", and that's why I suggested this script just assuming all the above, because rebooting wouldn't do anything if the problem was beyond his NIC-->(router, modem, etc.).
Then again maybe I've lost myself looking at the problem from my past experience when actually something else may be happening. So I second that **reesy** should clarify...

---

### Post by timcredible on 2007-11-23
no script needed, just go to System->Administration->Network and uncheck your network connection and then check it again, that'll cause the system to drop and restart your networking.

---

### Post by bluepowder7 on 2007-11-23
first, can you clarify what type of modem your father has to use?  is it old-fashioned dial-up or a broadband?  and, if it's dial-up, why do you have two services?  if it's broadband, then why is he not able to connect to your router?  does your router have wireless capability?  even if his laptop doesn't have wireless, he (or you) can buy a small usb wireless thingy so that his laptop gets wireless connection to your router - and everything can stay connected.

---

### Post by Austin_KW on 2007-11-23
> **bluepowder7 said:**
> first, can you clarify what type of modem your father has to use?  is it old-fashioned dial-up or a broadband?  and, if it's dial-up, why do you have two services?  if it's broadband, then why is he not able to connect to your router?  does your router have wireless capability?  even if his laptop doesn't have wireless, he (or you) can buy a small usb wireless thingy so that his laptop gets wireless connection to your router - and everything can stay connected.

Beat me to it, It sounds like you are trying to solve the wrong problem here; You want to put the router where all PCs can connect to it (wired/wireless) not mess about with different modems.

---

### Post by reesy on 2007-11-23
Rite i can still connect to the router but for some reason it wont let me connect to the internet but the router is connected to the internet because on one of my other computers connected to the router it lets me use the internet again on Windows Xp.

 I'm using Ubuntu Gutsy Gibbon and i have the GNOME desktop. I connect with a Ethernet cable from the router. I have an ADSL broadband and the router plugs directly into the phone line with the filter.

We have broadband and he doesn't connect to my router because he is to far away to run a cable and it doesn't have the aerial on it to connect to him with out a cable.

---

### Post by bluepowder7 on 2007-11-23
line filter should be on the phone line, not the modem line.  but that aside, did you set up the router for static IP addresses of the computers, or DHCP?  also, if you did DHCP, did you limit the number of connections to just one?  what router is this on?  i've got a linksys wrt54g with wireless, and i'm able to run two pc's wired and two laptops wireless on it, without having to do any major manual setup.

---

### Post by reesy on 2007-11-23
rite for some bizarre reason it actually lets me go back on the internet when i unplug it the plug it in. I honestly haven't got a clue why its done this :s thanks any way, now i feel like a complete ***!

---

### Post by bluepowder7 on 2007-11-23
no worries on feeling line a small set of asterisks.  :P  on my laptop which is running 7.10, i can't even toggle between wired and wireless cuz the network manager borks.  nothing short of a reboot gets it working again.

---

### Post by ugm6hr on 2007-11-23
> **bluepowder7 said:**
> on my laptop which is running 7.10, i can't even toggle between wired and wireless cuz the network manager borks.  nothing short of a reboot gets it working again.

really?  i used wicd on feisty cos network manager was rubbish, but with gutsy it works great.  i can't think of anything it can't do that i need it to.  wicd, wifi, hot-swapping between....

---

