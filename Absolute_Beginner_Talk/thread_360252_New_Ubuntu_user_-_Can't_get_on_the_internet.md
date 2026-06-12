---
title: "New Ubuntu user - Can't get on the internet"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by derryk on 2007-02-12
So, as with most of the posts in the absolute new linux ubuntu users - I cannot get my internet connection to work. I am at work right now, but I'll give you a vague idea as to what I have happening, and perhaps by the time I get home some kind persons can help me out. I've searched through many posts already and anything i've tried doesn't seem to help. So, here is my situation:

* Just installed Ubuntu 6.10 (i386) on my PC
* Everything is working great, I have sound, video etc.
* I'm using a wireless USB networking card which is going out to a wireless router and into a ADSL internet connection
* In the network settings, there are many devices: one for a dialup modem, one for a ethernet card, and it seems as if there are two listed for my wireless card - I cannot remember the specific names for them but just by guessing i believe one is called wlan and one wmaster?
* I've tried using automatic dhcp settings but I could not get any pings or see a network. 
* I've tried manually putting in IP's to try and reach my router (default 192.168.1.1) and assigning an IP that would not interfere with any other computers on my network (there are two).
* When going into Network tools, I cannot send out a ping to anything (WWW or IP address)

So, please take into mind that I am basically brand new using linux, but I am an avid computer user and will take on anything someone has to offer as for instructions, etc...

Without further ado, can someone please write me back a few step-by-step instructions as to how I can get this thing going? I want to get into using Linux but If it's too complicated as for something as simple as getting Internet to work I'm just going to stick to Windows. That should get someone angry and hopefully help me get going!

Thanks.

---

### Post by nickoli_02 on 2007-02-12
Haha, great tactic to get a quick response :) As for your wireless USB card, what's the brand and model? You may not have correct drivers installed. Can you connect to a network on the Ubuntu PC through your wired ethernet interface?

---

### Post by derryk on 2007-02-13
It is a DLink wireless card, and also a DLink router. I'm still at work, but I'll post the exact models when I get home. If I have the wrong drivers installed, shouldn't it not be picked up at all?

Thanks for such a quick reply.

---

### Post by tonyr1988 on 2007-02-13
Under the Networking dialog, did you:

1) Enable the connection(s)? You have to double-click the connection and select the "Enable" box at the top.

and

2) Activate the connection(s)? After enabling, you must tick the checkbox to the left of the connection name. A window will pop up with a progress bar saying something along the lines of "Activating the connection . . . "

If that doesn't work, keep them activated and show us the result of

> ifconfig

(Applications -> Accessories -> Terminal)

---

### Post by kaede on 2007-02-13
this is one of my main reason not to switch ubuntu until now. since my pcmcia wireless card seems have a problem with this. im using SMC  2835W. anyone can figure how to do it step by step? since im still newbie in linux. thanks before

---

### Post by derryk on 2007-02-13
Hey, Just a quick follow-up from my last post and some replies to those who have posted.

Okay, so I lied earlier, I am using a DLink WUA-1340 Wireless USB card, but the router is a Linksys, model WRT54GC. 

Anyway, yes, the connections are enabled of course - but as for what they are called; one is named "Wireless Connection - wmaster0" and the other is "Wireless Connection - wlan0). I've tried using the internet with them both enabled, no good. Also have tried using the internet with just one or the other enabled, no good. 

I have a question, however... under the settings for those connections, the Essid is named "Routerbot"... that is the name of the router when I'm using Windows. Is that okay? I'm guessing I can just name it anything...

I haven't tried using a wired connection to the router because I don't have a cable that will reach to the router, not that I want to do that, anyway. I'd much rather stick with wireless.

After doing some searching within Ubuntu I found a nifty little program called "wifi-radar" that I needed an internet connection to download/install, but I've just gone to the Ubuntu community and downloaded/burned it... If I can figure out how to install it and try to use it then maybe I'll post my next reply in Linux - Lets cross our fingers!

---

### Post by derryk on 2007-02-13
Well, Wifi-radar didn't help me at all. ](*,) 

Here is more information for someone out there to possibly help me out. I've attached a couple pictures - one showing that the driver for my wireless internet card is installed and working (drivers.png) one showing my network settings (networksettings.png) and the other is the extended network settings for the wireless devices (settingsforwlan&wmaster.png)

notice that right now the essid is "routerbot" - this is the id the router was given by my roommate when he set it up for windows. i'm still not sure if this is okay or not? and also, of course the password is in there for obvious reason, and yes, i've double checked it. As for the connection settings right now it is on auto DHCP; but I have tried assigning myself an IP (192.168.1.102) among others... the subnet mask of course defaulted to 255.255.255.0 and for the gateway I plugged in the router's IP (192.168.1.1) but even manually putting in the ip/subnet mask/gateway i still had no internet.

I've gone into the console and plugged in "ifconfig" and this is what I got:

-------------------------------------------------------------------------------------
derryk@derryk:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:802 errors:0 dropped:0 overruns:0 frame:0
          TX packets:802 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:65844 (64.3 KiB)  TX bytes:65844 (64.3 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:15:E9:F7:92:1F  
          inet6 addr: fe80::215:e9ff:fef7:921f/64 Scope:Link
          UP RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:12955 (12.6 KiB)
          Base address:0x1000 

wmaster0  Link encap:UNSPEC  HWaddr 00-15-E9-F7-92-1F-00-00-00-00-00-00-00-00-00-00  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x1000 
-------------------------------------------------------------------------------------

When I assigned IP's etc you can guess what was there.... what I put in! Still no internet though.

Oh! one more thing, and this may be why. When I am in Ubuntu, my wireless usb card doesn't blink at all. It just has a steady light on. :confused: 

I'm seriously running out of patience and ideas... I hope someone out there can help me out. I want to use Ubuntu and ditch Windows once and for all!!! :-({|=

---

### Post by IronMac on 2007-02-13
> **derryk said:**
> 
Here is more information for someone out there to possibly help me out. I've attached a couple pictures - one showing that the driver for my wireless internet card is installed and working (drivers.png) one showing my network settings (networksettings.png) and the other is the extended network settings for the wireless devices (settingsforwlan&wmaster.png)

notice that right now the essid is "routerbot" - this is the id the router was given by my roommate when he set it up for windows. i'm still not sure if this is okay or not? and also, of course the password is in there for obvious reason, and yes, i've double checked it. As for the connection settings right now it is on auto DHCP; but I have tried assigning myself an IP (192.168.1.102) among others... the subnet mask of course defaulted to 255.255.255.0 and for the gateway I plugged in the router's IP (192.168.1.1) but even manually putting in the ip/subnet mask/gateway i still had no internet.

I've gone into the console and plugged in "ifconfig" and this is what I got:


When I assigned IP's etc you can guess what was there.... what I put in! Still no internet though.

Oh! one more thing, and this may be why. When I am in Ubuntu, my wireless usb card doesn't blink at all. It just has a steady light on. :confused: 

I'm seriously running out of patience and ideas... I hope someone out there can help me out. I want to use Ubuntu and ditch Windows once and for all!!! :-({|=

Maybe I can help since I've just got my wireless connection going with an old 3COM Xjack PCMCIA card and a Linksys WRT54G? (On a tangent, I really don't care if you go back to Windows...I use a Mac...hehehe)

First off, you do not need to have your wireless USB card blinking at all. My 3Com Xjack isn't blinking at all.
Second, if your system detects "routerbot" then make sure that it's selected as Network name. Key type is Hexadecimal. Now, here's the somewhat tricky part. I've found that if you have a Hexadecimal Key type in your router settings then you should enter one of them in the WEP key box.
Third, configuration should be DHCP.

Your IP addresses, Subnet mask and Gateway address are left blank.

You can read some of what I am doing with this on my blog at [http://www.steppingforth.com](http://www.steppingforth.com).  :)

---

### Post by derryk on 2007-02-13
Well, my wireless card blinks when I am in Windows... It just seems kind of odd that it's just a steady light when using Ubuntu. :confused: 

Also - in Ubuntu network settings it did *not pick up any networks at all*- I manually typed in "Routerbot" in the ESSID box since Windows picks up my Internet connection (Router>ADSL) as that name. It is set as DHCP in Windows...

So, I've tried time and time again in Ubuntu to get my internet working, just typing in the ESSID and the hexadecimal password that is used in Windows, leaving everything else blank but it's still no good.

A couple questions though - In Windows I type in an actual password the Router was assigned in it's administration settings to access the internet - but i've never had to type in a WEP key, anywhere. I cannot find a place in Ubuntu to input this, and I do not even know how to aquire the WEP... I accessed the router in Windows and searched through all of it's information; the closest thing I could get was a MAC address. 

Anyone, please? :(

---

### Post by carrie.peary on 2007-02-13
I just did this earlier today on my computer (newbie too) and this worked for me (by accident go figure)

The ESSID is your network name (routerbot something was yours)
Hexidecimal is the next option to choose
now for the password, is the long key that contains the nos. 0-9 and letters A-H. It looks something like this: AFD0291ABDD04432DBCEE83D
And choose DCHD as the last option.

Then hit ok.

After that, click on your wireless icon on the panel, and click to choose the corrent one. Once you choose the right one, you should see it connect in an instant and you should be good to go. Hope this helps.

Oh, and to get the Key Phrase we uninstalled our network and reinstalled it (cause we couldn't remember our original password/username to get to the data). It only took about 15min to do it, and I was able to get the key password I needed. Might work for you too if your up for that.

---

### Post by derryk on 2007-02-13
How does one aquire that long password/key? When I was using Windows, the password that was used in the wireless network wizard was just a passcode that was set manually on the router...

I've tried logging onto the router in windows using it's default address (192.168.1.1) and looking there.... all I could find was the MAC address and the router's Internet connection IP. If there is a way to find that key in Windows even, let me know. otherwise any other suggestion would help! Thanks for the reply. :)

---

### Post by derryk on 2007-02-13
Okay, well I THINK I know why my internet isn't working. Someone suggested (sorry I can't remember your name) that I plug in my WEP password into the password box; and I never had to do this in Windows. Most users (like me) just select the "WPA" (Wi-Fi Protected Access) and assign a password within the router's settings; and what I am going to do is try switching over to to WEP.

Perhaps that will help, I don't know if people are successfully using WPA vs. WEP security.

I dunno - maybe someone can suggest something else before I go and mess up my Internet all together? :?:

---

