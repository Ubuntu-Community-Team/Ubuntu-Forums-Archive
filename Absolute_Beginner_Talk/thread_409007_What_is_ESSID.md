---
title: "What is ESSID?"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by awiggin on 2007-04-14
Hi

I feel like an idiot.  I am trying to configure my Linksys WUSB54G v.4 network adapter, which I heard from many people should work on ubuntu (my last adapter never did work - using the zd1211 driver - but that's another story).

Anyhow, I have to type something into the ESSID box but I don't know what that is nor how to find it.

Please help this Noob.

Peace,
L

---

### Post by Legionox on 2007-04-14
ESSID stands for Extended Service Set ID. The ESSID is the identifying name of a wireless network - strictly it is the identifying name of a wireless access point. It allows one wireless network to be clearly distinguishable from another. ESSID is one type of SSID (the other being BSSID). All you have to do is find your SSID in the configuration of your wireless router and put it there.

---

### Post by jfinkels on 2007-04-14
the default name is probably something like "linksys" or "default", if you didn't change the ESSID of the network when you set it up initially

---

### Post by awiggin on 2007-04-14
Sweet.

How do I figure out what to type in the box for my wireless net connection?

Thanks for clarifying.

-L

---

### Post by ayenack on 2007-04-14
The SSID is normally the make and model or just the model name of the access point (Router) you're connecting to. 

So if you were connecting to a D-Link G604T_WIRELESS access point the SSID would normally be D-Link G604T_WIRELESS or just G604T_WIRELESS.

So what you need to do is find out the name of your access point (Router). It's that simple.

Best of luck. ayenack.

---

### Post by n3tfury on 2007-04-14
> **jfinkels said:**
> ....if you didn't change the ESSID of the network when you set it up initially

and if he didn't, i highly recommend doing so.

---

### Post by ugashia on 2007-04-14
The ESSID is sometimes written on the bottom of the router

---

### Post by chili555 on 2007-04-14
The easy way to find it is:```
sudo iwlist eth1 scan
```Substitute your wireless interface for eth1 here. Might take a few tries. Spelling and case are vital.

---

### Post by wieman01 on 2007-04-14
> **n3tfury said:**
> and if he didn't, i highly recommend doing so.
Nah... encryption will do the job eventually. Changing the name (or even hiding it) adds no extra security at all.

---

### Post by wieman01 on 2007-04-14
> **chili555 said:**
> The easy way to find it is:```
sudo iwlist eth1 scan
```Substitute your wireless interface for eth1 here. Might take a few tries. Spelling and case are vital.
It appears he has got a WUSB54G V4 adapter with Serialmonkey driver, so the interface should be "rausb0" unless he has installed "ndiswrapper". Do a...
> sudo iwlist scan
...instead.

---

### Post by awiggin on 2007-04-14
Yes, wieman, that is correct.

I installed ndiswrapper and followed the instructions here:

[http://ubuntuforums.org/showthread.php?t=192588](http://ubuntuforums.org/showthread.php?t=192588)

Now, I have no rausb0 at all.  Did I screw up?

-Lance

---

### Post by user1397 on 2007-04-14
> **awiggin said:**
> Yes, wieman, that is correct.

I installed ndiswrapper and followed the instructions here:

[http://ubuntuforums.org/showthread.php?t=192588](http://ubuntuforums.org/showthread.php?t=192588)

Now, I have no rausb0 at all.  Did I screw up?

-Lancewait, do you even have a router at all?  _[what you bought]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1115416827517&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=2751739789B45")_, is just an adapter to connect your PC to a router (or wireless access point).  First you need a router. Something that _[looks like this]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1148435315453&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=1545339789B01")_.

and by the way, the default SSID for linksys routers IS **linksys**

---

### Post by awiggin on 2007-04-14
Sorry, I can see where it looks like I am a complete idiot.

Yes, I do have a router.  I am connected to it right now via the wire.  But when I typed in iwconfig, the rausb0 isn't listed because I think I removed it when I followed these instructions:

[http://ubuntuforums.org/showthread.php?t=192588](http://ubuntuforums.org/showthread.php?t=192588)

In those instructions, it says this:

First you'll see that in the admin -> network there is a rausb0 wireless. However that does not work with the native drivers provided (think they used rt2570)

> 
Step 1

So you need to blacklist it first in a file situated in etc/modprobe.d/

```


$sudo gedit /etc/modprobe.d/blacklist 
```

add the following line in the blacklist file

blacklist rt2570



Sorry for looking like an idiot.  How do I get my rausb0 back?

---

### Post by wieman01 on 2007-04-14
> **awiggin said:**
> Sorry, I can see where it looks like I am a complete idiot.

Yes, I do have a router.  I am connected to it right now via the wire.  But when I typed in iwconfig, the rausb0 isn't listed because I think I removed it when I followed these instructions:

[http://ubuntuforums.org/showthread.php?t=192588](http://ubuntuforums.org/showthread.php?t=192588)

In those instructions, it says this:

First you'll see that in the admin -> network there is a rausb0 wireless. However that does not work with the native drivers provided (think they used rt2570)



Sorry for looking like an idiot.  How do I get my rausb0 back?
You have just blacklisted "rausb0"... so you are currently using "ndiswrapper" and as a consequence the interface's name has changed. Please post the contents of this file (command line):
> sudo gedit /etc/network/interfaces
And remember for later... whenever you try to enable your wireless network, pull the Ethernet cable. You cannot have 2 network connections at the same time.

---

### Post by wieman01 on 2007-04-14
Find out about your new interface name this way:
> cat /etc/modprobe.d/ndiswrapper
Please post it here as well.

---

### Post by awiggin on 2007-04-14
Here is what I got from sudo gedit /etc/network/interfaces:

```

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface rausb0 inet dhcp
wireless-essid Huffman Family Network
wireless-key s:Piper153

```

And here is what I got from cat /etc/modprobe.d/ndiswrapper

```


alias wlan0 ndiswrapper


```

I am heading out now, so I will work with whatever you send me after this.

Check back when you can.

Thanks, 
lance

---

### Post by ayenack on 2007-04-14
Would it not be an idea to un-install ndiswrapper?

I'm curious did you try the USB adapter without ndiswrapper, and if so did it work?

Best of luck. ayenack.

---

### Post by ayenack on 2007-04-15
iface rausb0 inet dhcp
wireless-essid Huffman Family Network
wireless-key **********

It's there and it's being recognized on rausb0.


The Linksys USB WUSB54G v.4 should work fine out of the box it's natively supported as far as I can tell so there really is no need for ndiswrapper.

It also works fine when using WEP encryption. Not to sure about WPA though but this should work also with a few downloads and a bit of tweaking if you're up to it.

Best of luck. ayenack.

P.S. Your SSID should be Huffman Family Network according to the above info. It must have been changed by you or whoever installed your A.P. for you.

---

### Post by awiggin on 2007-04-15
Thanks for the tip!

I disconnected everything and uninstalled ndiswrapper, then started over.

I had to type in my own IP address and everything, but it worked.  I am now wireless.

Thanks so much for your help.  

-AWiggin

---

### Post by wieman01 on 2007-04-15
> **awiggin said:**
> Thanks for the tip!

I disconnected everything and uninstalled ndiswrapper, then started over.

I had to type in my own IP address and everything, but it worked.  I am now wireless.

Thanks so much for your help.  

-AWiggin
Nice. You don't really need "ndiswrapper" since the WUSB54G V4 works "out of the box". The only drawback is that the native driver does not support WPA2 security, but that's nothing I would worry about for now.

---

### Post by ayenack on 2007-04-15
No probs. These things can be tricky on GNU Linux. Glad I could help.:) 

You should probably change your network key and enable encryption if you haven't done so already just to be on the safe side.

Best of luck. ayenack.

---

### Post by awiggin on 2007-04-15
How do I change my network key and enable encryption?

Thanks again for all your help guys.

-AWiggin

---

### Post by n3tfury on 2007-04-15
> **wieman01 said:**
> Nah... encryption will do the job eventually. Changing the name (or even hiding it) adds no extra security at all.

leaving it default makes it look like you're a "noob" and would be a hackers first choice in a short list of available networks to get into.

---

### Post by wieman01 on 2007-04-15
> **n3tfury said:**
> leaving it default makes it look like you're a "noob" and would be a hackers first choice in a short list of available networks to get into.
Haha... That is true indeed. ;-)

As for encryption, it is a bit tricky as far as RAUSB0 is concerned as it refers to Serialmonkey's driver for Ralink (WUSB54G V4). You find stuff concerning it here:

[http://pastebin.ca/408779]("http://pastebin.ca/408779")

---

### Post by ayenack on 2007-04-15
Wait a minute here.... it seems to me as if you are already using encryption and I'm guessing that it's WEP by the length of the key. I have a few questions for you.

1, When you un-installed ndiswrapper and manually set up your wireless network did you have to type a password into the Network Password box in Network Settings?

I'm guessing you did. If you did it would be the afore mentioned Network Key. So if this is the case all you need to do is change your Network Key as I and everyone else who reads your post will know it (maybe you should edit your post and blank out the Network Key bit). 

To change your Network Key you will have to log into your router this is normally done through a web browser by typing 192.168.1.1 in the address bar entering the user name and password of the A.P. 

It's a remote chance that anyone will ever actually ping your A.P. and also have read the post so the chances are you will have no problems but I'm paranoid about these things.

2, What Router A.P. are you using?

3, Did you set up your router yourself?

Your SSID has already been changed to Huffman Family Network you don't need to worry about this.

Best of luck. ayenack.

---

### Post by mlnease on 2008-03-29
> **chili555 said:**
> The easy way to find it is:```
sudo iwlist eth1 scan
```Substitute your wireless interface for eth1 here. Might take a few tries. Spelling and case are vital.

Thanks, Chili--very nice to have this.

mike

---

