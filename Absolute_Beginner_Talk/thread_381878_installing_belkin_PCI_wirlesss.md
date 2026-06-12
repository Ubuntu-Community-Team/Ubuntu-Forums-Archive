---
title: "installing belkin PCI wirlesss"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by yachtblue on 2007-03-11
Hello
Brand new to  ubuntu and a complte novice.
trying to install a belkin F5D7000 UK

neep help!

any sugestions, have still to master the installing process so please advise.

Thomas

---

### Post by teaker1s on 2007-03-11
terminal type 
```
lspci
```

look through and there is a good chance you have broadcom wireless chipset, if so look at the link in my signature.
If your not sure or need  further help, please post output of above command

---

### Post by yachtblue on 2007-03-11
Thanks teaker

output from lspci

00:09.0 Ethernet controller: Belkin Unknown device 700f (rev20)

from what i have read up on, struggling to find what chipset this is based on.

---

### Post by teaker1s on 2007-03-11
no great joy fnding anything, please post full output so i can double check

---

### Post by MrDetermination on 2007-03-12
I have the same card and am also struggling.

Just as in [this thread]("http://ubuntuforums.org/showthread.php?t=338070") I have 6.10 and the same card as the OP in this current thread:

I put a Belkin F5D7000 wireless PCI card in and tried to install it.

If I type "ndiswrapper -l" I get:

blkwgdv7 driver installed, hardware present

If I type "modprobe ndiswrapper" my wireless card's lights do NOT come on.

If I type "iwconfig" I get:

lo no wireless extensions.

eth0 no wireless extensions.

sit0 no wireless extensions.

If I type "lspci | grep Belkin" I get:

00:0c.0 Ethernet controller: Belkin Unknown device 700f (rev 20)

If I go to the device manager, I see "Unknown (0x700f)". I click on it and it says:

Vendor: Belkin
Device: Unknown (0x700f)
Status: Status
Bus Type: PCI
Device Type: Unknown
Capabilities: Unknown

If I go to System Tools > Networking I see "Wired connection" "Modem connection".

The only driver I could use to get "hardware present" was from the Windows Belkin v7 driver (newest) in the XP folder if you break down the .exe that you download from the Belkin site.  I tried [this process]("http://www.linuxquestions.org/questions/showthread.php?t=303625") and driver as well, but no hardware present there.

Here is the full lspci output:
```
chip@chip-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:0b.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
00:0c.0 Ethernet controller: Belkin Unknown device 700f (rev 20)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
chip@chip-desktop:~$ 

```

---

### Post by Bachstelze on 2007-03-12
Could you please paste the output of this as well ?

```
lspci -n
```

---

### Post by MrDetermination on 2007-03-12
```
chip@chip-desktop:~$ lspci -n
00:00.0 0600: 1106:3099
00:01.0 0604: 1106:b099
00:0b.0 0401: 1412:1724 (rev 01)
00:0c.0 0200: 1799:700f (rev 20)
00:10.0 0c03: 1106:3038 (rev 80)
00:10.1 0c03: 1106:3038 (rev 80)
00:10.2 0c03: 1106:3038 (rev 80)
00:10.3 0c03: 1106:3104 (rev 82)
00:11.0 0601: 1106:3177
00:11.1 0101: 1106:0571 (rev 06)
00:12.0 0200: 1106:3065 (rev 74)
01:00.0 0300: 10de:0322 (rev a1)
```

Had to edit my prior post because I cut and pasted the other thread's contents as they matched identically except this:
```
chip@chip-desktop:~$ lspci | grep Belkin
00:0c.0 Ethernet controller: Belkin Unknown device 700f (rev 20)
```

---

### Post by Bachstelze on 2007-03-12
You might be out of luck, your card isn't in the list of devices known to work on the ndiswrapper wiki. When you install the Windows drivers shipped with the card, what does *ndiswrapper -l* say ?

---

### Post by MrDetermination on 2007-03-12
```
chip@chip-desktop:~$ ndiswrapper -l
Installed drivers:
blkwgdv7                driver installed, hardware present 

```

---

