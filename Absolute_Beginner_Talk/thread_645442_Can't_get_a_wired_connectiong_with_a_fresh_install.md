---
title: "Can't get a wired connectiong with a fresh install gutsy"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by Chris1091 on 2007-12-20
Hey guys,

New user here.  I'm having trouble getting a wired connection with a fresh install of Ubuntu 7.10.  Both are recognized in lspci as well as in the network settings.  The chips are:

nVidia nForce2 ethernet controller 
and
Marvell 88E8001 gigabit ethernet controller

I'm also having problems getting my wireless broadcom 4303 to connect, but I'll worry about that later..

Maybe (hopefully, rather) I'm missing an obvious step, I won't subjugate myself as not being naive.  I've been trying to follow all the threads and tutorials I can find, but no such luck yet.  

Thanks,
Chris

---

### Post by shadow-of-sin on 2007-12-20
Try disabling IPv6, you can find a guide here:
[http://www.simonscullion.com/2007/11/20/ipv6-issues-with-ubuntu-710/](http://www.simonscullion.com/2007/11/20/ipv6-issues-with-ubuntu-710/)

As for your wireless, the broadcom 4303 chipset has been reported to work with NDISwrapper.

---

### Post by Chris1091 on 2007-12-20
Thanks for the quick reply, Shadow.

I tried disabling the IPv6 with those instructions, as well as with a previous set of similar instructions, to no luck.  Any other ideas?

Chris

---

### Post by Presto123 on 2007-12-20
Unfortunately, the quickest way for me to tell you how to get the Broadcom would need a wired connection.

If you get your wired up and running, you can go into (on your panel) System/Administration/Restricted Drivers Manager. It will show that you have the Broadcom wireless. Click on it to enable, then it will update packages, and give you a prompt for where to get the driver. Easiest way is to select the second option for "download from internet". It will get the right package and have it installed in no time.

---

### Post by Chris1091 on 2007-12-20
Is there any way to download the necessary restricted drivers from a separate computer and transfer them over for install?

---

### Post by Presto123 on 2007-12-20
Yeah, there is, I'm just not sure where the file was located. Someone else will know this, though. But, you can TRY using what is in this thread:
[http://ubuntuforums.org/showthread.php?t=644231](http://ubuntuforums.org/showthread.php?t=644231)

---

### Post by Presto123 on 2007-12-20
AH...Yes. Get that download the fellow posted at the bottom, extract it, and double click on the file marked "installer.py".

---

### Post by GSF1200S on 2007-12-20
Please post the results of the following codes (put them in a terminal):

```
lspci
```

```
ifconfig
```

```
cat /etc/network/interfaces
```

And for the whole broadcom thing, just out of curiosity post the results of:

```
iwlist scanning
```

```
iwconfig
```

Usually ethernet works out of the box.. did you have the internet hooked up when you installed? If not, it probably just didnt setup the network interface for your ethernet. Once we get that going, well look at the broadcom... ;)

---

### Post by the Didey on 2007-12-20
you might want to at least check out the suggestions on [this thread]("http://ubuntuforums.org/showthread.php?t=603154&highlight=turn+off+roaming"). It seems that sometimes you interface configurations go haywire when you try to setup at the install. 

My devices were showing up in network manager and and in network tools but weren't connecting. After restoring my /etc/network/ interfaces as per the instruction in the thread I was able connect.


I hope it helps.

---

### Post by GSF1200S on 2007-12-20
Hehe.. sorry.. I just realized- duh- he cant post anything if he doesnt have internet.

Perhaps you have a thumb drive and you could save the results in a .txt and post them from your computer with internet.

The main ones I need are

ifconfig

iwconfig

cat /etc/network/interfaces

iwlist scanning

---

### Post by Chris1091 on 2007-12-20
> **Presto123 said:**
> AH...Yes. Get that download the fellow posted at the bottom, extract it, and double click on the file marked "installer.py".

Presto, thanks for digging that up for me.  However, after installation the wireless option has disappeared.  There is no recognition of the wireless in the network settings.  

GSF, I'll get those to you in a minute.  I have a working computer here with me as well.  Also, you're right, I didn't install with the ethernet connected.

---

### Post by Chris1091 on 2007-12-20
Ok, after reinstalling the firmware provided from the link on that page the wireless connection option reappeared.  

GSF, here's the results from the various commands:

> chris@chris-desktop:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
01:07.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
01:07.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
01:07.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
01:08.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)
01:09.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 04)
03:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
03:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)





