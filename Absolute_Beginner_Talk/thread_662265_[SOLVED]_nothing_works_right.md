---
title: "[SOLVED] nothing works right"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by huntis619 on 2008-01-08
Hi all, I've been on my laptop (hp zv5410us) all day trying to finish setup. I still can't get drivers for video. I can't install anything not even the missing codecs on firefox. I cant play my divx files and still most important to me- I can't connect to the internet wirelessly. I am not going to quit. I really want this to work.

---

### Post by durrell on 2008-01-08
First things first: did you enable the Restricted Drivers in the System > Administration > Restricted Drivers tab? You'd need a wired connection to do this, but it could very well solve the wireless problem depending on what card you're using. It could also solve the video card issue.

---

### Post by exactopposite on 2008-01-08
> **huntis619 said:**
> Hi all, I've been on my laptop (hp zv5410us) all day trying to finish setup. I still can't get drivers for video. I can't install anything not even the missing codecs on firefox. I cant play my divx files and still most important to me- I can't connect to the internet wirelessly. I am not going to quit. I really want this to work.

please post the specs of your laptop. specificaly the parts that aren't working right

---

### Post by shareMenaPeace on 2008-01-08
Huntis, you might want to download linuxmint.com and give this a try, it has all included from the very first beginning..... even runs better than gutsy on my asus notebook with ATI (compiz) ...


Cheers

---

### Post by stump138 on 2008-01-08
for your video card, I would recommend envy, which you can get from [here]("http://albertomilone.com/nvidia_scripts1.html").

For Firefox, what are you looking for? flash?

for divx etc.. try looking at the bottom of [this]("https://wiki.ubuntu.com/RestrictedFormats") page.

---

### Post by huntis619 on 2008-01-08
OK I'm trying to install missing plugins for firefox, yes flash. Still like I said I have been unable to download ANYTHING since I installed ubuntu.Yes I went to the restricted drivers and it says for each item NVIDIA accelerated graphics and my wireless card that the software source for the package is not enabled.

---

### Post by huntis619 on 2008-01-08
steven@steven-laptop:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go 64M] (rev a3)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)

---

### Post by huntis619 on 2008-01-08
-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:4C:8F:1B  
          inet addr:192.168.2.7  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe4c:8f1b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15991 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11524 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19103152 (18.2 MB)  TX bytes:1426219 (1.3 MB)
          Interrupt:17 Base address:0x2800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

steven@steven-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"steven"  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by durrell on 2008-01-08
That wireless card uses proprietary firmware. If you'll plug the laptop into a wired ethernet connection, you can download the firmware and your wireless should work just fine after that.

The reason it says no wireless extensions is because your card is disabled completely until you install the firmware.

---

### Post by huntis619 on 2008-01-08
I downloaded all available drivers for my wireless from hp site. Do I need to download the graphics driver also?

---

### Post by durrell on 2008-01-08
You shouldn't be downloading drivers from HP's site. You should be downloading them through System > Administration > Restricted Drivers. This is where you can find the graphics drivers as well.

---

### Post by huntis619 on 2008-01-08
OK when I go to the restricted drivers page after I try to enable drivers these are the responses I get-  the software source nvidia glx not enabled;  the software source bcm43xx-fwcutter is not enabled

---

### Post by PaulATL on 2008-01-08
I had the same problem as you when I installed Gutsy on my Compaq laptop (same exact drivers, I think).  However, at the time I did not have a wired ethernet connection.  At least one of the restriced drivers needs to be downloaded.  Once I had my wired connection, I could enable the two drivers.

So... do you have an active, wired ethernet connection?  (I hope that's all it takes for you.)

Good luck.
--Paul

---

### Post by huntis619 on 2008-01-08
First of all Hello PaulATL. I live in Augusta. To answer your question I don't know. I am plugged up to my network by ethernet and I am on this site. Don't scare me now. Like I said before I really want this to work. Back in 2005  I bought these 2 laptops hpzv5410us and a custom build from Monarch computer. AMD 3400 socket 754 2GB RAM 9600XT with 3 400GB HD. 2 sony  19" LCD. My setup back then cost me almost $7000.Not to mention the THREE computers  ( ranging from first gen media ctr to athlon xp2600) I have in my storage house. I have been reading about ubuntu since vista dropped. I was about to go mac but my wife will kill me...hence here I am thats why this has to work  LOL

---

### Post by huntis619 on 2008-01-08
I told you PaulATL you're scaring me.   Can anyone tell me how to get to device manager so I can check my wired connection and other devices

---

### Post by oldos2er on 2008-01-08
Go into System, Administration, Software Sources, and make sure all the boxes are checked.

---

### Post by huntis619 on 2008-01-08
Thank you very much oldos2er. When I finished trying to download ubuntu-restricted-extras this is what I saw
 msttcorefonts uses defoma                                                 &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Msttcorefonts uses the DEbian FOnt MAnager (defoma). If you wish to use   &#9474;  
 &#9474; the fonts provided by this package under the X Window System, you must    &#9474;  
 &#9474; configure it to use defoma fonts.                                         &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; The easiest way to do so is to use the x-ttcidfont-conf package. For      &#9474;  
 &#9474; more information, install the x-ttcidfont-conf package and consult its    &#9474;  
 &#9474; documentation under /usr/share/doc/x-ttcidfont-conf.                      &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; For uses of msttcorefonts not related to the X Window System (e.g.        &#9474;  
 &#9474; printing) this is not required. 
Then after I tried enable graphics driver
E: could not get lock /var/cache/apt/archives/lock-open (11 resource temporarily unavailable)

---

### Post by durrell on 2008-01-08
Open a terminal (Accessories > Terminal) and type:

```
sudo apt-get update
```

Then try again and see if it works.

---

### Post by huntis619 on 2008-01-08
Thank you all very much. Especially durell and oldos2er. It went through that time  durell. Also I was able to get my graphics drivers and wireless drivers.Now I just have to reconfigure my wireless settings and download some codecs and I'll be on my way. Again thank you all for your help.

---

### Post by shareMenaPeace on 2008-01-09
Huntis, try around play with compiz ( go to Administration -> synaptic package manager and search for compizconfig and install this).

But you might want to second my first post in this topic :D (download install the other live cd)
Than you have everything done except the restricted driver part (For this you also can see afterwards ENVY from System Tools).

To enable compiz PREFERENCES - APPEREANCE ... 

To know this sounds odd, but i just got teleported here from another time and you like to check this out if you get bored :D

Cheers

:popcorn:

---

### Post by huntis619 on 2008-01-09
Hi shareMenaPeace I'll try it. As of now though all my drivers are installed. I installed my codecs for audio/video. Now it seems I have to reconfigure my settings with my router. Will do that in the morning. I am pleased so far with ubuntu. Up and running in 2 days? Thats fantastic. This forum has been very helpful. Thank you all and shareMenaPeace thank you for the advice, like I said I will look into that.

---

### Post by shareMenaPeace on 2008-01-09
Nice that you got it running, and the first time is always the tuffest time ... and i agree thsi forum rocks ...

Cheers

---

