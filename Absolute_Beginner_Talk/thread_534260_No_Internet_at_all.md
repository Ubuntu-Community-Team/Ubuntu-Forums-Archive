---
title: "No Internet at all"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by Controlpanel on 2007-08-25
I am new to Linux and cannot run the internet at all. I am dual booting my computer. The internet works fine on Windows but not on Ubuntu. Thanks for the help.

---

### Post by wormser on 2007-08-25
We are going to need more info to be able to help you.  Can you post the results of the following commands.  Applications> Accessories> Terminal.

```
ifconfig
```
```
lspci
```

---

### Post by alienexplorers on 2007-08-25
Are you using a wired connection or wireless connection.  This information along with what wormser ask for would be great to know to help you.

---

### Post by Controlpanel on 2007-08-25
I have tried both useing wireless and wired

---

### Post by Controlpanel on 2007-08-25
ifconfig

> eth0      Link encap:Ethernet  HWaddr 00:14:22:90:98:B0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 

eth0:avah Link encap:Ethernet  HWaddr 00:14:22:90:98:B0  
          inet addr:169.254.7.217  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1120 (1.0 KiB)  TX bytes:1120 (1.0 KiB)

lspci

> 00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by Controlpanel on 2007-08-25
...

---

### Post by Controlpanel on 2007-08-25
...

---

### Post by Controlpanel on 2007-08-25
Someone please Help

---

### Post by Controlpanel on 2007-08-25
...

---

### Post by meindian523 on 2007-08-25
Just posting ...s to raise your thread to the top won't work.If nobody's replying means either no one knows or the ones' who know have not come across this thread yet.Wait for wormser to come back.

---

### Post by Controlpanel on 2007-08-25
> **meindian523 said:**
> Just posting ...s to raise your thread to the top won't work.If nobody's replying means either no one knows or the ones' who know have not come across this thread yet.Wait for wormser to come back.

Yea ok sorry, I figured someone would call me on that, sorry

---

### Post by meindian523 on 2007-08-25
It's OK,just don't repeat it,not just here,any other place where you are asking for help needs a big helping of patience.:)

---

### Post by xzero1 on 2007-08-25
Do you use a static IP address? Can you ping another computer? Can you ping your router? If so, can you log into it?

---

### Post by Controlpanel on 2007-08-25
> **xzero1 said:**
> Do you use a static IP address? Can you ping another computer? Can you ping your router? If so, can you log into it?

Im not sure, can you tell me how to do that? I got Linux yesterday so Im a super newb, sorry.

---

### Post by Controlpanel on 2007-08-25
I'm not sure how to use the Static IP address function.

---

### Post by xzero1 on 2007-08-25
Ok, windows is working right? In windows, do start->run-> (type in) cmd. Now type ipconfig /all and post the results back here.

---

### Post by oilchangeguy on 2007-08-25
try this. i dual boot with windows, and while in ubuntu if i  restart the computer, boot to windows, and get on the internet fine. however, if i restart windows, and boot ubuntu i can't get online. and i'm behind a router, so it should not make any difference. but i have to turn off the computer, modem, and router. turn everything back on in order to get online again in ubuntu.

---

### Post by Controlpanel on 2007-08-25
> **xzero1 said:**
> Ok, windows is working right? In windows, do start->run-> (type in) cmd. Now type ipconfig /all and post the results back here.

Yea I tried this and I got the IP Address, Subnet Mask and the other one and entered it into Ubuntu for both wired and wireless and it didn't change anything.

---

### Post by xzero1 on 2007-08-25
Thats why I said to post the results. What I want to do is compare the Ubuntu numbers with windows numbers. Usually, your computer gets its IP address from a DHCP server automatically and you cant just pick one. You can post to this forum from within windows.

---

### Post by fenian on 2007-08-25
First lets just use the wired connection connect those cables and restart you computer.
Then left click on the network manager icon in the panel and choose manual configuration click the connections tab select wired connection by checking the box then click the properties button and select Automatic configuratio (DHCP) from the pull down menu.

---

### Post by xzero1 on 2007-08-25
> try this. i dual boot with windows, and while in ubuntu if i restart the computer, boot to windows, and get on the internet fine. however, if i restart windows, and boot ubuntu i can't get online. and i'm behind a router, so it should not make any difference. but i have to turn off the computer, modem, and router. turn everything back on in order to get online again in ubuntu.

I would set up a static ip, at least in Ubuntu, since you have a router. My guess is the router is not resetting properly or something.