### Post by Bachstelze on 2007-03-12
```

sudo depmod -a
sudo modprobe ndiswrapper
sudo iwconfig
```

Does your wireless interface appear ?

---

### Post by MrDetermination on 2007-03-12
Hanging on sudo modprobe ndiswrapper

EDIT: For over 20 minutes now.

---

### Post by MrDetermination on 2007-03-12
*crickets*

---

### Post by teaker1s on 2007-03-12
connect to ethernet internt and
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils ndiswrapper-utils-1.1 ndiswrapper-utils-1.8 ndiswrapper-utils-1.9
```
reboot ad try 
```
sudo modprobe ndiswrapper
```

---

### Post by yachtblue on 2007-03-15
Hi Guys and Gal,
Have been following but pretty much lost at the first hurdle! First of all to check that we are talking about the same card Belkin F5D7000uk  ver.7000uv?

They all seem to have different chipsets for different versions. The chipset for this i have found is a realtek RTL8185L.

I have managed to find some linux drivers on the site, have no idea what to do with them now !

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true)

Thanks again for all your help, love this ubuntu idea but close the scrapping it as struggling so much with installing drivers and software

Regards

Thomas

---

### Post by essexboyracer on 2007-03-17
hey thomas, i too have a realtek 8185 cardbus (pcmcia) wireless, packaged as a belkin F5D7010UK ver7000. I have a thread here [http://www.ubuntuforums.org/showthread.php?t=384932&highlight=realtek]("http://www.ubuntuforums.org/showthread.php?t=384932&highlight=realtek")
 does a mod want to merge this thread?

---

### Post by GS2 on 2007-04-04
Important Note: See here for updated instructions [http://ubuntuforums.org/showthread.php?p=3539832#post3539832](http://ubuntuforums.org/showthread.php?p=3539832#post3539832)

Purchased one of these today - got it woking on Ubuntu Edgy with ndiswrapper 1.41. Don't bother with the linux drivers - did not make properly - and do not use the Windows drivers off the disk - they will make your system hang on boot.

**EDIT: Reliable sources (thankyou leftcase) now tell me the ndiswrapper in the repository works ok - no need to compile from source :) So click on the link above !! (unless you want to compile from source, and just search for ndiswrapper in Synaptic/Adept (if Kubuntu)**
[color=red]What you will need:
Latest version (1.41 at time of writing) from ndiswrapper
[http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/) [/color]

Windows drivers from Realtek: available [here](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=1&Level=6&Conn=5&ProdID=35&DownTypeID=3&GetDown=false&Downloads=true)
choose one of the three mirrors for the :
> Windows XP/2K/ME/98SE driver
Unpack the drivers to a folder in your /home/ directory - I named mine Belkin.

[color=red]Unpack ndiswrapper to a convenient location. (make sure you have used the cd command to get to that location)
```
tar -zxvf ndiswrapper-1.41.tar.gz
```
then
```
cd ndiswrapper-1.41
```.
 
Open a terminal and type:
```
sudo apt-get install linux-headers-`uname -r`
```
then
```
sudo apt-get install build-essential
``` [/color] 

First remove all drivers currently installed with version of ndiswrapper you may have currently installed
```
sudo ndiswrapper -e {driver name}
```
where {driver name} is the name of currently installed drivers - you can list these by typing:
```
ndiswrapper -l
```
(This probably is not needed, but keeps things tidy)

```
]Then uninstall your current version of ndiswrapper (synaptic, or adept if Kubuntu)
or use:
[code]sudo apt-get remove ndiswrapper-common
```

[color=red]Ensure you are still in the 'ndiswrapper-1.41' directory and type:
```
sudo make distclean
```
```
sudo make
```
```
sudo make install
``` [/color]

Now install the previously downloaded drivers there are three files named:
net8185.inf
net8185.cat
rtl8185.sys

One more thing, after the ```
ndiswrapper -i net8185.inf
``` step, you will need to associate this driver with the hardware:
```
ndiswrapper -a 1799:700f net8185
```

If you need a hand with that, give me a shout:

Sources:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)
[http://forum.computertrouble.co.uk/viewtopic.php?t=4686](http://forum.computertrouble.co.uk/viewtopic.php?t=4686)

lspci output:
> 01:0d.0 Ethernet Controller: Belkin Unknown device 700f (rev20)

lspci -n relevant result
> 01:0d.0 0200: 1799:700f (rev 20)

---

### Post by GS2 on 2007-04-04
This also works for the F5D7010 ver7000uk belkin wireless G laptop card :)

---

### Post by raffiki on 2007-05-03
I followed GS2's install procedure. I have 6.06LTS.

Almost everything went well except after "modprobe ndiswrapper" I get:

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-26-amd64-generic/misc/ndiswrapper.ko): Unknown symbol in module, or unknown parameter (see dmesg)

Also in /etc/modprobe.d the is no ndiswrapper file like there should be.

What should my next step be?

---

### Post by Pseudonomous on 2007-05-04
Hello GS2,

I followed your advice and was able to get my PC, running Feisty Fawn to recognize my
Belkin Wireless card, and then was even able to connect to our router and browse the
net for about 15 seconds, before my system completely locked up.  I couldn't even get
the keyboard or mouse to respond.  Any idess?

Thanks in advance

---

### Post by GS2 on 2007-05-14
> **raffiki said:**
> I followed GS2's install procedure. I have 6.06LTS.

Almost everything went well except after "modprobe ndiswrapper" I get:

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-26-amd64-generic/misc/ndiswrapper.ko): Unknown symbol in module, or unknown parameter (see dmesg)

Also in /etc/modprobe.d the is no ndiswrapper file like there should be.

What should my next step be?

Sorry for the late reply, no email alert.

to get the file in /etc/modprobe.d try
```
 ndiswrapper -m
