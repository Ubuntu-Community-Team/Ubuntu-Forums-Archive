---
title: "Another wireless internet problem"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by Rustafur on 2007-07-20
Sorry if this is just another re-hash of a similar problem, but I didn't want to steal anyone's thread and I haven't yet found a solution for my problem, so I thought I'd just start fresh.

Here's the problem: I installed 7.04 last night on an old Dell Inspiron 5100 laptop that uses a USR 5140 wireless network card, and I can't quite get it to connect to the internet through my Linksys wireless router. I know the card and laptop are in fine shape, as it would connect just fine when Windows XP was installed. Here's what happens, there seems to be some kind of a connection to the router as the Network Connection icon in the upper left of the desktop changes from the "no-connection" icon to the 5 bars representing signal strength. So I would assume there is some kind of a connection being made. The update manager was even able to establish enough of a connection to realize that there are 62 updates available for download. However, if I try to access the internet through Firefox, ping another computer on my network, or try to download the updates from my Update Manager, I can't get a connection. 

Here's some information...

When I run ifconfig -a I get..

```
adam@laptop1:~$ ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:0B:DB:19:52:B7   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:7  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:300 (300.0 b)  TX bytes:300 (300.0 b) 
 
wlan0     Link encap:Ethernet  HWaddr 00:C0:49:E9:D0:5B   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:280 (280.0 b)  TX bytes:336 (336.0 b) 
          Interrupt:11
```

When I run iwconfig I get...

```
adam@laptop1:~$ iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wlan0     IEEE 802.11b+/g+  ESSID:""  Nickname:"acx v0.3.36" 
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated    
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3   
          Retry min limit:7   RTS thr:off    
          Power Management:off 
          Link Quality=54/100  Signal level=36/100  Noise level=0/100 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Since I'm still VERY new so the iwconfig doesn't make a whole lot of sense to me, so if someone could point me to some place that would help explain that too, I'd sure appreciate it. Thanks in andvance

---

### Post by ddrichardson on 2007-07-21
> **Rustafur said:**
> When I run iwconfig I get...

```
adam@laptop1:~$ iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wlan0     IEEE 802.11b+/g+  ESSID:""  Nickname:"acx v0.3.36" 
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated    
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3   
          Retry min limit:7   RTS thr:off    
          Power Management:off 
          Link Quality=54/100  Signal level=36/100  Noise level=0/100 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Since I'm still VERY new so the iwconfig doesn't make a whole lot of sense to me, so if someone could point me to some place that would help explain that too, I'd sure appreciate it. Thanks in andvance

ESSID identifies the wireless router you're connecting to - in this case none. Nickname is mostly irrelevant. Everything else is what it says on the tin.

Have you tried network-manager to see the router is available?

---

### Post by User X on 2007-07-21
Rustafur, I to am very new and I am afraid I cannot offer you much help but I wil let you know that I am in the same boat.  I am using a marvel chip based on board wireless nic.  I have installed ndiswrapper, and the windows XP driver.  iwconfig shows my essid, as well as my connection strength to the network, however I cannot access the internet through my linksys wireless router (using firefox).  Possibly it is our routers???  If you figure it out please post back to let me know what the problem was - I have been battleing with this for almost 3 weeks...  It's getting old...  Have you tried to connect with a hard line instead of wirelessly?

---

### Post by ugm6hr on 2007-07-21
Do you have encryption on?  The acx drivers were not capable of encryption previously...

```
lspci
```

This will confirm the chipset, and give a place to start.

---

### Post by thefoolisme on 2007-07-21
If all else fails, try WiCD     [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)   

I worked for days on the wireless problem with my laptop and Linksys access point.  I installed this, and it worked great!  

It seems to be a failsafe for those who have done everything else to get their wireless working.

---

### Post by Rustafur on 2007-07-22
Thankyou everyone that replied! The Ubuntu forums are an awesome community, I'm proud to be a part!

**ddrichardson** - Thanks for the short explanation of iwconfig. Yes I had checked the Network-Manager, and my router did appear automatically. So it seemed like my card and router could see each other, they just couldn't resolve the connection.

**ugm6hr** - lspci gave me this out put:

```
02:04.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:04.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
03:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
```

So I assume that my chipset is Texas Instruments ACX 111?

**thefoolisme** - WiCD did the trick! It found me router and I had an IP address and resolved connection straight away.

User X - hope this helps you! WiCD worked perfectly for me.

Thankyou again to those that helped! I'd buy ya'll a round if I could.

---

