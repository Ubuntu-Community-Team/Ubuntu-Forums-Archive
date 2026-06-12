---
title: "Please help me get my Airport Extreme working in Feisty"
date: 2007-06-09
forum: Apple PPC Users
---

### Post by ticopelp on 2007-06-09
Hi, 

I could use some help getting my wireless card to work in Feisty. I am on an Apple PowerPC G4 15" Powerbook with an Airport Extreme. 

I followed the instructions at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty), installing the firmware, and it seems like I'm ninety percent there, but I just can't get to the final ten percent. 

Here's the problem. The system recognizes my wireless card. It will see my wireless network, as well as several others in my apartment complex. I just can't seem to successfully join my own wireless network. Whenever I try, it simply says "waiting for network key" and hangs, or joins and says "signal strength: 0%" even when I'm right next to the router and other computers in the house can get on the network.

A few things: 

1) The wireless network is working fine. I have other wireless-enabled PCs in the house that can use it.

2) The wireless card seems to be working, and worked fine on this machine under OS X (which was installed until yesterday).  

3) I tried using wifi-radar instead of the network manager, and I got a message that it "could not get IP address." It then joined the network successfully, but no IP. 

Any help would be much appreciated. I really don't know what to try next. 

Here are the results of my iwconfig:
```
iwdan@Jolene:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Holonet"


          Mode:Managed  Frequency=2.484 GHz  Access Point: 00:11:24:0C:B3:EB   
          Bit Rate:1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Here is the result of sudo iwlist eth1 scan
```
eth1      Scan completed :
          Cell 01 - Address: 00:11:24:0C:B3:EB
                    ESSID:"Holonet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:10
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=80/100  Signal level=-73 dBm  Noise level=-68 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 84ms ago
          Cell 02 - Address: 00:14:C1:2B:83:46
                    ESSID:"USR5461"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=82/100  Signal level=-69 dBm  Noise level=-68 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 56ms ago
          Cell 03 - Address: 00:0D:93:EA:C7:A7
                    ESSID:"Holonet"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:10
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=98/100  Signal level=-37 dBm  Noise level=-68 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 52ms ago