chris@chris-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0E:A6:1C:23:26  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:0E:A6:1C:10:F9  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:833 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:53312 (52.0 KB)  TX bytes:3956 (3.8 KB)
          Interrupt:20 

eth1:avah Link encap:Ethernet  HWaddr 00:0E:A6:1C:10:F9  
          inet addr:169.254.6.204  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5208 (5.0 KB)  TX bytes:5208 (5.0 KB)





chris@chris-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback






chris@chris-desktop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth2      No scan results



chris@chris-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

eth2      IEEE 802.11b  ESSID:off/any  Nickname:"Broadcom 4301"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

chris@chris-desktop:~$ 

I tried to space them out a bit to make it less an eye-sore.  Also, this was with a wired connection hooked up to the marvell adapter.  

Thanks again for your continued support here, guys.  :thumbup:

---

### Post by shadow-of-sin on 2007-12-20
Ah, the /etc/network/interfaces seems to be the problem, it should look like this:
```
auto eth0
iface eth0 inet dhcp
```

After changing it restart networking and it should now work:
```
sudo /etc/init.d/networking restart
```

---

### Post by GSF1200S on 2007-12-20
> **shadow-of-sin said:**
> Ah, the /etc/network/interfaces seems to be the problem, it should look like this:
```
auto eth0
iface eth0 inet dhcp
```

After changing it restart networking and it should now work:
```
sudo /etc/init.d/networking restart
```

Beat me to it ;)

Yeah, add that to your /etc/network/interfaces and put in that command. Since you had no connection at install, it simply skipped setting up your ethernet.

**EDIT** Once you have your ethernet setup, you should be able to enable the restricted drivers for your broadcom wireless card. And just a little clarification- keep the lo portion of the /etc/network/interfaces.

As an example, it should look like this when youre done:
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The ethernet network interface
auto eth0
iface eth0 inet dhcp

---

### Post by darkrider2k6 on 2007-12-20
I've been having the same problem as Chris1091. The strange thing to me is that the internet connection was fine when I booted from the LiveCD last night, but the internet doesn't work for the hard drive installation that I set up today, and it no longer works when I try booting again from the LiveCD. I'm able to "connect" to my home wireless network (with a connection strength of ~70%), but I can't actually get online--updates won't download, pings don't work, and I can't bring up webpages.

I know that it's definitely not a problem with my network (I'm using another laptop on wireless to write this post), and the same problem occurs when I try a wired connection. 

And, I've edited my interface file to look exactly as you've posted.

I could post the results of the various relevant terminal commands, but they're all fairly similar to Chris1091's. Do you guys have any more suggestions?

---

### Post by shadow-of-sin on 2007-12-20
Did you try and disable IPv6?

---

### Post by darkrider2k6 on 2007-12-20
Yep.

---

### Post by Chris1091 on 2007-12-20
Still no luck.  Here's what the commands read now:

> chris@chris-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0E:A6:1C:23:26  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1662 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:100002 (97.6 KB)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:0E:A6:1C:10:F9  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2525 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:161600 (157.8 KB)  TX bytes:4994 (4.8 KB)
          Interrupt:20 

eth0:avah Link encap:Ethernet  HWaddr 00:0E:A6:1C:23:26  
          inet addr:169.254.2.249  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:53 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4072 (3.9 KB)  TX bytes:4072 (3.9 KB)

chris@chris-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp







chris@chris-desktop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

chris@chris-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

chris@chris-desktop:~$ 



