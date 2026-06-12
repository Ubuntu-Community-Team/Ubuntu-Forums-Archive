---
title: "Wireless problem - D-Link Router"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by Mark Taylor on 2006-08-06
I'm very new to Linux, been using Ubuntu for a couple of weeks or so, and I've managed to get most of my hardware working in many cases by searching these forums and applying solutions posted by others.

All well and good but I still can't get my wireless connection to work. The machine I've installed Ubuntu on is connected directly to my D-Link DI-624+ Router via the ethernet port. It works perfectly for internet access, but I can't connect to my wireless network (two laptops running windows) because in the network settings tool it's only showing up as an ethernet connection, not a wireless device. So no wireless settings to configure and no access to wireless network. Any suggestions?

---

### Post by x64Jimbo on 2006-08-06
Wait... Both laptops are running Windows and you can't access the wireless? Is the wireless access point turned on in the web config? In the case of a D-Link, the way you find this out is by navigating to 192.168.0.1 and entering admin as the username, and leaving the password blank. Next, click on the "Wireless" button and see if "Wireless Radio" is disabled or enabled. If it's disabled, that's likely your problem. If it's enabled, post back and tell us as much as you can about what you know. The more knowledge the better.

---

### Post by Mark Taylor on 2006-08-06
I can access wireless from both laptops - and from my desktop machine if I boot into Windows, just not from Ubuntu. In Ubuntu, internet access works great through the router, but I'm not seeing a wireless network, and I can't talk to either of the laptops. In the network settings panel I'm only seeing an ethernet connection - no wireless device.

---

### Post by x64Jimbo on 2006-08-06
OK i'm confused as to what you're trying to do. You already said that your desktop connects fine, and you've just now told me that your laptops connect fine, so what's the issue? Why does your desktop need to be wireless? Does your desktop have a wireless card? What's it called?

---

### Post by Mark Taylor on 2006-08-06
Okay, to clarify the situation. My desktop machine is connected directly to the wireless router via an ethernet cable. It has no wireless card. When running Windows on my desktop computer I have full access to everything. When running Ubuntu, I only have internet access... I can't talk to my wireless laptops from Ubuntu for file sharing, printer sharing etc. My wireless laptops can still talk to each other, but not to the desktop machine when it's running Ubuntu. I understand that to connect to my wireless network using Ubuntu I need to configure the wireless settings... WEP key and such... that are already set up on the router, but there are no wireless settings to configure, it's only showing up as an ethernet device, not a wireless device.

P.S. I've already installed Samba and set up file shares etc... They just don't work.

---

### Post by Mark Taylor on 2006-08-06
Been trying to find an answer for the last few hours - still no luck. I'm not sure if my previous posts were clear enough so I'll try to explain this again.

1) My desktop PC - which has Windows XP and Ubuntu in a dual-boot setup, is connected directly to my D-Link DI-624+ wireless router via an ethernet connecter, not via a wireless network card. I.E. It's plugged into the wireless router with a cable, as is my cable modem.

2) The two laptops (one is mine and one is my wife's), running windows, connect to the router via wireless network cards.

3) When I'm running Windows on my desktop PC, I can access the wireless network from my desktop PC - I can share folders on my desktop and on my laptops and print to the printer attached to my desktop PC from the laptops, etc.

4) When I'm running Ubuntu on my desktop PC, I only have internet access on my desktop PC. From my desktop PC I can't access the shared folders on the laptops, and from the laptops I can't access the shared folders on my desktop PC even though I've already set those up with Samba.

5) Perhaps I'm wrong, but I think the reason I'm having this problem is because when I go into the network settings panel in Ubuntu, no wireless device shows up - so I can't configure it to connect to the wireless network with the correct WEP key etc. Correct me if I'm wrong, but I think the Wireless router should show up as a wireless network device even though I'm connected to it with a cable, so that I can configure the wirless networking properties and connect to the rest of my wireless network. This router is supposed to work out-of-the-box with linux, according to the manufacturer.

