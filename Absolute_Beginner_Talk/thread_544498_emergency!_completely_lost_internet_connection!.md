---
title: "emergency! completely lost internet connection!"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by jasonwatkins on 2007-09-06
first of all i apologise for the format of this post as i am writing it on my cellphone as i have no other means of getting online until tomorrow. i have a sagem f@st 800 usb modem and my internet connection was fine until last night when it just dropped the connection and died. when i run firefox it just goes straight to 'server not found'and that's it. my isp told me that my connection wasn't synced and that i had to re create the connection to the modem but i'm not really sure what to do since i've changed absolutely nothing or done anything remotely associated with the modem. i've unplugged it, re booted and tried again but nothing works.  when i try and run the command 'pppd call ueagle-atm' it says the pppd.o plugin is loaded but the ueagle-atm process doesn't run. i hope this rings a bell for someone because i'm desperate! i'll try to reply as much as i can but please bear in mind i'm only on a cellphone for now so i can't cut and paste anything or attach any files! thanks for any help you can give

---

### Post by jasonwatkins on 2007-09-06
another thing. if i type 'ifconfig ppp0' i get an error fetching interface information: device not found error if that helps

---

### Post by jasonwatkins on 2007-09-06
blatant bump because i'm desperate!

---

### Post by jingo811 on 2007-09-06
I can't call myself a Network Wizard yet but I have some tricks up my sleeves if you're on a Wired Network Card.  So answer these questions.

1.)
Are you using Wired or Wireless to connect to the Internet?

2.)
What operating system are you using and which version?

3.)
How long have you used your device on your chosen operating system?

---

### Post by jingo811 on 2007-09-06
Since it's taking you so long to respond copy and paste these commands into terminal and show ppl in here what the outputs are for each respective command.  B'coz I'm off to Windows to play some BF2 :)

This command gives you Network information if you're on a Wired Network Interface Card (NIC).
```
 ifconfig | more
```

This command tells you whether the Wired NIC is connected hardware wise.
```
 sudo mii-tool eth0
```

This one tells your router to give you a new ip-adress if you're using a router.
```
dhclient eth0
```


Other than these tricks I don't know anymore.  Then you just have to go fish for some other Penguin helpers to aid your problem.  Good luck!

---

### Post by jasonwatkins on 2007-09-06
thanks for your reply. my connection is wired. usb connects the modem to the pc and the modem is connected to the phone line with an adsl micro filter. i'm using ubuntu feisty fawn 1.14 which i've used with no problems for about 3 months now.. that's the most frustrating part -i've done nothing different to the operating system at all

---

### Post by irish_flu on 2007-09-06
Qustion: the word "sync" makes me wonder if your DSL modem is even connected to the network.  Did they for sure tell you that your modem was fine?

---

### Post by jasonwatkins on 2007-09-06
i'm very sorry but at the moment i can't cut and paste anything since i'm currently writing there posts on my mobile phone. i ran the mii-tool eth0 command and got 'eth0 no link'as the response. the last part of the dhclient command said 'no dhcpoffers received. no working leases in persistent database' i can't type out the output from ifconfig though,sorry > **jingo811 said:**
> Since it's taking you so long to respond copy and paste these commands into terminal and show ppl in here what the outputs are for each respective command.

---

### Post by jasonwatkins on 2007-09-06
truth be told, during my conversations with their (terrible) support team nobody actually said 'your modem is 100% fine' but then i only really asked them to check the connection and the line. another thing that might help is when i run the command 'poff'to disconnect the modem it says 'no pppd is running. none stopped'

---

### Post by LowSky on 2007-09-06
they probably checked the line but not the modem

i bet the modem went bad, these things happen

it happened twice to me,

---

### Post by nikef on 2007-09-06
cant help much
but i noticed micro filter,check that as bt workman told me,they can get faulty 
re-boot the modem

hope you get it sorted,so frustrating when theres no internet

---

### Post by jasonwatkins on 2007-09-06
when i reboot and look in the sys log, i see 'pppd 2.4.4 started by root, uid 0' then 'connect(0.38 ) : no such device' then exit. before that i get 'ADDRCONF(NETDEV_UP): eth0: link is not ready'

---

### Post by jasonwatkins on 2007-09-06
again, many apologies for the blatant bump but i've just spent the last 2 hours banging my head against a wall trying to work this out and i'm just utterly lost. ideally i'd reformat and start again but i have 15gb of music on my hard drive and no current means of backing it up

---

### Post by jasonwatkins on 2007-09-07
bumped again, sorry

---

### Post by jingo811 on 2007-09-07
4.)
run these 2 commands in your terminal and write down outputs on a piece of paper with a pen.  And post the ouputs in here!
```
mii-tool
``` and
```
sudo mii-tool
```