Again this is hardwired to the Marvell adapter.  

Depending on your input, I may just completely reinstall while hardwired.  After running several firmware changes and a few other programs such as fwcutter and ndiswrapper, something may have been modified beyond my knowledge.  

As with darkrider, attempts to ping 82.211.81.158 returns no results.  No pages are able to be opened with firefox.  

Chris

---

### Post by darkrider2k6 on 2007-12-20
Chris1091, does your internet work when you boot from the LiveCD?

---

### Post by GSF1200S on 2007-12-20
> **darkrider2k6 said:**
> I've been having the same problem as Chris1091. The strange thing to me is that the internet connection was fine when I booted from the LiveCD last night, but the internet doesn't work for the hard drive installation that I set up today, and it no longer works when I try booting again from the LiveCD. I'm able to "connect" to my home wireless network (with a connection strength of ~70%), but I can't actually get online--updates won't download, pings don't work, and I can't bring up webpages.

I know that it's definitely not a problem with my network (I'm using another laptop on wireless to write this post), and the same problem occurs when I try a wired connection. 

And, I've edited my interface file to look exactly as you've posted.

I could post the results of the various relevant terminal commands, but they're all fairly similar to Chris1091's. Do you guys have any more suggestions?

Sure do :) First, do a scan for active networks-

```
iwlist scanning
```

Make sure you note which interface is listing scan results. For example, well say the ath0 is showing scan results. When you find your network, input it in the following command (for example: mynetwork)

sudo iwconfig ath0 essid "mynetwork"
sudo iwconfig ath0 key mywepkey123     (if no wep or security is on the network, negate)
sudo dhclient ath0

if this doesnt work, please post

cat /etc/network/interfaces

iwlist scanning

iwconfig

Good Luck!!

---

### Post by darkrider2k6 on 2007-12-20
No luck yet. :(

Here's what my terminal says:

> 
ubuntu@ubuntu:~$ sudo iwconfig eth1 essid "HomeNetwork"
ubuntu@ubuntu:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:13:02:ac:d1:31
Sending on   LPF/eth1/00:13:02:ac:d1:31
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.



ubuntu@ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp



ubuntu@ubuntu:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0F:66:E0:25:FB
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=74/100  Signal level=-60 dBm  Noise level=-60 dBm
                    Extra: Last beacon: 100ms ago

ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"HomeNetwork"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:E0:25:FB   
          Bit Rate:11 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=73/100  Signal level=-61 dBm  Noise level=-62 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1455   Missed beacon:0



---

### Post by GSF1200S on 2007-12-20
I noticed that the scan showed the network as hidden.  Go into the router settings and make sure its not, at least until we get a good connection established.

Is the router itself setup for dhcp? If its set up for static only and you are running dhcp, that could cause a problem.

Try:

sudo ifdown eth1

and then:

sudo ifup eth1

Then:

sudo iwconfig eth1 essid networkname
sudo dhclient eth1

It almost seems as if its router setup issues.. is the other computer an Ubuntu machine or is it windows?

---

### Post by darkrider2k6 on 2007-12-20
I ran those commands, but no progress yet. Did you mean for me to post the terminal responses to those commands?

As far as the network goes, it is set up for dhcp. The laptop I'm typing on is running on a plain Windows XP installation, and two other laptops on the wireless network are running on XP and Vista. The network itself is hidden, and unfortunately I won't be able to change that for another few hours. I would be surprised if that is the cause of the problem, though, especially since Ubuntu was able to connect to the same network just last night without a problem.

The thing that baffles me is that the network connection worked last night when Ubuntu booted from the LiveCD, and now it doesn't. The only thing that has changed since then is that I installed Ubuntu onto my hard drive--but that shouldn't matter at all since I'm still running Ubuntu from the LiveCD, right?

---

### Post by GSF1200S on 2007-12-20
> **darkrider2k6 said:**
> I ran those commands, but no progress yet. Did you mean for me to post the terminal responses to those commands?

As far as the network goes, it is set up for dhcp. The laptop I'm typing on is running on a plain Windows XP installation, and two other laptops on the wireless network are running on XP and Vista. The network itself is hidden, and unfortunately I won't be able to change that for another few hours. I would be surprised if that is the cause of the problem, though, especially since Ubuntu was able to connect to the same network just last night without a problem.

The thing that baffles me is that the network connection worked last night when Ubuntu booted from the LiveCD, and now it doesn't. The only thing that has changed since then is that I installed Ubuntu onto my hard drive--but that shouldn't matter at all since I'm still running Ubuntu from the LiveCD, right?

I just noticed- you put in HomeNetwork as the essid, but you just said its hidden. Im foggy here because I always connect by essid. But what are you using for the network name? iwconfig isnt going to know which network you want if the network is hidden and youre inputting a different name. Im almost willing to gaurantee that revealing the network will let you connect fine.

Now, this isnt a solution- obviously you want it hidden for a reason. If I knew the commands to connect to a network some other way than essid, wed be fine right now...

Funny thing is, you seem to have a link, you just cant seem to get an IP address. You let me know what happens when you reveal with network and try it again, and ill do research- 

Once we get internet by terminal, we still have to figure out the Network manager. Hang in there- you seem to be an unlucky one ;) Ive had these wireless weirdo's before but now everything goes smooth..

