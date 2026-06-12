---
title: "Some questions about some commands in terminal"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by Raynt on 2007-03-14
Hi, I'm trying to install the RT61 driver with the instructions provided here [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61?action=show&redirect=Rt61WirelessCardsHowTo](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61?action=show&redirect=Rt61WirelessCardsHowTo)
I'm having a bit of trouble however. 

My main problem is when I try to use "modprobe --remove rt61pci" in terminal it tells me the operation isn't permitted. It doesn't even ask me for the administrator's password or anything. 

I also have two other questions.

Is the result of the instructions up to this point supposed to be the folder being extracted and copied to the home folder? Just double checking.

Is there some way I'm supposed to save the changes I made to the settings accessed by entering "sudo vi -b /etc/Wireless/RT61STA/rt61sta.dat"? Or is that automatic?

Thank you for the help,
Raynt

---

### Post by gangrelsurf on 2007-03-14
are you doing sudo before the modprobe?

---

### Post by Raynt on 2007-03-14
No, so I just add it in front? Is there anything I need to do to save the changes to the configuration file as mentioned in my third question first?

---

### Post by gangrelsurf on 2007-03-14
yeah, the two sudo commands should be:
----------------------------------------------------------
Activating the module (driver)

The pre-installed module, which is broken has to be removed. From the command line, enter:

$ sudo modprobe --remove rt61pci

Then, we can load the new module that we have just installed:

$ sudo modprobe rt61

To check if the module is activated and working, you should verify that ra0 device is visible in the output of iwconfig:

---------------------------------------------------------

as for your configs, are you doing it in vi? If so have you figured out how to do the changes and just need to know how to save?:
<esc> to enter command mode
press <:> (that's a colon) then <c> then <w> and <enter> to write (save)

---

### Post by 23meg on 2007-03-14
> No, so I just add it in front? 

Yes. 

> Is there anything I need to do to save the changes to the configuration file as mentioned in my third question first?

Yes. I suggest you use the "gedit way" described in the guide, and just save the file after making the changes. If you have to use a command line editor, try nano, which is simpler.

```
sudo nano /etc/Wireless/RT61STA/rt61sta.dat
```

Hit Ctrl +X to exit nano.

---

### Post by gangrelsurf on 2007-03-14
Sorry, but I've got to go grocery shopping here.  I'll pop back in when i get back and see how your doing.

---

### Post by Raynt on 2007-03-14
Hmm, I managed to save the configuration changes and the terminal seems to have accepted the two "sudo" commands. Yet, when I use "iwconfig" it says no wireless extensions for any of the options listed (lo,ra0,eth0,sit0). Is that ok? Or by visible does it literally mean that ra0 is still there?

---

### Post by gangrelsurf on 2007-03-14
try this at the terminal:
 lsmod | grep rt61

that will list all the installed modules which have rt61 in the name, which should be one line for the module itself, and then maybe some for what ever is using it

---

### Post by Raynt on 2007-03-14
Ok, this is what I got back "rt61 254596  0". That means I can go to the next step right?

---

### Post by gangrelsurf on 2007-03-14
the | character between the two commands is a pipe, btw. It send the out of one command to the in of another. It's the vertical bar, probably above your enter key

---

### Post by gangrelsurf on 2007-03-14
that means your modules loaded, but from what you said about the output of iwconfig, its not getting associated with the card

try this:

sudo ifdown ra0
sudo ifup ra0
iwconfig

that just shuts the card down, then brings it back up

---

### Post by Raynt on 2007-03-14
I took the liberty of trying the next step. "echo 'blacklist rt61pci' >> /etc/modprobe.d/blacklist" (with and without sudo at the front). Both ways I got back "bash: /etc/modprobe.d/blacklist: Permission denied".

---

### Post by Raynt on 2007-03-14
> **gangrelsurf said:**
> 
try this:

sudo ifdown ra0
sudo ifup ra0
iwconfig

that just shuts the card down, then brings it back up I did that and got back "interface ra0 not configured". The response for "lsmod | grep rt61" is the same as before.

---

### Post by Raynt on 2007-03-14
Sorry for the triple post, "interface ra0 not configured" was the response to the first command. The second response to the next command was "Ignoring unknown interface ra0=ra0". "iwconfig" still yielded no wireless extensions to everything.

Well I'm calling it quits for tonight. I'll check back some time tomorrow. Thanks a ton gangrelsurf and 23meg.

---

### Post by gangrelsurf on 2007-03-14
Your driver is compiled
It is being loaded

but you're not configured

post a copy of that weird proprietary config file (the normal one is  /etc/network/interfaces )

open it with:
```

gksudo gedit  /etc/Wireless/RT61STA/rt61sta.dat
```

that will open it in gedit, which is a nice intuitive, non-L33t editor that behaves more or less like notepad (and much more if ysomethinng though, edit that file to the minimal config, no encription,     ou get into it)

also do the same with /etc/network/interfaces and post it

if there are plain text wep keys in either, make sure you xxxxxx them out or whatever

I have to get to bed to (midterm tomorrow).  I'll pop in around noon and see what has changed here

If you want to try something though, edit that file to the minimum, no encryption, any essid (network), and if it is your router that you are hooking up to, turn the encryption off on that. I would assume that there is a description of the syntax for the config file in the folder that you unpacked into, or a subdir of it.

---

### Post by Raynt on 2007-03-15
Here is a copy of the propriety configuration file 
[Default]
CountryRegion=0
CountryRegionABand=7
WirelessMode=0
SSID=J's and K's Web
NetworkType=Infra
Channel=0
AuthMode=OPEN
EncrypType=NONE
DefaultKeyID=1
Key1Type=0
Key1Str=0123456789
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
WPAPSK=abcdefghijklmnopqrstuvwxyz
TxBurst=0
PktAggregate=0
WmmCapable=0
APSDCapable=0
APSDAC=0;0;0;0
BGProtection=0
IEEE80211H=0
TxRate=0
RTSThreshold=2347
FragThreshold=2346
RoamThreshold=75
PSMode=CAM
TxPreamble=0
FastRoaming=0

Here is a copy of /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp


auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


auto eth0


iface wlan0 inet dhcp
wireless-essid J's and K's Web

auto wlan0

I have found a read me for it, the part on the meanings of the settings for the configuration file doesn't seem to say anything that would require I change how it is currently set up. Is it possible that the reason it isn't configured is simply because I haven't finished the instructions in the how to yet? Also, might the fact that I'm currently using an ethernet cable to access the internet have the potential of causing the problem?

---

### Post by gangrelsurf on 2007-03-16
Hey sorry I didn't get back with you yesterday.  I got suddenly busy.  Assuming 1) you haven't moved on from here and gotten it working, b) that since you've got that readme with the syntax, all the options are good, I think I see your problem, and another possible kink in all this.  

