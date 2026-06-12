---
title: "wireless adapter voyager 1055"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by johnnyxf on 2007-02-22
greetings

i am new to ubuntu [v6.10] and am trying to get an internet connection through a bt voyager 1055.

following advice from tyres in a previous thread, [http://ubuntuforums.org/showthread.php?t=275058]("http://ubuntuforums.org/showthread.php?t=275058"), also see [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List"), i have:

- installed ndiswrapper
- installed driver bcmrndis.inf, taken from the drivers directory of windows installation, with ndiswrapper
- copied usb8023k.sys & rndismpk.sys /etc/ndiswrapper/bcmrndis/. i have tried the versions from my windows setup, and also those from ASUS [http://support.asus.com/download/download.aspx?SLanguage=en-us]("http://support.asus.com/download/download.aspx?SLanguage=en-us") as suggested by Gladier
- created hardware configuration file /etc/udev/rules.d/99-custom.rules
- ndiswrapper -l gives bcmrndis driver present, hardware present
- sudo modprobe ndiswrapper and sudo ndiswrapper -m 
- reboot

but the wireless adapter is still inactive, and no wireless connection is recognised by the system.
i have checked the widget on another machine, and the usb socket itself - both are fine

examination with lshw -C communication shows the device, but i note that there is no driver mentioned in the configuration line. does this mean that there is in fact no driver associated with the adapter, despite ndiswrapper claiming otherwise?

has anyone else managed to get this device working?

any help much appreciated. thanks.

---

### Post by johnnyxf on 2007-02-22
update.

i have been looking at the udev rule that i created for this device.
[http://www.reactivated.net/writing_udev_rules.html#syntax]("http://www.reactivated.net/writing_udev_rules.html#syntax")

i had simply copied from Gladier's post at ndiswrapper [link above] which was in relation to a wireless card rather than a wireless adapter. i suspect that the rule is wrong.

probing for the device with udevinfo give a single section of data:
KERNEL=="1-2"
SUBSYSTEM =="" ... [i won't type the whole thing out]

as i understand it, a udev rule for this device must begin with the match key KERNEL=="1-2", ...

the assignment keys SYSFS{idProduct} and SYSFS{idVendor} returned by udevinfo are different to that suggested by Gladier.

i made the appropriate modifications to 99-custom.rules:
KERNEL=="1-2", SYSFS{idProduct}=="0715", SYSFS{idVendor}=="1690", RUN+="/bin/sh/ -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"

needless to say, it still doesn't work.

i gather that the RUN+= key assigns a file to run when the device is inserted, and i would guess that it should point at the ndiswrapped driver? this is already way beyond my competence.

does anyone have any suggestions?

---

### Post by fenderjaguar on 2007-02-22
i have no suggestions, but i had a voyager 100 usb modem (not the same thing, i know) and i wanted to get that to work with linux. there was a guide written by someone who claimed they got one towork. but at the end of the day, it's a virtual 'hack' and i just saved myself the time. 

btw, are you still with bt? because we 'upgraded' our account to 4.5 mbit and received a free home hub. and we are actually paying less now that we were, i think (£22 a month now). although, maybe that was because we were on an old type of account that probably didn't exist anymore, and they gave us the router just to get us off it..

---

### Post by johnnyxf on 2007-02-22
fenderjaguar: no, bt isn't the isp. i bought the unit - a voyager 2091 wireless router - to get wireless access to the net for a laptop, and the little 1055 widget came with it. i have never had to use it before as the desktop uses an ethernet line to the router.

i have installed ubuntu on an old machine which used to run on windows, and i did check the wireless adapter before nuking the drive - it was fine.

a guy - tyres - in a previous thread said that he got his 1055 working, so i guess it is possible. i will just have to keep plugging away. it is a valuable learning process.

---

### Post by tyres on 2007-02-26
Hi Johnny,

One other thing I probably should have mentioned. I changed 2 things in the 99-custom.rules file from what the guy 'Gladier' had in his, and that was the values for 'idProduct' and 'idVendor'.

I don't know for sure that that was necessary, but it seemed logical to me when i did it, as when I opened up the adapter to look at what chip was inside it, I noted down everything on the chip, and amongst that was the Vendor and Product ids, which weren't the same as what Gladier quoted.

This is the contents of my 99-custom.rules script.

#START**
BUS=="usb",
SYSFS{idProduct}=="0715", 
SYSFS{idVendor}=="1690",
RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"
#END**

I suggest you put the values I've got for 'idProduct' and 'idVendor' in your script. That might be the key. I certainly think the 99-custom.rules script is crucial to getting this adapter working.

Good luck.

Colin

---

### Post by johnnyxf on 2007-03-01
greetings.

I apologise for turning this thread into a blog: I hope that this information may help someone else. I also apologise that so much of what follows is conditional or subjunctive. but I am reluctant to make firm assertions given that I understand very little about this subject - corrections are very welcome.

While I do not yet have a wireless connection to my LAN, I believe that I may have sorted out the drivers for the 1055 dongle.

The issues appear to be
1. the version of ndiswrapper on the ubuntu live cd is too low
2. getting the right versions of the windows drivers

I will set out the procedure after which the 1055 is recognised by System->Administration->Networking, with instructions for the baffled [in brackets]

0.  Start
  Remove the 1055 dongle. If you have been using the cd version of ndiswrapper, it is probable best to reinstall Ubuntu and start from fresh - it doesn't take long.
  [Read the links - they helped me]

1. Acquire data
- Download the latest version of ndiswrapper (link below). Currently 1.37. [Put the compressed tarball .tar.gz on the desktop]
- Get the drivers. See appendix. I have attatched the ones I used. [Put the individual files bcmrndis.inf, rndismp.sys and usb8023.sys on the desktop]

2. Install gcc [Gnu C Compiler] headers.
  [open a terminal: Applications->Accessories->Terminal]
- sudo apt-get install cpp gcc build-essential linux-headers-$(uname -r)

This is necessary for the compilation of the new version of ndiswrapper. 

3. Install ndiswrapper.
   Extract ndiswrapper. [double-click on it - a directory will appear on the desktop]
   Enter ndiswrapper-1.37 directory in the terminal [- cd Desktop/ndiswrapper-1.37]
- sudo make uninstall

   If an error "cannot remove directory" appears, do:
- sudo rm -fR /lib/modules/$(uname -r)/kernel/drivers/net/ndiswrapper (see _javajake_ link)

  Then:
- make
- sudo make install
- sudo ndiswrapper -m

4. Prepare udev rule for the hardware.
- sudo nano -w /etc/udev/rules.d/99-custom.rules [this will open a new file in a text editor]
  Enter on one line:
BUS=="usb",SYSFS{idProduct}=="0715",SYSFS{idVendor}=="1690",Run+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"
  [close and save the file with ^X, y, enter]
   See _javajake_. This apparently overrides the operating system's power limitation rules for usb devices.
- sudo udevcontrol reload_rules. 
   This may not be necessary, but doesn't seem to hurt.

5. Install drivers with ndiswrapper and build module
- sudo ndiswrapper -i Desktop/bcmrndis.inf
- sudo cp Desktop/*.sys /etc/ndiswrapper/bcmrndis
- sudo depmod -a
- sudo modprobe ndiswrapper

6. Finish
  Plug in the 1055 dongle
  Reboot.
  The wireless connection should now appear under System->Administration->Networking.

I still, however, have no connection, but I suspect that the problem is not now with the dongle.

The wireless connection appears in Networking, and I have proceeded as best I can, but no  joy.

iwconfig gives:
wlan0 IEEE802.11g ESSID off/any
          Mode:Managed Frequency 2.412 GHz, Access Point: Not Associated
          ...
          Power Management: off
          ...

iwlist scan gives:
wlan0 No scan results

sudo ifup wlan0 gives:
ifup: interface wlan0 already configured

I think that I have not linked to the LAN correctly - can anyone help me out?

In particular, how do I find the ESSID of the existing LAN. I know what i _think_ it is, but i would like to verify it. The network consists of a desktop, a laptop and a wireless router, although the desktop connects by an ethernet cable. I created a windows network with the Network Set-up Wizard - not the Wireless Network Set-up Wizard - and that has been fine: the laptop can access the internet, share files and use the printer. Do I have to set the whole thing up again?

Any help much appreciated. 

Links.
ndiswrapper [http://ndiswrapper.sourceforge.net/]("http://ndiswrapper.sourceforge.net/")
speedwolf [http://ubuntuforums.org/showthread.php?t=361287]("http://ubuntuforums.org/showthread.php?t=361287")
javajake [http://www.ubuntuforums.org/showthread.php?t=225206]("http://www.ubuntuforums.org/showthread.php?t=225206")
ASUS [http:////support.asus.com/download/dow...Language=en-us]("http:////support.asus.com/download/dow...Language=en-us")

Appendix: these perishing drivers.
The set of drivers - bcmrndis.inf configuration file and rndismp.sys usb8023.sys system files are available from many places. Sometimes the filename has a suffix "k" (or "m" or "w") and sometimes the filename is in capitals. I have investigated files from the following sources: 1) my windows set-up, C:>Program Files>BT Voyager>BT Voyager Wireless>Driver. 2. ditto C:>Windows>System32>Drivers. 3. dl from ASUS as recommended by _Gladier_. 4. attatchment given by _speedwolf_. 5. attatchment given by _javajake_. Links below. Note that 3 - 5 are actually for wireless cards; in particular the .inf file given in 5 is WUSB54GS.INF

1. BT
bcmrndis.inf   date in text 2004, date last modified 2005/02/17
RNDISMP.sys   md5sum AF79...4E01, date last modified 2005/01/19
RNDISMPK.sys md5sum AF79...4E01, date last modified 2005/01/19
usb8023.sys   md5sum F390...F282, date last modified 2005/01/19
usb8023k.sys md5sum F390...F282, date last modified 2005/01/19

2. Sys32
bcmrndis.inf   date in text 2004,       date last modified 2005/02/17
rndismp.sys   md5sum 7CE8...EFC6, date last modified 2004/08/04
usb8023.sys   md5sum AF09...D5EA, date last modified 2004/08/04

3. ASUS
bcmrndis.inf   date in text 2005, date last modified 2005/09/27
RNDISMP.sys   md5sum AF79...4E01, date last modified 2005/01/19
RNDISMPK.sys md5sum AF79...4E01, date last modified 2005/01/19
rndismpm.sys   md5sum 5FAC...D89E, date last modified 2005/01/19
rndismpw.sys   md5sum 31E5...77AE, date last modified 2005/01/19
usb8023.sys   md5sum F390...F282, date last modified 2005/01/19
usb8023k.sys md5sum F390...F282, date last modified 2005/01/19
usb8023m.sys md5sum 32F9...6253, date last modified 2005/01/19
usb8023w.sys md5sum A525...09FB, date last modified 2005/01/19

4. speedwolf
BCMRNDIS.INF  date in text 2004, date last modified 2005/07/13
RNDISMP.SYS   md5sum BB16...5DBB, date last modified 2004/03/30
USB8023.SYS   md5sum 67F9...857A, date last modified 2004/03/30

5. javajake (both versions)
rndismp.sys   md5sum 7CE8...EFC6, date last modified 2004/08/04
usb8023.sys   md5sum F390...DF282, date last modified 2004/08/04

Note that capitalisation or the addition of suffix "k" is irrelevant to the file content.

The only set that works for me is that from the windows system32 directory. I cannot see why these should be different from those in the BT Voyager directory, as they presumably came from the same place - the installation disk - but there you go. The files on the disk itself are archived in an unkown (to me) format.

---

### Post by tyres on 2007-03-01
Hi johnnyxf.

Boy, you're really going back to basics! I hope it works for you. One point I would make is that you talk about using the driver files "rndismp.sys and usb8023.sys". Those are *not* the driver files I'm using (successfully). I'm using rndismpk.sys and usb8023k.sys (note the 'k' at the end of the filename). Could be significant. The drivers you mention (without the 'k') are part of my Windows installation (I think), but I don't use them in my Ubuntu setup at all. I think I copied the driver files from the BT Voyager directory in my Windows installation.

Cheers,

Colin

---

### Post by tyres on 2007-03-01
Hi,

A couple of other things that might be useful. What does the 'ifconfig' command show, and what is the content of your /etc/network/interfaces script?

Colin

---

### Post by johnnyxf on 2007-03-01
Greetings Colin.

I tried all sets of drivers listed above, but the ones in Sys32 are the only ones that will show the wireless connection in Networking. They are clearly different from those in the BT Voyager directory - different md5 sums - although the bcmrndis.inf files are the same. There seem to be several versions of these files around.

ifconfig gives:
lo  ...
wlan0  Link encap:Ethernet  HWaddr 00:11:F5:dA:8C:5A
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

/etc/network/interfaces contains:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp 

auto wlan0
iface wlan0 inet dhcp
wireless-essid PEAKHOUSE
wireless-key s:6p49zcb51xzc5

The last two values are those I entered under Wireless Connection->Properties. PEAKHOUSE is the name of the windows network, and the number [not the real one] is the WEP code for the router.

Basics is all I can cope with!. The last time I "used" - was allowed to poke at - a Unix system was 15+ years ago at uni.

atb.

Johnny

---

### Post by tyres on 2007-03-01
Hi Johnny,

It certainly looks like your adapter is configured ok, it's just not associating with the router right now.

You've not got any kind of light showing on the adapter, have you?

Have you got DHCP installed and working?

Couple of things you could try. Try changing the settings on the router to use no encryption at all (and adjust /etc/network/interfaces accordingly).
Not recommending that for routine use, but just to see if that lets you connect. If it does it would suggest something wrong with the WEP key, preventing association.

Also, you could try setting static IP addresses, to see if that might make a difference. Might not, but no harm trying!

What does '/usr/sbin/ndiswrapper -v' show (version info). Just for comparison with what I've got.

If you like I could bundle up the driver files I'm using and attach them to a message, see if those do any good for you. You didn't post the file sizes of the driver files you're using. Might be useful for comparison with what I've got.

Final thought. Does 'dmesg' and /var/log/syslog show anything useful about the adapter?

Colin

---

### Post by tyres on 2007-03-01
Johnny,

Further thoughts looking at your post, where you say you set up the network using Windows, and you didn't know how to check the ESSID of the network (LAN). 

You should do that via your router configuration software. I don't know what your router is, mine's a BTHomeHub, and like all BTHomeHubs you get to the configuration web-interface by entering something like 'http://bthomehub/' in your browser.

You should have something similar. If not a web-interface, then a utility that lets you configure the router. That will show you what the settings are currently. Routers usually come with a default 
SSID. It may say what it is on the back of the router.

If you're just assigning the (non-wireless) network name you set up in Windows as the SSID, that may cause a problem, if the router is still working with its default SSID. So you need to get into the router to check that out. 

Colin

---

### Post by johnnyxf on 2007-03-02
Greetings Colin.

I had a long post for you, answering the above questions, but I have just done the last on my list - disabling WEP - which has made all the rest redundant.

If I disable WEP on the router, it all works - the machine is assigned an IP, I can ping the router, Firefox works, and the dongle light is active. I guess that is the answer.

There is a difference in Network Tools->Devices under IP Information.

With WEP off, and the connection working, I see two IP Addresses, for IPv4 and IPv6:

IPv4  192.168.1.4
IPv6  FE80::211:F5FF:FEDA:8C5A

With WEP on, I only get the IPv6 address. Is this significant or just a by-product of not being able to associate with the router?

I sorted out the ESSID issue, by the way. I have been into the configuration manager for the router and learned a lot today.

However, I don't think that running the network without security is a good idea. I will try varying the protocol and changing the keys and see what happens.

I want to thank you for your support, Colin. You have really kept me sticking at this.

Johnny.

---

### Post by tyres on 2007-03-02
Hi Johnny,

Good to get somewhere at last, even if as you say, no security is not good!

But hopefully only a step on the way to wireless nirvana ;-)

I did wonder about your WEP key. I know you didn't post the real key, but 
I wondered what that 's:' was you had at the start of the number? When I was using a WEP key (I've now moved onto WPA) I didn't have anything like that at the start. You could try putting a new WEP key in the router, changing the one in /etc/network/interfaces to match, and see if that works.

In my experience you get the IP address assigned if everything else is ok.
If there's a problem with say, the encryption or the SSID, the adapter won't associate with the router, and no IP address is assigned. So no IP address suggests some configuration problem between the adapter and the router.

But this development at least does confirm that ndiswrapper is working, and the drivers are working (to some extent anyway).

As I've mentioned before, I've managed to get the configuration right for the SSID to not be broadcast, so that may be something you could do. You need to set it to not broadcast the SSID in the router, and then get the correct syntax in /etc/network/interfaces so that it scans for the hidden SSID. Get the syntax wrong and it won't associate again! Let me know if you want that syntax. Then at least you wouldn't be advertising your wide-open system!

Colin

---

