---
title: "network configuration problems"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by noobbutnotboob on 2007-06-22
I installed Ubuntu a couple weeks ago on my Thinkpad T22 laptop. All seemed fine, got through the Savage driver issue thanks to posts here, and was mostly impressed with Ubuntu. But I could not get either the wireless (Netopia 3D Reach) or the wired (Cox digital cable) to work. Both connections would be recognized, it would even say "you are now connected".. but the connection itself didn't actually work. Pulled my hair out, etc, got nowhere. Decided that being a noob I must have done something wrong in the installation. So I just started to reinstall Ubuntu and came across a problem. Looking back, I had this problem the first time I installed but didn't know enough about Ubuntu at the time to worry about it. Now I can see it was the source of my troubles. So here's the prob:

Under "configure the network" it finds:

[COLOR="RoyalBlue"]primary network interface = 
eth0:  Intel Corp 82557/8/9 [Ethernet Pro 100]
irda0: unknown interface[/COLOR]

I thought the irda0 might be showing up because my wireless card was plugged in. So I unplugged it and reran the config... but it still shows up. So, I choose the Intel interface as the primary and then I get this:

[COLOR="royalblue"]Network autoconfiguration failed
Your network is probably not using the DHCP protocol. Alternatively, the DHCP server may be slow or some network hardware is not wokring properly.[/COLOR]

I hit continue and then "retry" but get the same result. Went back and tried the irda0 interface as primary with the same result. Which makes me realize that I have no idea what I doing.:redface:

The first time I installed Ubuntu I then chose the "do not configure the network at his time" option and went on with it. Hence the problems connecting to the net wired or wireless (I think).

So, the question is, [COLOR="Red"][SIZE="2"]how do I fix this? what do I do next?[/SIZE][/COLOR]

---

### Post by dbbolton on 2007-06-22
> **noobbutnotboob said:**
> I installed Ubuntu a couple weeks ago on my Thinkpad T22 laptop. All seemed fine, got through the Savage driver issue thanks to posts here, and was mostly impressed with Ubuntu. But I could not get either the wireless (Netopia 3D Reach) or the wired (Cox digital cable) to work. Both connections would be recognized, it would even say "you are now connected".. but the connection itself didn't actually work. Pulled my hair out, etc, got nowhere. Decided that being a noob I must have done something wrong in the installation. So I just started to reinstall Ubuntu and came across a problem. Looking back, I had this problem the first time I installed but didn't know enough about Ubuntu at the time to worry about it. Now I can see it was the source of my troubles. So here's the prob:

Under "configure the network" it finds:

[COLOR="RoyalBlue"]primary network interface = 
eth0:  Intel Corp 82557/8/9 [Ethernet Pro 100]
irda0: unknown interface[/COLOR]

I thought the irda0 might be showing up because my wireless card was plugged in. So I unplugged it and reran the config... but it still shows up. So, I choose the Intel interface as the primary and then I get this:

[COLOR="royalblue"]Network autoconfiguration failed
Your network is probably not using the DHCP protocol. Alternatively, the DHCP server may be slow or some network hardware is not wokring properly.[/COLOR]

I hit continue and then "retry" but get the same result. Went back and tried the irda0 interface as primary with the same result. Which makes me realize that I have no idea what I doing.:redface:

The first time I installed Ubuntu I then chose the "do not configure the network at his time" option and went on with it. Hence the problems connecting to the net wired or wireless (I think).

So, the question is, [COLOR="Red"][SIZE="2"]how do I fix this? what do I do next?[/SIZE][/COLOR]
do you use a static IP with your provider?

---

### Post by Xoanan on 2007-06-22
Most cable providers use DHCP these days...its possible I suppose

---

### Post by owise1 on 2007-06-22
what is your network setup?  Do you have a wireless router connected to a broadband modem?

---

### Post by noobbutnotboob on 2007-06-22
hi owise1 (nice moniker!)!

I am just sky surfing on free wifi - that's how I want to use the laptop 100% of the time once it is up and running. When I've tried the wired connection it is on Cox which uses DHCP.

---

### Post by dbbolton on 2007-06-22
> **noobbutnotboob said:**
> hi owise1 (nice moniker!)!

I am just sky surfing on free wifi - that's how I want to use the laptop 100% of the time once it is up and running. When I've tried the wired connection it is on Cox which uses DHCP.
go to System > Administration > Networking and check the settings under the DNS tab

---

### Post by owise1 on 2007-06-22
Cox I assume is your provider - do you just plug the ethernet cable into your modem?  Did you try re-starting the modem?

For the free wifi (wish we had that here!) is there encription (WEP or WPA)?

---

### Post by noobbutnotboob on 2007-06-22
Thanks for the reply here too...

Cox is the provider. Ethernet cable from modem into laptop. Recognizes it as wired connection. Tried restarting the modem, but nothing changed. Ditto on restarting the system while ethernet cable plugged in. On the desktop, there is nothing to do for the Cox connection, which just is automatically and always on. There was an installation CD with it, which I tried to use on the laptop, but it is for Win xp, so of course Ubuntu doesn't recognize the program type. I manually entered in the DNS and IP info from my desktop onto the network manager|wireless in the laptop, but that did not work either. :(

---

### Post by owise1 on 2007-06-22
Does your modem do the authentication?  On XP did you have to provide username and password to connect to your ISP or did the modem "just work"

---

### Post by noobbutnotboob on 2007-06-22
OK ndiswrapper-common, -utils installed. Did not have the ndisgtk for some reason. So I downloaded that from packages.ubuntu.com/feisty on the desktop and tranfered it over to the laptop. Installed just fine and am now looking at it. It's pretty clearly indicating that I have no driver installed at all. Sheez.

---

### Post by noobbutnotboob on 2007-06-22
Following the instructions in the internet section of the manual, I managed to get some bars on my wireless (51% from my neighbors unprotected router - which btw I could connect to no problem with XP, so I know I can access it and that all this equip works) . Now ifconfig shows the same stuff, and lshaw shows the network DISABLED.

I have also verified that wpasupplicant is installed.

Still, server not found in Mozilla. :((

---