6) It's vital for me to have access to files on my desktop PC from the laptops. So far it seems that I can do everything I need with Ubuntu - except this. However, this one facility is vital and without it Ubuntu won't be of much use to me.

7) I don't want to have to go back to using Windows XP on my desktop PC. I'm tired of the security issues which have caused me to lose vital data twice in the last six months despite running a firewal and up-to-date active anti-virus software all the time. I like Ubuntu. It seems to work great for me except for this one problem. So please help if you have any suggestions at all. Thanks.

---

### Post by x64Jimbo on 2006-08-06
You can't configure wireless settings on a wired interface. WEP security and such are only for wireless interfaces. I guarantee you this is not the problem, as your Windows desktop doesn't have a WEP key for its wired connection either. As for the SAMBA issues, I suggest you read this:
[http://ubuntuguide.org/wiki/Dapper#Samba_Server](http://ubuntuguide.org/wiki/Dapper#Samba_Server)

---

### Post by Monsieur le Comte on 2006-08-06
I think you're looking at it the wrong way (wireless network vs wired, router trouble).  It doesn't seem to be anything wrong with the router or the router setup.  If it was, it wouldn't work with Windows XP either.  And your network, regardless of whether it's wired or not, is still just a network.  Look at it as one thing rather than two seperate (wired & wireless).  All the computers attached to your network are the same regardless of whether they're wired or not -- they're just devices on the network, with IP addresses, all alike.  If you're hard-wired into the network you don't need to worry about WEP keys or anything.  As long as you're getting an IP address from the router, you're on the same network as those computers wirelessly getting an IP from the router.

Now, what SEEMS to be happening from what I understand is that when booted in Windows XP, those samba shares are showing up and when in Ubuntu they're not -- is this correct?  If so it's just a matter of configuring.  Samba is a native XP protocol so once that's set up properly it should all work just like it did before.

---

### Post by stormblue on 2006-08-06
To get your network files working try this:

places -> connect to server -> select windows share from the drop down -> click browse

Second, to get your wireless working on your desktop can you please give the outputof the following commands
```

sudo iwconfig
```
```
sudo ifconfig
```
```
sudo iwlist scan
```

---

### Post by Mark Taylor on 2006-08-06
OK so because my desktop PC is wired into the router my Ubuntu install will treat my network as if it were a wired network even though it has wireless components, right?

I originally set up all my fileshares on Windows. When I installed Ubuntu I set it up to share my home directory (and by extension my Windows partitions as they're mounted in a subdirectory of my home directory) and Ubuntu automatically installed Samba for me. I just can't see any of my shared Windows folders on the laptops from Ubuntu, or my shared home directory from the laptops running Windows. When I try to access the Windows network through my Ubuntu desktop it is there but it appears to be empty.


Output from sudo iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


Output from sudo ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:40:F4:4C:87:47
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fe4c:8747/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:73042 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56322 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:80086318 (76.3 MiB)  TX bytes:6992379 (6.6 MiB)
          Interrupt:193 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:256 (256.0 b)  TX bytes:256 (256.0 b)


Output from sudo iwlist scan:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

---

### Post by x64Jimbo on 2006-08-07
> **stormblue said:**
> To get your network files working try this:

places -> connect to server -> select windows share from the drop down -> click browse

Second, to get your wireless working on your desktop can you please give the outputof the following commands
```

sudo iwconfig
``` ```
sudo ifconfig
``` ```
sudo iwlist scan
```
Please don't confuse this user by telling him to run wireless commands on his desktop. It's already been established that the desktop is plugged straight into the router.
@OP:
I highly recommend following the instructions previously outlined here. Check out your Samba config and look to see if you can map the Samba shares through your Places menu.

---

### Post by Mark Taylor on 2006-09-22
Thanks to all those who tried to help out, however the problem turned out to be my own stupidity. I'd installed the Firestarter firewall and failed to configure it not to block my network. Doh.

---