**EDIT** Try this command as mentioned earlier- I should have mentioned this above:
sudo /etc/init.d/networking restart

---

### Post by darkrider2k6 on 2007-12-20
I've been running "sudo /etc/init.d/networking restart" as appropriate, so no need to worry about that.

"HomeNetwork" actually is the name of our network. Uncreative, I know, but it wasn't my call. Since the network icon in the system tray (or whatever it's called in Ubuntu) shows blue vertical bars and on mouseover reads, "Wireless network connection to 'HomeNetwork' (73%)," I think iwconfig was able to work without a problem.

At any rate, I'll try changing the network settings ASAP (probably one or two hours), and I'll post with an update. If you're able to find anything or get any new ideas in the meantime, go ahead and post--I'll still be here.

Thanks so much for your help. I really appreciate it!

---

### Post by darkrider2k6 on 2007-12-20
Ok, I'm back with an update!

I changed the router settings to broadcast the network SSID, so HomeNetwork is no longer hidden. After rebooting and checking settings and everything, though, my laptop still can't get online. It's the same problem as before: it'll connect to the network, but it can't connect to the internet. The other 3 laptops on the network are still surfing the web just fine.

This seems like a fairly basic issue, so I'm sure someone has encountered a similar problem before. Does anybody have any ideas?

---

### Post by Chris1091 on 2007-12-20
Hey guys,

I tried completely reinstalling with the ethernet connected, disabled ipv6, as well as changed the /etc/network/interfaces to include the eth0 commands, and am still not getting a connection.

Here's the latest log:

> chris@chris-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0E:A6:1C:23:26  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:0E:A6:1C:10:F9  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3223 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:206272 (201.4 KB)  TX bytes:3893 (3.8 KB)
          Interrupt:20 

eth0:avah Link encap:Ethernet  HWaddr 00:0E:A6:1C:23:26  
          inet addr:169.254.2.249  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:200 errors:0 dropped:0 overruns:0 frame:0
          TX packets:200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15064 (14.7 KB)  TX bytes:15064 (14.7 KB)

chris@chris-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp





chris@chris-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

eth2      IEEE 802.11b  ESSID:off/any  Nickname:"Broadcom 4301"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

chris@chris-desktop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth2      No scan results

chris@chris-desktop:~$ 


still no luck.

---

### Post by Chris1091 on 2007-12-20
> **darkrider2k6 said:**
> Chris1091, does your internet work when you boot from the LiveCD?

No, it doesn't work from the liveCD either.  I made sure to do all the download and CD verifications when I got it, all passed.

---

### Post by Chris1091 on 2007-12-20
any other ideas?