5.)
Do you have a Dual Boot setup with Windows XP or something so you can tell whether it's Ubuntu that's having problem.  Or if it's some hardware specific problems?

6.)
```
ifconfig
```
Write down on a piece of paper the output you get from the first 3 rows!  I want to make sure whether you're using eth0 or if it's some other NIC you're using.
( You don't have to show us your real NIC address just put in HWaddr **:**:**:**:**:** or something. )

7.)
Is it possible to persuade your modem distributor to loan you another unit of modem to test if your old modem is really malfunctioning or if the problem is Ubuntu related?

---

### Post by jasonwatkins on 2007-09-07
right, i'm in my local library so i can at least type out a post properly ! :)

ok, when i run mii-tool it says

"eth0 no link"

i've got some output from various files to past here, so hopefully that might help.

this is the output when i run "ifconfig"

```
eth0      Link encap:Ethernet  HWaddr 00:**:**:**:**:**
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xe000

eth0:avah Link encap:Ethernet  HWaddr 00:**:**:**:**:**
          inet addr:169.254.7.214  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3856 (3.7 KiB)  TX bytes:3856 (3.7 KiB)
```

this is taken from the syslog output straight after the system reboot

```
Sep  6 21:25:41 Kirsty pppd[5543]: Plugin pppoatm.so loaded.
Sep  6 21:25:41 Kirsty pppd[5544]: pppd 2.4.4 started by root, uid 0
Sep  6 21:25:41 Kirsty pppd[5544]: connect(0.38): No such device
Sep  6 21:25:41 Kirsty pppd[5544]: Exit.

```

this is the output when i run "dhclient eth0"

```
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:15:58:c2:9a:7a
Sending on   LPF/eth0/00:15:58:c2:9a:7a
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

i've also attached the entire syslog file from the point where I restarted the system.

i don't currently have a dual boot system set up to test the modem, but i think that's going to be something i'm going to have to do - i can't really see a way of testing it out under wine at the moment.

i guess the ultimate solution is to find a way of backing up my 15gb's worth of music and re-formatting.

but if it's something that can't be fixed then i'm going to have to go back to windows full time and i don't really want to do that ..

thanks for all your help and patience so far :)

---

### Post by jasonwatkins on 2007-09-07
actually, i suppose if i back up my music, i won't largely matter what i do because i can re-format to my hearts content there :D

---

### Post by jasonwatkins on 2007-09-07
i'm just leaving my library, so any further posts in this thread from me will be from cellphone ..

or if i can find 5 blank DVD's from somewhere, maybe from some form of decent internet connection ..

so i'm bumping .. again .. sorry

---

### Post by jingo811 on 2007-09-07
When you run **ifconfig** the below output is something new to me and you keep mentioning **pppd** something which I have never played with before.  I don't think I can help you much further.  You'll just have to wait for some pppd guys to answer your call.

```

eth0:avah Link encap:Ethernet  HWaddr 00:**:**:**:**:**
inet addr:169.254.7.214  Bcast:169.254.255.255  Mask:255.255.0.0
UP BROADCAST MULTICAST  MTU:1500  Metric:1
Interrupt:18 Base address:0xe000

```

Installinging Dual Boot Ubuntu/Windows XP is the perfect marriage I think.  You'll be better equipped for handling hardware and Linux kernel malfunctions in the future.  When Ubuntu breaks you can still access Internet with Win XP.  If Windows breaks you can use Ubuntu to access the Internet.


> ok, when i run mii-tool it says

"eth0 no link"
If I'm not mistaken that output says that there's something wrong with your physical Network Card in your PC.  It might have been fried happend to me once.  Internet worked on Windows for 10 years then one day it just went down.  Might have happened to you too!

---

### Post by jingo811 on 2007-09-07
Before I abandon you what does it output exactly when you typed this in terminal?
```
 sudo mii-tool