1) Try setting the SSID= line to something without spaces and no ' , just alpha numeric chars (and change it on the router too), or put quotes around it (probably easiest cause you won't have to mess w/ the router, but the apostrophes may still mess things up, not sure )  or set it to what ever the readme says to do to connect to any available network, so:

```

SSID=JandKWeb
(or)
SSID="J's and K's Web"
(or)
SSID=Any
(or what ever the readme says to do for any available network)

```


2) then change the  /etc/network/interfaces to the same value

```

iface wlan0 inet dhcp
wireless-essid JandKWeb
(or)
iface wlan0 inet dhcp
wireless-essid "J's and K's Web"
(or)
iface wlan0 inet dhcp
wireless-essid any

```

3) do
[CODE]
sudo ifdown ra0
sudo ifup ra0

sudo ifdown wlan0
sudo ifup wlan0
/CODE]

4) Your /etc/network/interfaces is calling this card wlan0 (unless you have another wireless card installed?), where as the card is also known as ra0.  It is probably just an alias.  So check both names like this:

iwconfig ra0
< this will spit out your config for that card >
iwconfig wlan0
< this will probably be the same thing, but check>

And lets just see where we're at from there

---

### Post by Raynt on 2007-03-16
I changed the ssid so it should work. Than I tried to restart ra0 and wlan0. ra0 gave the exact same response as what I recieved last time. wlan0 was a different story, for ifdown I got the same response "ifdown: interface wlan0 not configured". Then when I tried ifup I got this, 

"Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0."

> **gangrelsurf said:**
> 
4) Your /etc/network/interfaces is calling this card wlan0 (unless you have another wireless card installed?), where as the card is also known as ra0.  

I think this has something to do with a bit of a problem with the RT61 and Ubuntu. It sometimes seems to claim that it is two cards. In network manager (before I started to install the new driver) it showed up as wlan0 and wmaster0.

As for the iwconfig's they were different, "ra0       no wireless extensions." and, "wlan0     No such device"

There is absolutely no reason for you to apologize for not replying yesterday. Besides, I was rather busy myself.

---

### Post by Raynt on 2007-03-16
I just tried to go through the final few steps and then tried sudo ifup ra0 and wlan0 again. I got a strange answer for ra0, 

"Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ra0/00:16:b6:99:dc:af
Sending on   LPF/ra0/00:16:b6:99:dc:af
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping."

Does that mean that my wireless card was working, but it was having trouble communicating with the network?

---

### Post by gangrelsurf on 2007-03-16
That's exactly what it means. making progress.

Did you wind up setting for any network, or did you quote your net work name in the config file?  If the latter, check that the name in the config file matches the name of the essid for the router (I'm assuming that you can get to the router config at 192.168.0.1 or something over your wired network)
Also, make sure the router isn't using encryption at this point (set it up later if you want), since your NIC is set for no encryption

---

### Post by Raynt on 2007-03-16
I have temporarily turned off the encryption on the router. I changed the ssid so that it no longer had the ' and then quoted the new version. I double checked the config files with the network name, it is the same. Would the settings for wlan0 in /etc/network/interfaces have any possiblity of interfering with the settings I added to ra0 as told to do in the how to?

I've been going over the configuration file and there is one part I'm not sure about that looks like it might be important.

"CountryRegionABand=value      							

	value	

		0: use 36, 40, 44, 48, 52, 56, 60, 64, 149, 153, 157, 161, 165 Channel

		1: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140 Channel

		2: use 36, 40, 44, 48, 52, 56, 60, 64 Channel

		3: use 52, 56, 60, 64, 149, 153, 157, 161 Channel

		4: use 149, 153, 157, 161, 165 Channel

		5: use 149, 153, 157, 161 Channel

		6: use 36, 40, 44, 48 Channel

		7: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140, 149, 153, 157, 161, 165 Channel

		8: 52, 56, 60, 64 Channel

		9: 34, 38, 42, 46 Channel

		10: 34, 36, 38, 40, 42, 44, 46, 48, 52, 56, 60, 64 Channel"
I have absolutely no idea what it is talking about, so I'm not sure which of these channels would be correct (CountryRegion on the other hand is correct).

---

### Post by gangrelsurf on 2007-03-16
> **Raynt said:**
> Would the settings for wlan0 in /etc/network/interfaces have any possiblity of interfering with the settings I added to ra0 as told to do in the how to?

They might be. We're getting a bit beyond my depth here.  What you need to find out is: is wlan0 a link to ra0?

One thing you might want to try, just kind of a stab in the dark that just occurred to me (If there's anyone else watching this post, please feel free to jump in any time : ) - try changing wlan0 to ra0 in the /etc/network/interfaces file. If it doesn't improve things just change it back, but see what you get when it's pointing at ra0

As for that other thing with the ```
"CountryRegionABand=value 
``` I haven't a clue.

---

### Post by Raynt on 2007-03-16
That didn't seem to cause any noticeable change. I'm not sure if this means anything, but I checked in administration- networking and found that one wireless connection has reappeared and it claims the interface isn't configured. For the sake of scientific inquiry I'll try to log on to some other nearby unencrypted network and see if the result is any different.

---

### Post by Raynt on 2007-03-16
Weird, I tried another network and got a slightly different response.
"There is already a pid file /var/run/dhclient.ra0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ra0/00:16:b6:99:dc:af
Sending on   LPF/ra0/00:16:b6:99:dc:af
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 15
[B]DHCPOFFER from 192.168.1.1
DHCPREQUEST on ra0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.45 -- renewal in 37411 seconds.[/B]"

No internet though.

---

### Post by Raynt on 2007-03-16
Well, that's it for me tonight. I dare say that we are getting close to the solution. I don't claim to understand any of this, but that last result sounded a lot like, "Oh, hi, you wanted to talk to me? Come over here." Wow, I really need to find a new hobby, now I'm personifying computer code. :)

Aha! The first victory. I happened to decide to check this thread one more time tonight and it loaded up fine. One twist though, I realized that the internet cable had been disconnected. It was a little creepy at first actually. Now all that remains is getting it working on my network and re- adding encryption.

---

### Post by Raynt on 2007-03-17
It works, the problem seemed to be that the propriety configuration file couldn't understand the quotations around the ssid. It probably thought that they were part of the ssid. Many thanks for the amazing help gangrelsurf.

---

### Post by Sharzoe on 2007-03-17
I am trying to install a .run file from NVIDIA.  I have tried running the file in the Terminal.  The installation starts but then reports that I'm in X server and cannot run it in that mode.

??  How do I install the latest drivers from NVIDIA?  I am completely new to ubuntu.

Thanks
Mark

---

