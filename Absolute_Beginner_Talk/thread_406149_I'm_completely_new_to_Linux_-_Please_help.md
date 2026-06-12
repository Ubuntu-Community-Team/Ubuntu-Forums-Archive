---
title: "I'm completely new to Linux - Please help"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by HellTestament on 2007-04-10
Hi, I am completely new to the Linux scene, I just crossed over from WindowsXP not too long ago(3 or 4 days). Somebody reccomended Ubuntu for me, so I downloaded the Live CD and gave it a try, and I loved it. I could get on the internet when I still had XP, but when I installed Ubuntu and partitioned my entire drive, I found I could no longer connect to the internet via WiFi or Ethernet cable.

When I try my Ethernet cable, it sets my connection to "Idle". When I enter my WEP key and everything for my wireless, it says I have no connection, and when I go to view the connection manager, it says that Wireless is not activated, even though I just activated it.
Sorry if this question had been asked before, I searched but did not understand a thing, so thanks for dealing with me in advance.

---

### Post by dbbolton on 2007-04-10
i think the first priority is to get your wired connection working (eth0). 

go to System > Administration > Networking, and make sure "Wired connection" is enabled (i.e., checkmark beside it). then, click on the DNS tab, and make sure the info matches that of your router. for example, your DNS Servers list should probably have 192.168.1.1 .

---

### Post by HellTestament on 2007-04-10
> **dbbolton said:**
> i think the first priority is to get your wired connection working (eth0). 

go to System > Administration > Networking, and make sure "Wired connection" is enabled (i.e., checkmark beside it). then, click on the DNS tab, and make sure the info matches that of your router. for example, your DNS Servers list should probably have 192.168.1.1 .

Yes, that is all fine. I figured out that lastnight. What is next?

---

### Post by dbbolton on 2007-04-10
next, you need to make sure your computer is using eth0 and not lo. right-click the network manager in the systray, and click properties. under connection, choose eth0.

---

### Post by HellTestament on 2007-04-10
Yussir, it is using Eth0, but it says that it is Idle

---

### Post by dbbolton on 2007-04-10
can you ping your router

---

### Post by HellTestament on 2007-04-10
If the 192.168.0.1 is my router, then yes, I can

And they were all sucessful

---

### Post by dbbolton on 2007-04-10
well, this might be kind of an obvious suggestion, but open your router's ip in a browser, check the settings, and temporarily set it to allow all traffic.

---

### Post by HellTestament on 2007-04-10
> **dbbolton said:**
> well, this might be kind of an obvious suggestion, but open your router's ip in a browser, check the settings, and temporarily set it to allow all traffic.

Well, I must be screwed. Somebody set up a password on it, and it is not opening up. Just a few months ago, it had no password(Because I got a NDS and a Wii and got my WEP key from that address, 192.168.0.1) Nobody remembers setting a password on it, though, so nobody knows it. 

Any way to get around this? I am posting this from the main computer in the house, the family computer. Could I set it up from there? This has Windows XP on it

---

### Post by bagguley on 2007-04-10
What router is it you're using?

---

### Post by HellTestament on 2007-04-10
Airplus XTreme G D-Link Wireless Router

---

### Post by Origin415 on 2007-04-10
If you never changed it, put the username as admin and leave the password blank.

---

### Post by pirothezero on 2007-04-10
> **Origin415 said:**
> If you never changed it, put the username as admin and leave the password blank.
And if that fails, get a paper clip and reset the router by sticking the clip in the reset hole on the backside or on the bottom of the router.

---

### Post by bagguley on 2007-04-10
You coukd try admin as the p/w, common to DLink routers

---

### Post by HellTestament on 2007-04-10
> **pirothezero said:**
> And if that fails, get a paper clip and reset the router by sticking the clip in the reset hole on the backside or on the bottom of the router.

I reset the router, yet admin still doesn't work for the username

---

### Post by Origin415 on 2007-04-10
> **bagguley said:**
> You coukd try admin as the p/w, common to DLink routers

Not according to the faq on their website and the dlinks ive used you might be thinking of Linksys.

btw, you should change that password as soon as possible, especially with a wireless router. Anyone can look up the default password for a router on the web and change your settings.

---

### Post by bagguley on 2007-04-10
May sound like a daft question but do you have the documentation for the router? That will have the default password/user name

---

### Post by bagguley on 2007-04-10
user name: User
No password