```

---

### Post by jasonwatkins on 2007-09-07
if i type it exactly as you have then i get 'eth0: no link' and if i type it under my id then i get 'SIOCGMIIPHY on eth0 failed: operation not permitted' and this is the same for eth0 through eth7. at the end i get 'no MII interfaces found'. i'm backing up my music so i'll check back when that's done in an hour and then i'm re formatting. thanks so much for your help so far

---

### Post by jingo811 on 2007-09-07
See how Windows handles your Wired NIC card?  If Windows also fails consider that your NIC migh have been **fried**.  Try and get a new NIC card to test.  If that doesn't work there must be problem with your SAGEM modem.

---

### Post by jasonwatkins on 2007-09-07
well when vista finished installing i ran the modem installation disk the same way i'd done a hundred times before and it installed the drivers but did NOT tell me to unplug and re plug in the modem-which it has also done a hundred times before. i did it anyway and vista detected new hardware so i pointed the wizard at the modem drivers and it said it couldn't install them. so i rang the jackasses at the call centre who decide to tell me that the sagem wasn't compatible with vista which is a total lie since i was using it on vista before i switched to linux. he did tell me he'd send me a new modem which might be an ethernet one by the sounds of it but i won't get it until next friday. so the upshot is i have an empty machine that isn't compatible with most of the games i have! bloody thing

---

### Post by jasonwatkins on 2007-09-07
going to bump one last time just in case anyone has any different ideas

---

### Post by jingo811 on 2007-09-08
While you wait for ppl who's experienced the same thing as you.
And while you wait for your SAGEM modem until next friday.

I suggest that you start looking around for an internal ethernet Network Interface Card to purchase (just in case).
They shouldn't be that expensive nowadays.  You might buy and replace it with your old one to see if things will change during this week.  Or you could wait until after next Friday to purchase it to see if your old NIC is really fried and damaged.

---

### Post by jasonwatkins on 2007-09-10
well i'm definately getting a new ethernet modem, so that'll be good.

i'm not too worried about the NIC card situation largely because my PC is still under guarantee because I only got it in April.

so if the worst comes to the worst and it is fried, i'll just send it back for repair.

interestingly enough though, since I didn't actually have Ubuntu on disk anywhere, i decided to download and install Linux Mint, which I must confess to being slightly more impressed with than Ubuntu :D

(and i prefer minty green to orange anyway .. hehe ..)

---

### Post by surfdoc on 2007-09-10
If your suffering from the same problem as me, then it's down to the new kernel release.
Actually this happens to me every time there is a new kernel update, so i'm well used to it now. To get you connection going again, simply select the old kernel at boot in grub. 

Should be 2.6.20-15-generic (new one is 20-16)

This should get you back online, where you can then work on fixing the new kernel if you can be bothered. Unfortunately i can't remember what i had to do last time to get the latest kernel working. Probably had to install new kernel module for ueagle-atm

Hope this helps.

---

### Post by jasonwatkins on 2007-09-10
hi and thanks for your reply. i actually think the problem is either the modem or the nic card because when i plug the modem into the usb port the PWR light and ADSL lights are both on and solid all the time -even when i unplug it from the phone line and the micro filter and completely unplug and re plug it as well

---

### Post by surfdoc on 2007-09-11
Sounds reasonable. Just so you know, when i booted with the latest kernel, my modem showed both lights on, but wouldn't connect to the internet. Hope you sort it out soon!

---

### Post by jingo811 on 2007-09-11
> Actually this happens to me every time there is a new kernel update, so i'm well used to it now. To get you connection going again, simply select the old kernel at boot in grub.

Should be 2.6.20-15-generic (new one is 20-16)

If I'm not mistaken he said that he tried connecting on his Windows Vista partition last week and it didn't work like before so I don't think he has some kernel issues.

---

### Post by Ant_Merlin on 2007-09-11
Hi, just caught up on this post, You are using sagem modem which is USB so your NIC adapter which is cat 5/6 will show not connected because you connect through USB so no probs with your NIC card, its simply not being used. PPPD is the type of Broadband you have (Point to Point Protocol). Have you tried connecting the modem to a different USB slot?, this should get a reinstall (I am totally new to linux but it works in windows) for the modem. when you run ifconfig it suggests that you have been given an IP address 169.***.***.***. which suggests you modem may have recieved it from your ISP, suggesting it works.

Have you run network tools in system, administration menu?

---

### Post by jasonwatkins on 2007-09-11
that's right. vista detects i've plugged something in, but doesn't want to install the drivers. i've even re-formatted to linux mint and followed the same procedure to get the sagem connected and just get the same problem. essentially whenever the modem is plugged into the usb port, regardless of operating system, both lights are on and solid. in an ideal world my ethernet modem will arrive tomorrow but then my luck doesn't work like that!

---

### Post by jasonwatkins on 2007-09-11
i did run network tools but to be honest i wasn't entirely sure what i was looking for. i've tried the modem on different usb ports with no luck but since i'm sitting here bored out of my head, i may well try again!

---

### Post by Officer Dibble on 2007-09-11
Have you checked all the cable connections? What I mean by check is disconnecting and reconnecting them ensuring that anything and everything related to your Internet connection is properly seated?

---

### Post by jasonwatkins on 2007-09-11
i've checked all the cables and they are ok, although for the sake of argument i'm going to try the usb ports on the back again

---

### Post by jingo811 on 2007-09-11
I Googled this it seems like your modem is one piece of work :)
```
sagem f@st 800 usb modem problems
```
[http://www.google.se/search?q=sagem+f%40st+800+usb+modem+problems&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.se/search?q=sagem+f%40st+800+usb+modem+problems&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

---

### Post by jasonwatkins on 2007-09-11
i'll check that out when i'm properly back online-thanks! i think the main thing that seals the deal that the modem is fried is when i unplug it from the micro filter so there's no connection to the network at all, the ADSL light is still on and solid. according to the manual, this means its connected when it clearly isn't :D

---

### Post by jasonwatkins on 2007-09-14
this ..

[IMG]http://ec1.images-amazon.com/images/I/21EelbxbHkL._AA160_.jpg[/IMG]

is what i'm getting.

> Product Features and Technical Details
Product Features 
COMPATIBLE WITH THE NEW WINDOWS VISTA, PC AND MAC 
Small and Smart, plug and play, stable, easy set-up wizard, remote management 
ADSL2+ Downstream rate of 26 Mbps, upstream rate of 1M bps, 
1483B bridging and routing function, DHCP server, NAT/NAPT, PAP/CHAP, IP Filter, Firewall, protocol block, Built-in PPPOE/PPPOA dialing 
MT882 gives full consideration to the household arrangements, enabling horizontal and vertical positions as well as hanging on the wall. 
Technical Details 
Standarts: ITU G.992.1 (G.dmt), ITU G.992.2 (G.lite), ITU G.994.1 (G.hs),
WAN: One RJ-11 port for ADSL; LAN: One USB port for USB cable & One RJ-45 port for 10/100 Base-T Ethernet
LED Indicators Power, ADSL Link , ADSL ACT, LAN Link ,USB
Operating Temperature: 0°C - 40°C ( 32 - 104°F)
AC: 90~240V, power adapter: 9 V AC 1A 

it's been dispatched, so i should get it any day now :D

---

### Post by jingo811 on 2007-09-14
There's one thing that I'm still confused about.  Are you connecting your modem cable to your computer with a USB connector?
Does the modem have any holes for using TCP/IP connectors instead?  So that you can have TCP/IP cables between your modem and your PC's built-in Ethernet Network Card?

---

### Post by jasonwatkins on 2007-09-14
the modem is (or was in this particular case!) strictly usb only - one port for the phone connection and one for the usb connection

---

### Post by jingo811 on 2007-09-14
But now you have the option to use Ethernet TCP/IP cables to connect to your PC right?
By the way is the problem solved with the new modem?

---

### Post by jasonwatkins on 2007-09-15
the new modem hasn't arrived yet :D

it was dispatched last wednesday, so it could arrive any day now ..

i am posting here using a combination of my cellphone and my local library.

but to answer your question, yes I will be able to use an ethernet connection with the new modem.

---

### Post by quinnten83 on 2007-09-15
if your library has a very fast connection and allows you to use P2P, you might be able to download an XP live cd (much like ubuntu, but with XP). You can then try running it to see if it then works.
I think there might be a problem with your modem/ connection.  If i remember correctly 169.xxx.xxx.xxx is an internal IP number and if you are using a USB modem, you should have an IP number which your ISP assigns to you. I don remember USB modems having an internal DHCP.
My advice, never go with USB modems if at all possible.

---

### Post by jasonwatkins on 2007-09-15
> **quinnten83 said:**
> I think there might be a problem with your modem/ connection. it's most definately the modem. the line has been tested and is fine. if i was able to find a direct download for an XP live cd then i'd try it but i'm 99% certain it wouldn't make any difference at all.

---

### Post by jasonwatkins on 2007-09-21
i'm baaaacckk :D

i've got an addon arm8200 ethernet modem and it's working fine, so i think it most certainly proves it was the modem all along.

i'm connected through vista at the moment, so i need to go off and find out how to set up the connection for linux then i'll be reformatting as soon as i can.

smelly vista :lolflag:

---

### Post by jasonwatkins on 2007-09-21
actually if anyone can point me in the direction of a guide to set up my ethernet modem in ubuntu then i'd be grateful .. cheers ..

---

### Post by jasonwatkins on 2007-09-21
scratch that .. it seems to be working.  i'm on linux mint actually and not ubuntu now, and mint seems to have detected it and set it up and everything is cool.

glad to be back on linux in any sense though :D

---

### Post by jingo811 on 2007-09-22
Now you're ready to live life Neo and remember There is no spoon :)

---

### Post by jasonwatkins on 2007-09-23
i was actually quite surprised at the strength of my desire to get windows off my machine as soon as humanly possible ...

---

