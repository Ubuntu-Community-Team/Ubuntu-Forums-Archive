---
title: "help with ubuntu"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by huntis619 on 2008-01-08
Hi all, I'm a newbie to the ubuntu community. I have a hp zv5410us laptop.I need help with the following:(1) wireless network, I can only connect with ethernet. (2) codecs for playing mp3 and divx/xvid files. I put in a cd with mp3 files ubuntu searched for codecs but would not install. (3) I have shared memory with my video card (NVIDIA GE4400) I want to know how toget latest driver support with ubuntu. Thanking you all in advance...( young grasshopper ) huntis619

---

### Post by The Cog on 2008-01-08
1)
Open a terminal (Accessories->Terminal) and enter the command:
```
lspci
```
and post the output here. It will mean something to folks who know about wireless cards.

2)
As far as I know, you need to connect to the internet and then run the command 
**sudo apt-get update**
then try the searching for codecs again (still connected to the internet).

3)
System->Administration->Restricted Drivers Manager should offer you a nvidia driver, I think.

---

### Post by Tadock on 2008-01-08
Well your first problem I can't help you with much. But, the others I can help with  to get the missing codexs  first click on the applications-> add/remove programs button in the bar then in the top right hand corner there should be a box that says Supported Applications and change it to Use Unsupported programs and search Gstreamer and install it
And for the Nvidia driver use this [Envy Script]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by huntis619 on 2008-01-08
Thank you both. I'm going to try it now. I'll let you know the results

---

### Post by huntis619 on 2008-01-08
Here is the output8.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
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

### Post by zipperback on 2008-01-08
> **huntis619 said:**
> Hi all, I'm a newbie to the ubuntu community. 


Welcome to Ubuntu.


> **huntis619 said:**
>  I have a hp zv5410us laptop.I need help with the following:(1) wireless network, I can only connect with ethernet.


Please open a terminal window (Applications -> Accessories -> Terminal) and provide us the output of the following commands.

```


lspci

lsusb

ifconfig

iwconfig


```

The above listed commands will tell us about your hardware configuration.

> **huntis619 said:**
> 
 (2) codecs for playing mp3 and divx/xvid files. I put in a cd with mp3 files ubuntu searched for codecs but would not install. 


Install the ubuntu-restricted-extras package for codecs

system->Administration->Synaptic package manager


To listen to your mp3 files you can use one of several different applications available.
I use Rhythmbox because it also allows me to manage podcasts and some other things as well.




> **huntis619 said:**
> 
(3) I have shared memory with my video card (NVIDIA GE4400) I want to know how toget latest driver support with ubuntu. Thanking you all in advance...( young grasshopper ) huntis619


I don't have an NVIDIA chip set, I use ATI.

- zipperback
:popcorn:

---

### Post by zipperback on 2008-01-08
> **huntis619 said:**
> 
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

This link might be able to held you with the broadcom wifi.
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

And this one too.
[http://ubuntuforums.org/showthread.php?t=201902&highlight=4306](http://ubuntuforums.org/showthread.php?t=201902&highlight=4306)

- zipperback
:popcorn:

---

### Post by zipperback on 2008-01-08
Also, please tell us if you are using the 32bit or 64bit version of Ubuntu.

- zipperback
:popcorn:

---

### Post by huntis619 on 2008-01-08
OK Tadcock I did what you said- add/remove, all available applications. Scrolled down to Gstreamer and after I checked the box I got the following response: confirm installation of restricted software. press confirm. Then   list of applications not availabe   Then  downloading package information    and then....... nothing. Apparently I'm doing something wrong.  PLEASE HELP.

---

### Post by huntis619 on 2008-01-08
I'm using 32-bit. I didn't know I could use 64-bit.

---

### Post by huntis619 on 2008-01-08
lspci
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
steven@steven-laptop:~$ lsusb
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
steven@steven-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:4C:8F:1B  
          inet addr:192.168.2.7  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe4c:8f1b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8309 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6839 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9552771 (9.1 MB)  TX bytes:1158234 (1.1 MB)
          Interrupt:17 Base address:0x4800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5800 (5.6 KB)  TX bytes:5800 (5.6 KB)

steven@steven-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by zipperback on 2008-01-08
> **huntis619 said:**
> I'm using 32-bit. I didn't know I could use 64-bit.


Your output from lspci indicated that you had a 64bit processor which is why I asked.

> 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron]



You can use either the 32 bit or the 64 bit version on  your system.

There are somethings that are not 100% fully supported in native 64bit code as of yet, so I use the 32bit version and it works great.

- zipperback
:popcorn:

---

### Post by stump138 on 2008-01-08
[this page]("https://wiki.ubuntu.com/RestrictedFormats") might be able to help with your mp3 issues.

As far as your wireless is concerned it is showing that it is installed when you use do a iwconfig, which is a good sign :) 

Try turning off roaming mode on the network interface.  system->administration->network.

You might have to try and use a static IP address :) welcome and GL with the setup :)

---

### Post by zipperback on 2008-01-08
It looks like your wifi is being recognized as eth1

> 
eth1 IEEE 802.11b/g ESSIDff/any Nickname:"Broadcom 4306"


Is your wireless network device available via your network manager control?

- zipperback
:popcorn:

---

### Post by huntis619 on 2008-01-08
That I don't know

---

### Post by zipperback on 2008-01-09
To make your life a little easier in regard to network management, you might also want to consider using WICD for your network manager.

It makes setting up your wifi configuration pretty easy.

It's what I use, and it's saved me from many headaches in regard to my wifi access point management.

[http://wicd.sourceforge.net](http://wicd.sourceforge.net)


Launch wicd.

Go to preference and make sure you added the wifi adapter to the wireless interfaces box.

Also, is your router using wep or wpa?

If you can see the list of wifi access points, then you should be able to configure your connection.

Select the additional options for the wifi access point you want to configure from the list of available ones.

Click the name or the arrow just to the left of the name, this will give you the required configuration options for the access point.

If you want to always have it automatically connect to the access point, then check the box next to "Automatically connect to this network."

Next click on "Advanced Settings".

Check the "Use Encryption" check box.

Select the encryption method you are using.

Provide the required access key.

Click "Connect"

You should now be connected to your access point.

You can now close the application, and your wifi connection should automatically be established from this point on.

- zipperback
:popcorn:

---

### Post by zipperback on 2008-01-09
If you want to see if your wifi card is seeing your available access points use the following.

```
iwlist scanning
```

That will give you a listing of available access points that it sees.

If it sees one, then your wifi card should be working and you just need to configure it to connect.

- zipperback
:popcorn:

---

### Post by shareMenaPeace on 2008-01-09
Hi zipperback.,
i never ever used wifi yet, but when i boot i have always liek 10 wifi options to connect to under my network view (even 1 which is not locked). Anyway id liek to know if even from just fetching these wifi signals, that my wifi is sending something back to them?
or does this happen when i try to actually connect to one of those?

Thanx

---

### Post by huntis619 on 2008-01-09
Sorry it took so long to respond. Hi shareMenaPeace. Zipperman check this please
 iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:14:BF:A8:0C:B4
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=90/100  Signal level=-56 dBm  Noise level=-70 dBm
                    Extra: Last beacon: 816ms ago

---