``` 

post the dmesg output - also post lspci output too :)

=================
> Hello GS2,
 
 I followed your advice and was able to get my PC, running Feisty Fawn to recognize my
 Belkin Wireless card, and then was even able to connect to our router and browse the
 net for about 15 seconds, before my system completely locked up. I couldn't even get
 the keyboard or mouse to respond. Any idess?
 
 Thanks in advance

Power it down, and start up again. If the system locks up a second time - remove the wireless card.
post dmesg output, lspci and lspci -n output
you can remove the drivers with:
```
ndiswrapper -r driver-name
```
replace driver-name with name of driver installed shown by ndiswrapper -l 

The system lock-up I got when using the drivers from the cd - the ones from realtek taiwan work a treat.

Now turned on email notification, so my reply will be more prompt

---

### Post by GS2 on 2007-05-14
One thing I should mention, compiling from source means that the package will not be updated by apt (or Synaptic) it will be up to you to upgrade if necessary. 
If this is not for you, removing source can be done pretty easily :)

---

### Post by Kreuger on 2007-07-04
I'm having trouble. I tried PMing GS2 but no reply. I decided to use the driver directly off the disc as previous attempts with the one he showed got me nowhere.. When I tried associating my driver with my NIC it said it failed. However when I use ndiswrapper -l it shows the driver and it says the NIC too so I assume it worked? I'm just not sure what else I need to do now to get it working and how to go about setting up WPA.

Edit: The driver is BLKWGN7v7.inf and I'm using feisty with kernel 2.6.20 and ndiswrapper 1.47 built off the site.

---

### Post by leftcase on 2007-07-07
Hey there - thanks for the pointer with those Windows drivers - they're spot on!

I tried using the ndiswrapper package for Feisty and that worked so at least with Feisty you shouldn't have to build it yourself (unless you want to of course!).

Thanks Again!

---

### Post by weatherman1293 on 2007-08-24
Mine worked until I rebooted a second time, now I don't see any networks.

---

### Post by mikexgough on 2007-09-18
works great for me .....................................................................thanx guys

---

### Post by GS2 on 2007-10-15
Update:

Don't bother with the linux drivers - did not make properly - and do not use the Windows drivers off the disk - they will make your system hang on boot.

**EDIT: Reliable sources now tell me the ndiswrapper in the repository works ok - no need to compile from source :) Just search for ndiswrapper in Synaptic/Adept (if Kubuntu) and install in the normal manner**
What you will need:

Windows drivers from Realtek: available [here](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=1&Level=6&Conn=5&ProdID=35&DownTypeID=3&GetDown=false&Downloads=true)
choose one of the three mirrors for the :
> Windows XP/2K/ME/98SE driver
Unpack the drivers to a folder in your /home/ directory - I named mine Belkin.
---------------------------------------------------------------------------------------------------------------

First remove all drivers currently installed with version of ndiswrapper you may have currently installed
```
sudo ndiswrapper -e {driver name}
```
where {driver name} is the name of currently installed drivers - you can list these by typing:
```
ndiswrapper -l
```
(This probably is not needed, but keeps things tidy)

Now install the previously downloaded drivers there are three files named:
net8185.inf
net8185.cat
rtl8185.sys

One more thing, after the ```
ndiswrapper -i net8185.inf
``` step, you will need to associate this driver with the hardware:
```
ndiswrapper -a 1799:700f net8185
```

If you need a hand with that, give me a shout:

Sources:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)
[http://forum.computertrouble.co.uk/viewtopic.php?t=4686](http://forum.computertrouble.co.uk/viewtopic.php?t=4686)

lspci output:
> 01:0d.0 Ethernet Controller: Belkin Unknown device 700f (rev20)

lspci -n relevant result
> 01:0d.0 0200: 1799:700f (rev 20)

---

### Post by ushills on 2007-12-12
This works for me but only if I enter 

```
sudo /etc/init.d/networking restart
```

everytime that I reboot, networking doesn't start automatically.

---

### Post by FMonk on 2007-12-21
Ok, GS2 or anyone else who might be able to help.... :)

I have a Belkin F5D7010v7 card.  I've followed the instructions above exactly and I get..... nothing.  I had this card working in Feisty, but since I used the online upgrade to Gutsy, it hasn't worked at all (I'm plugged into a cable now, but I'd really like to have my wireless back ;)).  I posted about this in another thread, but this one seems to have a bit more life (and the other thread was specifically instructions for getting the card working in Feisty).

When it worked before, I always had to type "sudo modprobe ndiswrapper" every time I booted to get it to work.  If I try that now, I get the error message "FATAL: module ndiswrapper not found"  ndiswrapper is installed correctly though Synaptic, along with ndiswrapper-utils-1.9 and ndisgtk.  Running ndisgtk shows the proper net8185 driver installed (which I know for a fact were the same drivers I used before on Feisty) and says that the hardware is present, but if I go to the network settings, the wireless card does not show up.

My lspci output is this:
```
03:00.0 Ethernet controller: Belkin Unknown device 701f (rev 20)
```

My lspci -n output is this:
```
07:00.0 0200: 1799:701f (rev 20)
```

I'm really getting frustrated with this whole situation, I had it working before, and I'm not sure what I'm doing wrong here :(

---

### Post by FMonk on 2007-12-22
Nevermind, I got it working thanks to this post:

[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

It seems the problem was somehow related to the ndiswrapper I had installed through Synaptic.  When I installed from source, it worked fine this time.  Hopefully others will not have to go through quite as much trouble as I did over this :p

---

### Post by Telepso on 2008-02-06
I have restarted the net and have had the following message of mistake:

```
~/Desktop$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          
eth1: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
Ignoring unknown interface eth2=eth2.
Ignoring unknown interface ath0=ath0.
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
```

---

### Post by GS2 on 2008-02-10
Copy/paste the output of /etc/network/interfaces and 
```
tail dmesg
```
and
```
lspci
```

---

### Post by beeman1266 on 2008-07-22
not sure if this thread is still ongoing, but i'll give it a try anyways. I followed the helpful step by step (more or less.. I used synaptic package manager instead of the terminal and i installed ndiswrapper from the cd... does it matter?) but when i write: ndiswrapper -l, I only get: net8185:driver installed, but no info about hardware. also, if i try ndiswrapper -a 1799:700f net8185, I get:
couldn't creat symlink for "10EC:8185:14F2:10BD.5.conf": Permission denied - installation may be incomplete
. sim
.
.
.
driver 'net8185' is not installed (properly)!

---

