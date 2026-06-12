---
title: "Help!  Wireless and Integrated both will not stay conected!"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by pastorjay on 2006-11-08
Ok, I am getting really frustrated!  ](*,)  Here is my rig:

Dell 1705
Broadcom 4311 wireless
Broadcom 440x 10/100 integrated
2GB ram
60GB HDD
7900GS

It seemed as if I had everything installed correctly, including the broadcom 4311 wireless.  When I first boot up, I can connect with the wireless or the integrated no problem.  But within 30 seconds to 5 minutes, it just stops working!  Where should I start looking?

Thanks for your help!

**Here is the reason I have been experiencing this**
***Guys, I am putting this in as many threads about the broadcomm as I can.  The new nvidia drivers cause some kind of comflict with the broadcom wireless cards.  Not sure what happens, but as soon as I unloaded the nvidia drivers, and went with the default drivers the wireless function all of a sudden is working perfectly, and not droppiing out anymore.  Just a heads up!  And here is hoping that nvidia can fix this real quick, as you cannot use any 3d functions of the card, which means no Beryl and the sorts.***

---

### Post by pastorjay on 2006-11-08
up for some help

---

### Post by pastorjay on 2006-11-09
no one?

---

### Post by Bachstelze on 2006-11-09
Be more precise, please. "It's not working" doesn't help us much to find out what the problem is.

---

### Post by pastorjay on 2006-11-09
> **HymnToLife said:**
> Be more precise, please. "It's not working" doesn't help us much to find out what the problem is.

Ok, sorry about that.  Rigth after I boot up, I can connect either wirelessly or wired and everything is fine.  I literally will be connected and surfing, and will go to another page or site, and the connection will just stall, and eventually i will get a screen telling me it cannot connect to the server i am going to.  

When I look at the wireless connection, I still have a strong signal.  When I go to Wi-Fi radar, it says I am still connected, but the wireless router that I am connected to is greyed out, and shows no signal. 

When I am connected through the integrated nic, the same will happen.  I will be connected to a site, and when I go to anoter site or page, it will all of a sudden just stall, and eventually tell me that it cannot connect to the page I am going to.

I hope that is specific enough.  If there are more specific things you need to know, please ask, and I will do my best to answer what you need. 

Thanks! 
Jason

---

### Post by wieman01 on 2006-11-09
Mmm... I'd give this howto a try... Frankly, some of the native Linux drivers are a pain. Give this one a go, I am sure it'll improve things:

[http://www.ubuntuforums.org/showthread.php?t=285809]("http://www.ubuntuforums.org/showthread.php?t=285809")

_**EDIT 1:**_
Do you have access to your router? Do you see a wireless setting called "beacon interval" or similar? What's the current value?

_**EDIT 2:**_
The Howto is for 4318 but should equally work for you.

---

### Post by pastorjay on 2006-11-09
> **wieman01 said:**
> Mmm... I'd give this howto a try... Frankly, some of the native Linux drivers are a pain. Give this one a go, I am sure it'll improve things:

[http://www.ubuntuforums.org/showthread.php?t=285809]("http://www.ubuntuforums.org/showthread.php?t=285809")

_**EDIT 1:**_
Do you have access to your router? Do you see a wireless setting called "beacon interval" or similar? What's the current value?

_**EDIT 2:**_
The Howto is for 4318 but should equally work for you.

I will try uninstalling and re-installing using that guide.  I am already using the windows drivers, but a re-install can't hurt.  

As far as the beacon goes.  It was set at its default of 100.  I set it at 10, as I read that in another post as well.  Did not seem to help.

I am not sure, but do you think the wireless settings would affect the integrated nic as well?

---

### Post by wieman01 on 2006-11-09
The wireless settings might have an impact on the stability of your network. Changing the channel would also be an option to avoid interference with other wireless networks around you. Do a quick scan & see if your neighbors have networks running on the same frequency/channel. Using another channel might help indeed.

If you have are using "ndiswrapper" then I can only recommend to get hold of the latest version of your Windows driver. Then play around with the wireless settings. Keep us in the loop.

---

### Post by Aranel on 2006-11-09
I've got a Broadcom 4306, which does something similar once every other day or so. My rednecky solution was to create a new file in Gedit, containing the following:

> #!/bin/sh
sudo ifconfig eth1 down
sudo ifconfig eth1 up
sudo dhclient eth1

(In your case, replace "eth1" with whatever your interface is named.)

Then I saved it to the desktop as "connect.sh" and opened a terminal. I entered "chmod a+x Desktop/connect.sh" to make it executable, and... that's it. Now whenever that happens, I click that little icon, and a menu comes up asking me what to do with it. I click "Run in Terminal," a terminal window comes up for a couple seconds, and when it's gone, I'm connected again.

I'd try that before screwing around with other drivers. If it still persistently drops the connection like every 5 minutes or so, I'd consider using NdisWrapper or something... but... this solution works for me.

---

### Post by pastorjay on 2006-11-09
Ok, here is where I am at right now.  I have narrowed the integrated issues down to being caused by the wireless.  When I turn off the wireless in system>administration>networking, and then enable the integrated in the Network Connections, the integrated is fine.  In fact, it has been connected for several hours.  

As far as the wireless is concerned, I tried uninstalling and reinstalling the wireless.  I removed ndswrapper and reinstalled that as well.  I have removed the WiFi radar that was installed.  So, I am stuck at this moment, not knowing where to go next.  I have the driver successfully installed again at this moment, and the wireless will still work briefly, and then just stall out.  in WiFi-radar, when this happened, the network I was connected to would all of a sudden show no signal from the source.  Network Manager woulds till show a full signal though...

What to do next?

---

### Post by wieman01 on 2006-11-09
Having removed both NetworkManager & Wifi-Radar, please do a scan:
> iwlist scan
And post the contents of this file:
> sudo gedit /etc/network/interfaces
Please turn of encryption & set your network/router to use DHCP. We'll configure your network manually & see how that goes.

_**EDIT:**_
Post the results of both queries.

---

### Post by pastorjay on 2006-11-10
Here is the iwlist scan:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0D:88:C0:F3:41
                    ESSID:"Casey"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-83 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:0C:41:36:0B:5F
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-36 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=10
                    Extra:atim=0
          Cell 03 - Address: 00:12:88:E8:63:19
                    ESSID:"2WIRE240"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-79 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:18:3F:68:2C:79
                    ESSID:"2WIRE182"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-72 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 05 - Address: 00:13:46:88:8A:D2
                    ESSID:"Graddy Home Office"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-89 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 06 - Address: 00:16:B6:F2:7C:63
                    ESSID:"1302138 Home"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:0/100  Signal level:-71 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
          Cell 07 - Address: 00:0C:41:AB:AC:8F
                    ESSID:"Home"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:0/100  Signal level:-86 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

---

### Post by pastorjay on 2006-11-10
And the interfaces...
auto lo
iface lo inet loopback


iface eth0 inet dhcp


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by pastorjay on 2006-11-10
One thing i am seeing here is that my wireless is actually connecting under eth1, and that is not listed.  Should I edit an entry and change that?  It seems that i did do that the first time I installed ubuntu a few weeks ago.  Also, are there some of these I can/need to delete?

---

### Post by wieman01 on 2006-11-10
Previously (in Dapper) "wlan0" would refer to "ndiswrapper" but I have heard that this has changed in Edgy. Try edition your "interfaces" file:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
Make it exacly look like this and restart the PC. Then fire up the network applet & see if you adapter appears there.

_**EDIT:**_
Since a lot of networks around run on channel 6, I would avoid using the same frequency. Choose channel 1 to be safe. There might be interference.

Let us know how it goes. If the networking applet is of no use, then we'll edit "interfaces" manually.

---

### Post by pastorjay on 2006-11-10
ok, got everything edited.  I have the wireless adapter in the network applet.  There is no signal strength or connection though.  I also changed the wireless router to use channel 1.  So where do we go from here?

---

### Post by wieman01 on 2006-11-10
Ok, now turn off any kind of wireless security (e.g. WEP), tell me what your ESSID is and enable DHCP. Then I'll make the necessary changes in "interfaces".

_**EDIT:**_
Whenever you try to connect via wireless, make sure your Ethernet cabled is pulled.

---

### Post by wieman01 on 2006-11-10
Basically "interfaces" will look like this:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid [COLOR="Red"]linksys[/COLOR]
Then restart the network:
> sudo /etc/init.d/networking restart
No (Gnome)NetworkMananger or Wifi-Radar installed, correct?

---

### Post by pastorjay on 2006-11-10
essid is just linksys, DHCP is already enabled.  cable is pulled!

---

### Post by wieman01 on 2006-11-10
What's the output now (after restarting)?

---

### Post by pastorjay on 2006-11-10
This is what I get:

 * Reconfiguring network
interfaces...                                          /etc/network/interfaces:35: duplicate interface
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:35: duplicate interface
ifup: couldn't read interfaces file "/etc/network/interfaces"

---

### Post by pastorjay on 2006-11-10
and there is no wifi-manager or anything else installed.  Also, just as a reminder, the driver was removed from ndswrapper, 

I still have no signal being detected

---

### Post by pastorjay on 2006-11-10
well, still no progress, I may just scrap it all and either try the wrapper thing again or just buy an intel wireless adapter so I can be done with this...

---

### Post by dbott67 on 2006-11-10
Hi pastorjay,

Here's a thread that I wrote up on how I got the Broadcom working:
[http://ubuntuforums.org/showthread.php?t=274915](http://ubuntuforums.org/showthread.php?t=274915)

Basically, these are the steps that I followed:
*[COLOR="Red"]Before starting, you may need to enable the additional repositories in Synaptic.[/COLOR]*

1. Install **686 SMP Kernel** from Synaptic (to enable both CPUs).  Do this first, as ndiswrapper is compiled against the kernel.

2. Install **build-essential** from Synaptic (for compiling ndiswrapper)

3. Download latest stable version of **ndiswrapper** from [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)

4. Compile **ndiswrapper** according to [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

Before you begin can you please post the output of the following:
```
sudo lshw -C network
```
From my computer:
```
*-network
                description: Wireless interface
                product: Broadcom Corporation
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0b:00.0
                logical name: wlan0
                version: 01
                serial: 00:16:ce:31:88:xx
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes [COLOR="Red"]driver=ndiswrapper driverversion=1.25[/COLOR] firmware=Broadcom,11/02/2005, 4.10.40.0 ip=192.168.1.105 link=yes multicast=yes wireless=IEEE 802.11b
                resources: iomemory:dfcfc000-dfcfffff irq:169
```

Also, I didn't read every post carefully --- where are you getting the bcm*.inf file from?

-Dave

---

### Post by pastorjay on 2006-11-10
*-network               
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0c:00.0
       logical name: eth1
       version: 01
       serial: 00:16:ce:34:23:88
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.22 firmware=Broadcom,11/02/2005, 4.10.40.0 ip=192.168.1.108 link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:ecffc000-ecffffff irq:177
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:f0:d1:0e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=1.00 duplex=full ip=192.168.1.124 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:ecbfe000-ecbfffff irq:177

---

### Post by pastorjay on 2006-11-10
I got the file from Dell

Also, the 686 Kernal in Edgy is the generic is it not?  If so, that is what I have already.

---

### Post by dbott67 on 2006-11-10
I'm not sure what's in Edgy.  To get the kernel info:
```
uname -r
```

Does the Dell 1705 have dual core processors?
```
cat /proc/cpuinfo
```
If so, you want to make sure that you've enabled SMP and have got the latest kernel, etc.

I know that in Dapper, I was unable to get wifi working with the ndiswrapper in the repos.  You seem to be using v. 1.22 where as I am using v.1.25 (ndis is now up to v. 1.28).

-Dave

---

### Post by pastorjay on 2006-11-10
2.6.17-10-generic

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2300  @ 1.66GHz
stepping        : 8
cpu MHz         : 1000.000
cache size      : 2048 KB
physical id     : 0
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr
bogomips        : 3332.80

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2300  @ 1.66GHz
stepping        : 8
cpu MHz         : 1000.000
cache size      : 2048 KB
physical id     : 1
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr
bogomips        : 3328.89

---

### Post by pastorjay on 2006-11-10
looks like the generic in edgy is the smp version, so we are good there

So what next?

---

### Post by dbott67 on 2006-11-10
> **pastorjay said:**
> I got the file from Dell

Also, the 686 Kernel in Edgy is the generic is it not?  If so, that is what I have already.

The drivers should be okay, then.  The wiki for ndiswrapper & broadcom ([http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B)) indicates that you can get them from Dell.

If you post the output of:
```
lspci -n
```
and 
```
lspci -v
```
You should be able to compare it to the list above and make sure you've got the right driver, etc.

-Dave

---

### Post by dbott67 on 2006-11-10
> **pastorjay said:**
> looks like the generic in edgy is the smp version, so we are good there

So what next?

Okay,

Let's run sudo apt-get update and then follow steps 2, 3 & 4 for compiling & installing the latest version of ndiswrapper.

-Dave

---

### Post by pastorjay on 2006-11-10
ok, will do it now.  I have not done it this way yet, so bare with me

---

### Post by pastorjay on 2006-11-10
Well, I feel like an idiot, but I cannot get it to do this:

tar -zxvf ndiswrapper-version.tar.gz

Never used a tar before, so this is one of those noob things

---

### Post by pastorjay on 2006-11-10
I probably have to add something or change something to that command, i am just not sure what.  I saved the file to my desktop

---

### Post by dbott67 on 2006-11-10
> **pastorjay said:**
> Well, I feel like an idiot, but I cannot get it to do this:

tar -zxvf ndiswrapper-**[COLOR="Red"]version[/COLOR]**.tar.gz

Never used a tar before, so this is one of those noob things

If you downloaded the latest stable version, the command would be:
```
tar -zxvf ndiswrapper-*[COLOR="Red"]1.28[/COLOR]*.tar.gz
```

The '-version' just refers to the specific version that you're trying to extract.

-Dave

---

### Post by pastorjay on 2006-11-10
Ok, then that much I did know... I get this error

tar: ndiswrapper-1.28.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors


Maybe I have it saved in the wrong place?

---

### Post by dbott67 on 2006-11-10
There's a nifty little feature in linux (and Windows XP, for that matter) called 'tab completion'.

Suppose you wanted to extract the file above, rather than typing out the full command and filename, you could just type out the command (plus any desired options) followed by the first few letters of the filename.  Then press TAB and the system should fill out the rest of the file name or present you with some options.
```
tar -zxvf ndi**[COLOR="Red"]*<press TAB>*[/COLOR]**
```
The system should complete it for you:

```
tar -zxvf ndi[COLOR="Red"]swrapper-1.28.tar.gz[/COLOR]
```

Caveats:

1. You need to be in the correct directory (the one containing the file).
2. The part of the filename or command must be unique.  If not, pressing tab twice will give you all options that meet the criteria.

Try it out... it's cool! :)

---

### Post by pastorjay on 2006-11-10
where was this file suppose to have been downloaded to?  Maybe I shouldput it there to make this easy to foolow stpe by step?

---

### Post by dbott67 on 2006-11-10
> **pastorjay said:**
> Ok, then that much I did know... I get this error

tar: ndiswrapper-1.28.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors


Maybe I have it saved in the wrong place?

Where did you save the file?  To the destkop?  If so:
```
cd Desktop
ls
```

Verify that the ndiswrapper file is there.

If so, carry on with previous steps.  If not, type:
```
slocate ndiswrapper-1.28
```
to search for the file.

-Dave

---

### Post by pastorjay on 2006-11-10
got it...

still have a hard time remembering "case sensitive"!

---

### Post by pastorjay on 2006-11-10
Well, just got through the whole thing.  I rebooted and everything worked great for about 30 seconds, and then I los tthe connection again... I am relaly frustrated at this point...  I am not sure why it will connect, and then stall.  It shows that I still have a strong signal, but I cannot load anything or check my mail,,,blah!

---

### Post by pastorjay on 2006-11-10
Dave, I was reading through the log of the command "dmesg"  and it said that the ndiswrapper was using 1rq #177, then at the end of the dmesg log it says disabling irq #177

Any thoughts?

---

### Post by dbott67 on 2006-11-10
Do you have both wired and wireless interfaces connected at the same time or are you unplugging the wired cable?

Basically, we have to pinpoint the cause:
1. Is it the wireless router?
2. Is it the wireless card?
3. Is the driver?
4. Is it external interference (other routers, cordless phones, cell phones, microwave ovens, flourescent lights all generate interference in the 2.4 GHz range)

For #1, if your computer dual-boots to Windows (or you have another wireless device), you could run it and see if there are any problems.

For #2, you would need a dual-boot system to verify that the wifi card is faulty.

For #3, this one is more difficult to narrow down, however, I am running Dapper on similar hardware with the Dell Broadcom driver and do not have any problems.

My thinking is that it's #4 --- your card may be hopping back & forth between other nearby APs.  If you travel between multiple wireless access points, you may need to edit this file to connect:
```
gksudo gedit /etc/network/interfaces
```
```
auto eth1
iface eth1 inet dhcp
wireless-essid "whatever-your-ESSID-is"
wireless-key s:your_ASCII_wep_key
```

Here's mine, for example:
```
auto wlan0
iface wlan0 inet dhcp
wireless-essid bott
wireless-key s:secretWEPkey1
```

-Dave

---

### Post by pastorjay on 2006-11-10
Well, I do dual-boot already, and I have absolutely no issues in windows at all.  There are many different AP's in my neighborhood, so I guess that could be a possibility, other than this: I do connect several places, one of them being my church.  There is only one AP there, and I still deal with the constant stalls/disconnects.

I could try editing the interfaces file.  But would that mean I have to do it every time I go somewhere else and want to connect?

I do not have the wired lan plugged in at all.

Thoughts?

---

### Post by pastorjay on 2006-11-10
ok, edited the interfaces file and rebooting now

i am still wondering about that irq being disabled.  
Could you run dmesg and see if you get anything like that at the very end... you likely will not

---

### Post by dbott67 on 2006-11-10
If that doesn't work,  I think I know what the problem is.

You've got an nVidia video card, right?  I've got the ATI x1400 Radeon.

Can you post the output of your xorg.conf file:
```
cat /etc/X11/xorg.conf
```

When you have the proprietary binaries installed, you should have a section:
```
Section "Device"
    Identifier     "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
    Driver         "**[COLOR="Red"]nvidia[/COLOR]**"
        Option          "RenderAccel"           "true"
EndSection
```

This is the trouble.  Apparently the 'nvidia' driver is causing issues with the Broadcom wireless.  Try changing the driver to 'nv'.

[http://www.ubuntuforums.org/archive/index.php/t-193350.html](http://www.ubuntuforums.org/archive/index.php/t-193350.html)

-Dave

---

### Post by dbott67 on 2006-11-10
> **pastorjay said:**
> ok, edited the interfaces file and rebooting now

i am still wondering about that irq being disabled.  
Could you run dmesg and see if you get anything like that at the very end... you likely will not

I just SSH'd home and checked dmesg... no irq error message as you suggest.  I'm thinking it's the nVidia thing.

let me know.

-Dave

---

### Post by pastorjay on 2006-11-10
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Nov  1 19:47:17 PST 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 96.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200"
    EndSubSection
# Enable 32-bit ARGB GLX Visuals
   Option "AddARGBGLXVisuals" "True"
# If you are using an older version of compiz that
# does not support rendering into the Composite
# Overlay Window, you will need to disable clipping
# of GLX rendering to the X Root window with this
# option, or you will get a blank screen after
# starting compiz:
#  Option "DisableGLXRootClipping" "True"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

### Post by pastorjay on 2006-11-10
I had attributed the dropouts to installing Beryl awhile ago, but had others tell me that had nothing to do with it.  I guess it did not, but the associated nvidia driver that I had to install to get it to work may be the problem.  I will edit that line and see if it is the issue here in a sec.

---

### Post by pastorjay on 2006-11-10
Finally got some time to change the nvidia driver back to the default one, and all is well with the wireless now.  Really stink to be honest, because now I cannot use Beryl and other 3d things.


See the first post for more...

---

### Post by pastorjay on 2006-11-10
Also, a big thank you to Dave and everyone else for all there help!  Dave was the one that alerted me to this.

Now, I am gonna go and buy an Intel wireless unit so i do not have to worry abotu all these conflicts!

---

### Post by dbott67 on 2006-11-10
Glad you got it working!

I'm just in the process of nuking my desktop and putting Edgy on it... we'll see what happens! :)

-Dave

---

### Post by pastorjay on 2006-11-10
> **dbott67 said:**
> Glad you got it working!

I'm just in the process of nuking my desktop and putting Edgy on it... we'll see what happens! :)

-Dave

It has been several hours now since I made these changes, and everything is just perfect.  We will see how hard it is to change AP's when I go to work tomorrow morning, or Panara on Monday, but I have high hopes now!

---

### Post by dbott67 on 2006-11-10
You may want to remark/remove the lines that you added from my post #43.

```
auto eth1
iface eth1 inet dhcp
[COLOR="Red"]# wireless-essid "whatever-your-ESSID-is"
# wireless-key s:your_ASCII_wep_key[/COLOR]
```

As it may be cause for trouble at work.

-Dave

---

### Post by wieman01 on 2006-11-11
dbott67 & pastorjay:

Excellent work! Both of you. Please post your findings whenever you can because I see other threads that possibly relate to the same problem. I'll link them to this thread if you don't mind.

---

### Post by pastorjay on 2006-11-11
No problem wieman... I am posting as I can in threads I find that are relevant.  Link away!

---

### Post by pastorjay on 2006-11-11
By the way, all is working just fantastic still... over a day later!  Dave, how did your install go?

Hopefully the drivers can be fixed to avoid this...  

I have to put Beryl on hold until my Intel Pro Wireless card gets here...

---

### Post by dbott67 on 2006-11-11
Edgy went very smoothly... In fact, I can even run Beryl on this computer (P4-1.8 GHz, 896 MB RAM, nVidia GeForce2 MX 400 w/128 MB RAM).  The frame rate in Beryl is a little low, but it still looks cool.

I haven't finished tweaking just yet, but things are good with Edgy! :)

Let me know how you make out with the new intel card & Beryl.

-Dave

---

### Post by pastorjay on 2006-11-11
Great man!  Glad to hear it went well.  Hopefully I will have my new card by the end of the week, and then I can get Beryl running again and get it tweaked.  I am hoping to speed it up a little more than what it was running at.

---

### Post by Jan Hrbacek on 2006-11-16
irq 177 nobody cared is the confirmed bug:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/57355](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/57355)

Let's hope this issue is solved soon.
Now it involves the big community of Dell Latitude users :-|

---