```

"Holonet" is the id of my wireless network. 

Also, my wireless network is using WPA Personal authentication -- I tried configuring it according to the tutorial above, and that may be the problem, but I'm not sure. 

Thanks again for any help -- I'm at the end of my rope here.

---

### Post by ticopelp on 2007-06-09
Okay, update time.

I abandoned WPA and switched to 40, then 128-bit WEP security. Still no dice. 

 I actually got connected wirelessly by turning off WEP security and just running an open network. I'm actually posting this from the wireless right now -- so hooray!

But I don't want to run an unsecured wireless network in my building, so I need to figure out how to re-enable WEP and still be able to connect with this machine. 

Any thoughts?

---

### Post by ticopelp on 2007-06-09
Nevermind, I got it working for the time being.

Thanks for letting me talk to myself in this thread. :D

---

### Post by stmiller on 2007-06-09
Yeah that driver unfortunately is picky with getting the exact security setting it likes from your router. If you have any tips, please add them to the PPCFAQ wiki:

---

### Post by tcrroadie on 2007-06-09
ticopelp,

Could you please post how you resolved your wireless issue?  This will help improve solving wireless issues in the future.  

I am starting to get the feeling that a thorough document on how to configure wireless on Airport Extreme (wireless G) Macs needs to be created.  I have been thinking about creating a wireless how-to myself to help reduce confusion and ease wireless configuration.  The link you posted in your original post is actually for X86 PC's not for PowerPC.  

Glad to hear you got your wireless working.  :)

---

### Post by ticopelp on 2007-06-09
Sure, let me put something together and post it.

---

### Post by sudo55 on 2007-06-23
An easy step by step howto for ppc users with airport extreme wifi and feisty 7.04 would be sweet. :--D

Sorry for the long post people... :--O

I have been piecing together information from various threads including:

How to: Broadcom Wireless cards

[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

I found these comments interesting from the aforementioned thread...

uninstall all other wifi programs but wifi radar,
thats right network manager does not use the traditional config files, looking at my networking through system > administration > networking shows all my netowork cards to be disabled.

If/Iw config show accurate stats but making changes by these two commands dont effect the network manager settings.
ndiswrapper didnt work at all.

also this thread...

HOWTO: Broadcom 4318 Wireless Cards

[http://ubuntuforums.org/showthread.php?t=197102&highlight=Download+http%3A%2F%2Fubuntuforums.org%2Fattachment.p...8%26amp%3Bd%3D1177147133](http://ubuntuforums.org/showthread.php?t=197102&highlight=Download+http%3A%2F%2Fubuntuforums.org%2Fattachment.p...8%26amp%3Bd%3D1177147133)

I found this comment interesting from the aforementioned thread...

When you can connect with out any encription, do this:

system > administration > networking

put your key in there. Let ubuntu time out with the new settings.

edit your interface file like Randall suggests:

iface wlan0 inet dhcp
wireless-essid Starfleet
wireless-key open XXXXXXXXXX

the key is to add the word 'open" before your key. I don't know why the network manager doesn't have this in there already, but it doesn't. and I don't know why wifi-radar doesn't add it either (I didn't test this, I only know it doesn't work) but I suspect that, as a Windows user, I am used to haveing the program do what i say. Perhaps there is a way to run wifi-radar as sudo that i don't know about or understand. But that is the fix! put open in there and it works!

I am going to reset all of my devices to use open, bring the network back up, and post to you all my successes (I KNOW it will work, i can feel it!).



PS: there is still no icon in network manager in the upper right that let me know the wireless is connected, but who cares if ti works, right?
__________________
Goats lead the lambs to slaughter...... 

Re: HOWTO: Broadcom 4318 Wireless Cards
Actually, I just got it working and am posting this from within ubuntu. What I did was I went to the ubuntu package collection online(here) 

[http://packages.ubuntu.com/feisty/](http://packages.ubuntu.com/feisty/)

and manually downloaded ndiswrapper-common and ndiswrapper-utils-1.9 (listed under miscellaneous.) After that, I installed them and then installed the drivers from your package and after a restart, boom, it worked. Thanks, after a two days of searching, I'm finally able to stay in ubuntu without having to go to windows for the internet.

The discalimer, none of this information was originally posted by me, all credit is to the original posters in the aforementioned threads.  I edited the information to keep this post as short as possibe.  :-)

Hopefully, this information can help in the development of the tutorial or inspire someone to read through more of the postings/comments from the aforementioned threads.

Cheers,  :--->

---

### Post by tcrroadie on 2007-06-23
^^sudo55^^

I appreciate the time that you have taken in trying to gather some information on how different users have configured there Broadcom wireless cards.  

Please keep in mind that ndiswrapper is ***only*** for X86, and will not work on PowerPC. 

For installing the driver for the Broadcom chips used in Macs, all that is needed is the package bcm43xx-fwcutter.
```

kris@ibook:~$ sudo aptitude show bcm43xx-fwcutter
Package: bcm43xx-fwcutter
State: installed
Automatically installed: no
Version: 1:006-1
Priority: optional
Section: universe/utils
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 123k
Depends: libc6 (>= 2.5-0ubuntu1), debconf (>= 0.5) | debconf-2.0
Recommends: wget | curl
[I]Description: Utility for extracting Broadcom 43xx firmware
 fwcutter is a tool which can extract firmware from various source files. It's written for BCM43xx driver
 files. [/I]
 
 The project page is http://bcm43xx.berlios.de/
```
```

kris@ibook:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       [COLOR="Red"]product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation[/COLOR]
       physical id: 12
       bus info: pci@10:12.0
       logical name: eth1
       version: 02
       serial: 00:14:51:80:67:eb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes [COLOR="Red"]driver=bcm43xx driverversion=2.6.20-15-powerpc [/COLOR]ip=192.168.1.100 latency=16 link=yes multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:80084000-80085fff irq:52