---

### Post by Controlpanel on 2007-08-25
Ok but I can't copy and paste out of that thing on windows.

---

### Post by xzero1 on 2007-08-25
> Ok but I can't copy and paste out of that thing on windows.

Yes you can. If you select the text then you can use copy paste. Or try this:
Instead of ipconfig /all do ipconfig /all >ipconfig.txt. This creates a text file with the output in it in the current folder.

---

### Post by ayenack on 2007-08-25
Take a look at [this]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5BAirForce_One_54g%5D") for your wifi.

---

### Post by Crafty Kisses on 2007-08-25
> **Controlpanel said:**
> I am new to Linux and cannot run the internet at all. I am dual booting my computer. The internet works fine on Windows but not on Ubuntu. Thanks for the help.

If you're using Wireless, you'd probably have to use a NDISWrapper.

---

### Post by Controlpanel on 2007-08-25
> **Codename said:**
> If you're using Wireless, you'd probably have to use a NDISWrapper.

I know, but how do I download it. Because I can't connect to the internet on Ubuntu so how do I get it on Ubuntu?

---

### Post by oilchangeguy on 2007-08-25
> **Controlpanel said:**
> I know, but how do I download it. Because I can't connect to the internet on Ubuntu so how do I get it on Ubuntu?

until you get this resolved, can you use a wired connection with ubuntu?

---

### Post by Controlpanel on 2007-08-25
> **oilchangeguy said:**
> until you get this resolved, can you use a wired connection with ubuntu?

No I can't thats part of the problem

---

### Post by oilchangeguy on 2007-08-25
> **Controlpanel said:**
> No I can't thats part of the problem

you router should have 1-4 rj45 jacks, for a wired connection. if you don't have a cable, they're cheap.
and if you have a cable going from the modem to the router, use that one. for right now go from the modem direct to the computer.

---

### Post by Controlpanel on 2007-08-25
> **oilchangeguy said:**
> you router should have 1-4 rj45 jacks, for a wired connection. if you don't have a cable, they're cheap.

what does that look like?

---

### Post by oilchangeguy on 2007-08-25
> **Controlpanel said:**
> what does that look like?

what does what look like? and see my previous post. i added to it.

---

### Post by ayenack on 2007-08-25
Has your laptop got a normal modem? If so use that on your phone line.

---

### Post by oilchangeguy on 2007-08-25
> **ayenack said:**
> Has your laptop got a normal modem? If so use that on your phone line.

with linux, good luck.

---

### Post by Controlpanel on 2007-08-25
> **oilchangeguy said:**
> you router should have 1-4 rj45 jacks, for a wired connection. if you don't have a cable, they're cheap.
and if you have a cable going from the modem to the router, use that one. for right now go from the modem direct to the computer.

Whats a modem?

---

### Post by Controlpanel on 2007-08-25
Oh wait I should take the cable from the router and plug it into my computer?

---

### Post by fenian on 2007-08-25
From what I understand you can hook your computer to your router with an ethernet cable and that is detected by the network manager but when you try to connect to the internet with firefox you are unable to do so.Is this correct?

---

### Post by oilchangeguy on 2007-08-25
> **Controlpanel said:**
> Whats a modem?

you have a high speed connection, correct? if so, then most of the time you'll have two boxes. one is a cable modem, and one is your wireless router. do you have this type of set up? do you have dsl (phone company), or cable (tv cable)?

---

### Post by Controlpanel on 2007-08-25
> **fenian said:**
> From what I understand you can hook your computer to your router with an ethernet cable and that is detected by the network manager but when you try to connect to the internet with firefox you are unable to do so.Is this correct?

Yes that sounds correct.

---

### Post by Controlpanel on 2007-08-25
> **oilchangeguy said:**
> you have a high speed connection, correct? if so, then most of the time you'll have two boxes. one is a cable modem, and one is your wireless router. do you have this type of set up? do you have dsl (phone company), or cable (tv cable)?

I have a high speed Comcast internet connection.

---

### Post by oilchangeguy on 2007-08-25
> **Controlpanel said:**
> I have a high speed Comcast internet connection.

then take the router out of the loop. just go from the modem to the computer.

---

### Post by ayenack on 2007-08-25
Originally posted by oilchangeguy
> *with linux, good luck.*

Don't know what that's supposed to mean? Dial is possible with linux.