[http://www.phenoelit.de/dpl/dpl.html](http://www.phenoelit.de/dpl/dpl.html)

Model Number DI 624 right

---

### Post by HellTestament on 2007-04-10
> **bagguley said:**
> May sound like a daft question but do you have the documentation for the router? That will have the default password/user name

Alas, I do not. It never once required a username/password up until now, and nobody is fessing up.

I do, however, have another router that Verizon gave me when we set up with FiOs.
I shall switch to that and see if I can connect through that

---

### Post by HellTestament on 2007-04-10
> **bagguley said:**
> user name: User
No password

[http://www.phenoelit.de/dpl/dpl.html](http://www.phenoelit.de/dpl/dpl.html)

Model Number DI 624 right

You are awesome, I just read this post before hooking up the behemoth ActionTech MI424WR that they gave me

---

### Post by bagguley on 2007-04-10
The manuals are available online

[http://www.dlink.co.uk/?go=jN7uAYLx/oIJaWVTALoeU8H8g50JcLpcTc63PfG5wBm2FNY8i74tNJgwN6Ng6j8lHCvuzg==](http://www.dlink.co.uk/?go=jN7uAYLx/oIJaWVTALoeU8H8g50JcLpcTc63PfG5wBm2FNY8i74tNJgwN6Ng6j8lHCvuzg==)

You just need to look which revision it is.

---

### Post by bagguley on 2007-04-10
Any luck?

You should probably take Origin415s advice and change that fairly soon (many sneaky bored people out there)

---

### Post by HellTestament on 2007-04-10
> **bagguley said:**
> Any luck?

You should probably take Origin415s advice and change that fairly soon (many sneaky bored people out there)

Nope, not yet. I can't figure out where to change the settings to allow traffic, I just opened up the manual that bagguley has shown, so I am looking there

EDIT

Strange, my connection still says Idle on Ubuntu, yet after I opened up my routers IP and got in, I can freely surf the web via ethernet cable

EDIT

Even more strange, my wireless can now surf, too, yet it says I am not connected am my connetion bar claims little to no connection, yet I am right next to my router and my speed is just fine

:confused:

---

### Post by bagguley on 2007-04-10
Still fairly new on linux/ubuntu but mine currently says idle and have been surfing freely all night. 

Are you sending and recieving data? And can you see your laptop on your routers DHCP allocation table?

Your problem may be solved!

---

### Post by HellTestament on 2007-04-10
> **bagguley said:**
> Still fairly new on linux/ubuntu but mine currently says idle and have been surfing freely all night. 

Are you sending and recieving data? And can you see your laptop on your routers DHCP allocation table?

Your problem may be solved!


Why, yes I can :]

Now, to fix my Wireless. I thought it was working, but then after I unplugged my ethernet cable, I can no longer surf, even though I told it to use eth1. It keeps disabling it after I activate it and close out of the network panel. :confused: Help, please?

---

### Post by bagguley on 2007-04-10
Is your wireless integrated or via a peripheral card? And what model is it?

---

### Post by HellTestament on 2007-04-10
Integrated, I believe. It came with the laptop.
I don't know what version, is there a command I can type up in the Terminal or DOS or whatever it is called?

I discovered it. Itcomes from Broadcom Corp, and it is called AirForce One 54g(BCM4318 are the numbers infront of it). It's bus type is PCI

---

### Post by dbbolton on 2007-04-10
broadcom 4318 - good luck. there are plenty of tutorials on the forum on how to set up ndiswrapper with the windows drivers.

there's an app in the repositories called "Configure network card" that might be worth checking out.

---

### Post by HellTestament on 2007-04-10
> **dbbolton said:**
> broadcom 4318 - good luck. there are plenty of tutorials on the forum on how to set up ndiswrapper with the windows drivers.

there's an app in the repositories called "Configure network card" that might be worth checking out.


So this is gonna be a challenge? Ah, I've got all day. Thanks, I'll check out that app

---

### Post by dbbolton on 2007-04-10
yeah, i have basically the same card. it took me awhile to get it working. 

of course, my wireless router is so crappy that i have more range with a 20' cable.

---

### Post by HellTestament on 2007-04-10
> **dbbolton said:**
> broadcom 4318 - good luck. there are plenty of tutorials on the forum on how to set up ndiswrapper with the windows drivers.

there's an app in the repositories called "Configure network card" that might be worth checking out.

Does anyone happen to know where I can get the bcmwl5.sys and bcmwl5.inf([http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177))? I can't seem to find them. I'll continue searching google, but it'd be nice if somebody could upload those two files for me, since the link to download those files within that thread is broken.

EDIT

I have the bcmwl5.sys, but cannot find the bcmwl5.inf , would anybody be kind enough to upload it for me?

---

### Post by dbbolton on 2007-04-10
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B)

you can find the files there

---

### Post by HellTestament on 2007-04-12
Thank you everybody for your help. I think it is almost finished(I am hoping)

My light now turns on, which shows that my card is installed. But, when I switch my connection to eth1, it says it is idle, yet I have no connection, even when I am next to my router. Here's what I get when I type the command iwconfig - 
```

ikit@kit-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

:confused:

---

### Post by dbbolton on 2007-04-12
if your light comes on, you're definitely almost there. i think it would be very helpful to install "wifi-radar." it makes it easier to find networks, enter WEP keys, etc.

you can also do this manually. first, set the WEP key for your network:
```
iwconfig eth1 key restricted  XXXXXXXXXX
```then set the name of the network:
```
iwconfig eth1 essid XXXXXXXXXX
```

again, wifi radar makes this much easier by providing a GUI, as well as remembering network names/keys.

---

### Post by alexlex on 2007-04-12
your not screwed just reset the router... hold the reset pin in for 20 sec and release

---

### Post by HellTestament on 2007-04-12
> **dbbolton said:**
> if your light comes on, you're definitely almost there. i think it would be very helpful to install "wifi-radar." it makes it easier to find networks, enter WEP keys, etc.

you can also do this manually. first, set the WEP key for your network:
```
iwconfig eth1 key restricted  XXXXXXXXXX
```then set the name of the network:
```
iwconfig eth1 essid XXXXXXXXXX
```

again, wifi radar makes this much easier by providing a GUI, as well as remembering network names/keys.

I wanted to grab that, but in my Synaptic Package Manager, ther is no Wifi Radar :'(

I set my WEP and my network name, but it didn't work.

I'll try reseting my router, dunno if it will help or not

---

### Post by dbbolton on 2007-04-12
> **HellTestament said:**
> I wanted to grab that, but in my Synaptic Package Manager, ther is no Wifi Radar :'(

I set my WEP and my network name, but it didn't work.

I'll try reseting my router, dunno if it will help or not
you might need to enable extra repositories.

System > Admin > Software Sources ; and check multiverse. (universe and main should also be checked)

---