---

### Post by Chris1091 on 2007-12-21
I just got the wireless up and running following VON_CAPO's instructions here:  :thumbup:

[http://ubuntuforums.org/showthread.php?t=583052&highlight=enable+firmware+broadcom](http://ubuntuforums.org/showthread.php?t=583052&highlight=enable+firmware+broadcom)

any recommendations now that I have internet access to get wired access?

---

### Post by The Tronyx on 2007-12-21
Chris, could you please go to your network manager in gnome and take a screenshot (or tell us in great detail) any connections listed on the general tab and the properties of any listed wired connections?

Thanks

---

### Post by GSF1200S on 2007-12-21
Darkrider, please post the results of the following:

lshw -C network

lspci

What card you have? If you are using built in firmware drivers, I would suggest you use ndiswrapper.

You could try using wifi radar (in add/remove) and see if you can connect that way.

---

### Post by jan quark on 2007-12-21
Same issue for me. Have  a desktop PC with a AVM fritz usb stick with ubuntu gutsy. There everything worked out of the box.

But on my laptop with the broadcom 4311 chipset I have the same problems as mentioned above. Read all:) the post dealing with this issue but none worked for. For a moment i have thought that the software updates after a fresh install mess something up so I disabled them. It worked till the next restart of the system.

I like Ubuntu very much and I know it can work out of the box, but I do not really want to have a laptopt without inet so help would be much appreciated.

---

### Post by billgoldberg on 2007-12-21
If the network manager won't connect you to the internet, remove it and try [wicd]("http://wicd.sourceforge.net/") to connect to the internet (wired and wireless, it worked for me with feisty, didn't need it in gutsy).
(download the deb file)

---

### Post by darkrider2k6 on 2007-12-21
> **GSF1200S said:**
> Darkrider, please post the results of the following:

lshw -C network

lspci

What card you have? If you are using built in firmware drivers, I would suggest you use ndiswrapper.

You could try using wifi radar (in add/remove) and see if you can connect that way.

Here's what lshw -C network shows:

> 
*-network
description: Ethernet interface
product: 82573L Gigabit Ethernet Controller
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 00
serial: 00:0e:7b:77:a5:ef
capacity: 1GB/s
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.5-1 latency=0 link=no module=e1000 multicast=yes port=twisted pair

*-network
description: Wireless interface
product: PRO/Wireless 3945ABG Network Connection
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:03:00.0
logical name: eth1
version: 02
serial: 00:13:02:ac:d1:31
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () latency=0 link=yes module=ipw3945 multicast=yes wireless=IEEE 802.11b

And lspci:
> 
...
...
...
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03.00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
...
...
...

As you can see, my wireless card is the Intel 3945ABG. 

Let me know if any ideas come to you while looking at the outputs above. In the meantime, I'll look into ndiswrapper and wifi radar.

---

### Post by Blario on 2008-04-17
> **darkrider2k6 said:**
> Here's what lshw -C network shows:



And lspci:


As you can see, my wireless card is the Intel 3945ABG. 

Let me know if any ideas come to you while looking at the outputs above. In the meantime, I'll look into ndiswrapper and wifi radar.

I have this same exact setup

```
brandon@DIABLO:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:d2:c0:f9:ca
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () ip=192.168.1.153 latency=0 link=yes module=ipw3945 multicast=yes wireless=IEEE 802.11g
brandon@DIABLO:~$ lspci |grep  82573L
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller

```

The problem I have is that Gutsy doesn't detect my wired card at all.  My wireless has worked since day one.  I have no idea why there's no device for the ethernet card tho... , since it is actually listed in lshw & lspci... , but you will notice that the first line of lshw says "  *-network UNCLAIMED " for the wired card, whereas it simply says "  *-network" for the wireless card.  

I'm shocked at how I don't see this problem already solved on the forums.  Most problems I ever encounter have already been ran into and solved by other users.  Especially since this isn't a new version of *buntu, it should be pretty stable by this point.

---