```


I don't think users here are necessarily having problems getting there Airport cards working, it is getting there network settings properly configured (WEP, WPA).   Specifically setting up WPA is what I would like to see.

---

### Post by ticopelp on 2007-06-23
For the record, I could not get WPA to work on my PowerPC machine. I had to change to WEP. 

The biggest issue I noticed is that Ubuntu demanded very specific passphrase lengths for the WEP key, while the AirPort setup did not. So I had to make sure the passphrase was the correct length (13 characters in my case).

---

### Post by sudo55 on 2007-06-23
tcrroadie, thanks for the reply... :-)

I will mess with the bcm43xx-fwcutter package.

Thanks for the code info... :--)

Cheers

---

### Post by sudo55 on 2007-07-02
An interesting tutorial... :-D

[http://www.lanterntorch.com/free-software/149/airport-extreme-lives-in-linux/](http://www.lanterntorch.com/free-software/149/airport-extreme-lives-in-linux/)

---

### Post by dynamicv on 2007-07-25
Just wondering whether I'm alone on this one.  I've managed to get the BCM4306 card in my PowerBook G4 attaching briefly to my Netgear access point over WPA-PSK, and it receives an address over DHCP.  Unfortunately it only works for a maximum of a couple of minutes before it then bombs out.  Pings from that point no longer receive a response and eventually return Destination Host Unreachable.  When I boot the PowerBook into OSX the connection is stable so I don't think it's the router that's at fault.  Any ideas on how I can improve the stability?

I'm using 7.04 if that helps.

---

### Post by dantheman6690 on 2007-07-27
> **sudo55 said:**
> An interesting tutorial... :-D

[http://www.lanterntorch.com/free-software/149/airport-extreme-lives-in-linux/](http://www.lanterntorch.com/free-software/149/airport-extreme-lives-in-linux/)

I checked that out and before this tried installing fwcutter using a different tutorial and both times when i type in my user name and pw, a grey box will appear in the top left corner of the screen and the system will just hang. i can still move the mouse and stuff but it just stays like that so i can't do anything. the first time this happened i reinstalled feisty fawn which wasnt too hard because i didn't have anything important on my ubuntu partition. is there an alternative to this or a workaround so that my computer doesnt freeze every time i try to get fwcutter working? I realize that ndiswrapper will not work since there is no ndiswrapper-utils package for powerpc. I'm on a Power Mac G5 dual booting mac os x and ubuntu. My wireless card is an airport extreme but is the bcm4306 chipset. Any help would be much appreciated

---

### Post by domino on 2007-08-29
Thanks for the tip sudo55.

I manually configured my AirPort extreem wireless setting to connect to my local AP. Then edited */etc/network/interfaces* by adding the word "**open**" (no quotes) before the* key*. I restarted the OS rather than restarting the network card. 3 chears for the tip :guitar:

The problem now is, what happens when I need to connect to WEP hotspots other than my own? Yet the saga continues.

---

### Post by BigAllen on 2007-09-01
I've recently installed Ubuntu on my 12 G4 Powerbook.  Being totally new to Linux, the process has been relatively painless so far, save my Airport issues.  I've been following the tutorial listed by the OP, but whenever I try to get the firmware, I'm given this message:

```
The following NEW packages will be installed:
  bcm43xx-fwcutter
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 27.5kB of archives.
After unpacking 123kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com feisty/universe bcm43xx-fwcutter 1:006-1 [27.5kB]
Fetched 27.5kB in 0s (39.9kB/s)    
Preconfiguring packages ...
Selecting previously deselected package bcm43xx-fwcutter.
(Reading database ... 110881 files and directories currently installed.)
Unpacking bcm43xx-fwcutter (from .../bcm43xx-fwcutter_1%3a006-1_powerpc.deb) ...
Setting up bcm43xx-fwcutter (006-1) ...
--11:48:20--  http://boredklink.googlepages.com/wl_apsta.o
           => `wl_apsta.o'
Resolving boredklink.googlepages.com... 72.14.203.118
Connecting to boredklink.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
11:48:20 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

There's a link in the tutorial to click if the install doesn't work, however the link is dead.

Here are the results of my iwconfig if relevant:

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I'm now at a total loss and would appreciate any hints.  Thanks.

---

### Post by domino on 2007-09-01
Allen, 

Get it from the Ubuntu repo. assuming you have uncommented them from your source.list file.

```
sudo apt-get install bcm43xx-fwcutter
```

or just simply search and install from Synaptic Pakage Manager.

---

### Post by BigAllen on 2007-09-04
> **domino said:**
> Allen, 

Get it from the Ubuntu repo. assuming you have uncommented them from your source.list file.

```
sudo apt-get install bcm43xx-fwcutter
```

or just simply search and install from Synaptic Pakage Manager.

That's what I did before.  It gives me the same error which is:

```
allen@allen-laptop:~$ sudo apt-get install bcm43xx-fwcutter
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcm43xx-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up bcm43xx-fwcutter (006-1) ...
--01:56:15--  http://boredklink.googlepages.com/wl_apsta.o
           => `wl_apsta.o'
Resolving boredklink.googlepages.com... 72.14.203.118
Connecting to boredklink.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
01:56:15 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

so I'm still stuck.

---

### Post by Ripfox on 2007-09-05
For the record, I got wireless working fine with this adapter on an iMac g3 with wpa: [http://www.airlink101.com/products/awll3026.html](http://www.airlink101.com/products/awll3026.html)

out of the box.

Also I use Wicd to connect instead of Network Manager.

---