Also your wired network is the broadcom BCM4401 (rev2) I know for sure that the (rev1) version works out of the box so this may well do also. If you want to get a ethernet cable (for wired network) go to your local PC store and ask them they will direct you to the right cable, might be an idea to take your laptop with you.

---

### Post by fenian on 2007-08-25
What happens if you open firefox and enter the following in the address bar...

> 192.168.1.1

---

### Post by Controlpanel on 2007-08-25
> **oilchangeguy said:**
> then take the router out of the loop. just go from the modem to the computer.

Ok I will have to try that. I was taking the cable out of the router before and plugging it into the computer (I wasn't using the modem) I got the two mixed up. Ok I will try that Later.

---

### Post by oilchangeguy on 2007-08-25
"Don't know what that's supposed to mean? Dial is possible with linux"

possible, yes. probable, no.

---

### Post by Controlpanel on 2007-08-25
> **fenian said:**
> What happens if you open firefox and enter the following in the address bar...

Firefox gives the screen: Can't Find Server

---

### Post by fenian on 2007-08-25
If you are still connected to the router (if you haven't followed the advice to plug directly into the cable modem) with the ethernet cable then there is a problem communicating with the router.Try unplugging the power cord of the router wait at least 30 seconds before plugging it back in then restart ubuntu and try entering that address again.

---

### Post by wormser on 2007-08-25
> Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)


I have the same card and it works out of the box.  

> eth0 Link encap:Ethernet HWaddr 00:14:22:90:98:B0
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:19

eth0:avah Link encap:Ethernet HWaddr 00:14:22:90:98:B0
inet addr:169.254.7.217 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
Interrupt:19 

My eth0 does not have an alias (avah).  Why is his creating an alias?

Try this command: sudo dhclient.  Use your password.  Which version of Ubuntu did you install?

---

### Post by Controlpanel on 2007-08-25
> **wormser said:**
> I have the same card and it works out of the box.  



My eth0 does not have an alias (avah).  Why is his creating an alias?

Try this command: sudo dhclient.  Use your password.  Which version of Ubuntu did you install?

7.04

---

### Post by Controlpanel on 2007-08-25
sudo dhclient 

> Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/eth1/00:14:a5:3e:16:2e
Sending on   LPF/eth1/00:14:a5:3e:16:2e
Listening on LPF/eth0/00:14:22:90:98:b0
Sending on   LPF/eth0/00:14:22:90:98:b0
Sending on   Socket/fallback
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by Controlpanel on 2007-08-25
ok I posted sudo dhclient

---

### Post by Controlpanel on 2007-08-25
...

---

### Post by fenian on 2007-08-25
That means your computer is not communicating with your router.What type of router (manufacturer and model number) do you have?

---

### Post by Controlpanel on 2007-08-25
> **fenian said:**
> That means your computer is not communicating with your router.What type of router (manufacturer and model number) do you have?

I tried connecting to the modem and it said that I have a wired connection established but then it did nothing and I could not connect to the internet still. I have a Motorola SB5120 modem and a Barricade Router.

---

### Post by Controlpanel on 2007-08-25
Does anyone know how I can fix this?

---

### Post by wormser on 2007-08-25
I do not know, but have a feeling that the alias eth0:avah might be causing the problem.  I have the same card but no alias.  I have been looking threw other post and found something to try.  

System> Administration> Network> General tab and uncheck Automatic service discovery.  Then restart you computer and test the connection.  Also do ifconfig to see if the eth0:avah is still there.

---

### Post by Controlpanel on 2007-08-25
> **wormser said:**
> I do not know, but have a feeling that the alias eth0:avah might be causing the problem.  I have the same card but no alias.  I have been looking threw other post and found something to try.  

System> Administration> Network> General tab and uncheck Automatic service discovery.  Then restart you computer and test the connection.  Also do ifconfig to see if the eth0:avah is still there.

Ok thanks, do you think it could be something that Windows put there?

---

### Post by fenian on 2007-08-25
what happens if you type

192.168.2.1  or 192.168.2.2

in the firefox address bar?

---

### Post by wormser on 2007-08-25
> **Controlpanel said:**
> Ok thanks, do you think it could be something that Windows put there?

No.

Also, I have you tried shutting your computer completely down and using the power button to start it?  Sometimes when I click restart from Windows and boot into Ubuntu I cannot connect to the internet with out completely shutting down.

---

### Post by Controlpanel on 2007-08-25
> **wormser said:**
> No.

Also, I have you tried shutting your computer completely down and using the power button to start it?  Sometimes when I click restart from Windows and boot into Ubuntu I cannot connect to the internet with out completely shutting down.

I tried what you said before and the eth0 thing was still there.

---

### Post by nonewmsgs on 2007-08-25
this thread is long and overly arduous.  can someone please clean this up?

did you post the ipconfig page from windows?  now if you click the network thing can you select eth0, or anything other than lo?  also enable automatic addressing with dhcp.

---

### Post by ayenack on 2007-08-26
Try this in terminal.

**sudo -i** To put you in the root terminal. Can't remember if you need to use root so better to be safe than sorry.

**ifconfig eth0 down**

**gedit /ect/network/interfaces **
This will open your network config file look to see if eth0 is listed. If it's not add this to the file.

[B]iface eth0 inet static
adress 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1[/B] (the gateway address may be different from this. It is the first ip of your router check the manuals to find out what this is). This will config your router with a static ip of 192.168.1.2. when you've done this save the file and exit.

Now in terminal type.

**ifconfig eth0 up**

It may be an idea to post the results of 'sudo gedit /etc/network/interfaces' So that we can see what's going on in your network config. Also if there's a listing in network interfaces that say eth0:avah or eth0avahi delete it. Reboot your PC and cross your fingers.

---

### Post by Controlpanel on 2007-08-26
I uninstalled Ubuntu because I was having so many problems with the internet on it. However I really wanted to run Linux, does anyone know some steps that I could take to make sure the internet works next time I install it? Maybe a different wireless card. Something I have to do with Windows. Or even a different Linux distribution. Thank You

---

### Post by Controlpanel on 2007-08-26
So I'm assuming that no one can answer my question, because I really wanted to run Linux.

---

### Post by oilchangeguy on 2007-08-26
> **Controlpanel said:**
> So I'm assuming that no one can answer my question, because I really wanted to run Linux.

after 7 pages, 60+ posts, this thread has run way too long. my advice is to simply try the live cd of different distros to see if it will work with your computer. and go from there.

---

### Post by Controlpanel on 2007-08-26
> **oilchangeguy said:**
> after 7 pages, 60+ posts, this thread has run way too long. my advice is to simply try the live cd of different distros to see if it will work with your computer. and go from there.

You mean like different Linux distributions?

---

### Post by oilchangeguy on 2007-08-26
> **Controlpanel said:**
> You mean like different Linux distributions?

yes

---

### Post by cerebellum on 2007-08-26
where are you connecting to the internet? using modem? LAN?
if u r in the office, do they have DHCP or does the administrator use fixed IP addresses?

---

### Post by xzero1 on 2007-08-27
You need to be a little more cooperative. I have asked you to post ipconfig /all from windows. Since windows works this will give us the correct IP numbers to compare to what you have now and use to troubleshoot your problem.

---

### Post by Controlpanel on 2007-08-28
I wanted to see if my computer could even work with Linux so I ran KNOPPIX and I was still unable to connect to the internet, even using an Ethernet cable. Does anyone have any idea what I am doing wrong or is my computer just at fault?

---

### Post by Controlpanel on 2007-08-28
> **cerebellum said:**
> where are you connecting to the internet? using modem? LAN?
if u r in the office, do they have DHCP or does the administrator use fixed IP addresses?

I have tried using the modem and WLAN.

---

### Post by meindian523 on 2007-08-28
@ControlPanel


Please Please Please post the info xzero is asking for........:mad:

---

### Post by DarkN00b on 2007-08-28
I notice you are using a Broadcom 4318 Airforce1 chipset for wireless... I have that very same chipset and am posting with it right now.

Have a look over [here]("http://ubuntuforums.org/showthread.php?t=405990"). bmartin and I have been working with these Broadcom chipsets and are having about an 81% success rate getting them working. Most of the time one combination of drivers / tools will work.

Anyway, it works often enough that the forum staff has seen fit to sticky the thread.

---

### Post by Controlpanel on 2007-08-30
> **DarkN00b said:**
> I notice you are using a Broadcom 4318 Airforce1 chipset for wireless... I have that very same chipset and am posting with it right now.

Have a look over [here]("http://ubuntuforums.org/showthread.php?t=405990"). bmartin and I have been working with these Broadcom chipsets and are having about an 81% success rate getting them working. Most of the time one combination of drivers / tools will work.

Anyway, it works often enough that the forum staff has seen fit to sticky the thread.

I will have to try that. I hope it works.

---

