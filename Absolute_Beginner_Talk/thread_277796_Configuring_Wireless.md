---
title: "Configuring Wireless"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by DavidJE13 on 2006-10-15
I've been trying to get my wireless card working in Ubuntu for a few days now with no success. I've set up a dual boot of XP/Ubuntu and XP can get on the network, but Ubuntu cannot.

Details:

* I can't get on the internet without the wireless, so I can't download any new software. I do have another ubuntu computer which is connected, so I could copy installers across via memory stick if absolutley necessary (and if told how :P)
* My wireless card appears in the Network Manager as eth2 and is correctly listed as wireless.
* I can ping myself (192.168.0.3) but not the router (192.168.0.1)
* lshw shows a driver is installed
* iwconfig says that the Access Point is "Invalid"
* iwlist finds no networks
* My network is WEP, Shared Key, DHCP and on channel 11. I have tried setting it to Open but this doesn't help. Also, I use a router which is set to use both g and b (The ubuntu driver is set to use b and I don't know how to change it)
* Whenever I use the Network manager, it seems to change the channel to 14 which my router is incapable of. Also, when I set the IP type to DHCP, it takes several minutes to apply changes. Using static instead applies changes instantly.
* My card is a Creatix CTX465

---

### Post by wieman01 on 2006-10-15
What does...
> iwlist scan
...say?

---

### Post by DavidJE13 on 2006-10-15
> lo      Interface doesn't support scanning
eth0    Interface doesn't support scanning
eth2    No scan results
sit0    Interface doesn't support scanning

I have no idea what sit0 is refering to...

---

### Post by wieman01 on 2006-10-15
What driver have you used? Can you show us the relevant section of "lshw" please? 

Something is missing, I am trying to figure out what. Perhaps it's only an entry in "/etc/network/interfaces"... But we'll see.

---

### Post by jshein on 2006-10-15
See my thread here

[http://ubuntuforums.org/showthread.php?p=1622085#post1622085](http://ubuntuforums.org/showthread.php?p=1622085#post1622085)

---

### Post by capn_hector on 2006-10-15
your wireless card is eth2.  try iwlist eth2 scan a couple of times and see what it gives you.  you might also need an ifconfig eth2 up (enable the wireless card)  you could also try setting the wireless card to channel 11  iwconfig <wifi card> chan 11  then do an iwlist <wifi card> scan.  this is all from the command line and possibly with the sudo.

---

### Post by wieman01 on 2006-10-16
> **DavidJE13 said:**
> I have no idea what sit0 is refering to...
**[COLOR="Red"]"sit0"[/COLOR]** is referring to the alias that **[COLOR="Red"]NetworkManager[/COLOR]** is using I believe. Uninstall NetworkManager & see how it goes.

---

### Post by DavidJE13 on 2006-10-16
Sorry for long delay;

wieman01; the driver is set to "islsm_pci"

capn_hector; I've already tried scanning using only eth2 several times - it always turns up nothing

jshein; About to try that suggestion now. I'll tell you how it goes.

---

### Post by DavidJE13 on 2006-10-16
Ok, it didn't work. Here's the contents of that file after making the change if it's any help:

> auto lo
iface lo inet loopback


auto eth1
iface eth1 inet dhcp


iface eth2 inet static
wireless-essid xxxxx
wireless-key XX:XX:XX:XX:XX
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth3 inet static
wireless-essid xxxxx
wireless-key XXXXXXXXXX
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1





auto eth2

eth3 is (I think) a reminant of trying to use a USB connection instead of the network card.

I know that my router's IP is 192.168.0.1 Also, my computer's IP (when logged into windows) is always 192.168.0.3, though it is set to DHCP.

---

### Post by wieman01 on 2006-10-16
> **DavidJE13 said:**
> Ok, it didn't work. Here's the contents of that file after making the change if it's any help:



eth3 is (I think) a reminant of trying to use a USB connection instead of the network card.

I know that my router's IP is 192.168.0.1 Also, my computer's IP (when logged into windows) is always 192.168.0.3, though it is set to DHCP.
This all looks fine but you need to uninstall NetworkManager to get this working. Could you try?

---

### Post by DavidJE13 on 2006-10-17
I'll have a go at uninstalling it and tell you what happens.

---

### Post by DavidJE13 on 2006-10-17
After taking a look, it seems that I don't have Network Manager installed at all; In the add/remove programs list it's shown without a tick.

Any other ideas? :(

---

### Post by wieman01 on 2006-10-17
And the wireless router is turned on? Have you enabled "wireless"? The scan delivers no results, that's why I am asking... I am not sure if the problem is with the PC.

---

### Post by fragos on 2006-10-17
gnome network manager gave me fits with a laptop and broadcom chip set.  wifi-radar on the other hand turned the trick for me.  Perhaps it can help you.

---

### Post by DavidJE13 on 2006-10-18
I can get on the wireless when I boot in XP (on the same computer), it's just Ubuntu that has problems, so I know my network is ok.

I'll have a go with Wifi-radar if I figure out how to copy the installer across from my other computer...

---

### Post by wieman01 on 2006-10-18
Then what wireless card have you got? It seems that Ubuntu has not recognized the hardware.

---

### Post by DavidJE13 on 2006-10-19
According to windows device manager it's a CREATIX 802.11g Wireless Adapter. I think the full description is CTX465

I should probaby point out that windows didn't recognise it automatically - I had to download drivers from the internet (no linux drivers avalible from the same place though) But windows did manage to use my USB wireless connection (which ubuntu can't)

---

### Post by fragos on 2006-10-19
I have no experience with CTX465.  The path to supporting WiFi cards and chip sets without Linux drivers is ndiswrapper which can marry a Windows driver to Linux.  That is the path I would pursue.  It worked well for me with a broadcom WiFi chip set in an Acer laptop.  We don't always have a choice but when you can its easy to research on the web which equipment has been most successful in a Linux system.

---

### Post by DavidJE13 on 2006-10-19
Ok, I've installed ndiswrapper from the live CD, and I even figured out how to install the driver files...

but how do I get it to actually *work*? I have no idea what the id of the card is (it says it should be XXXX:XXXX but I can't find an entry like that - I've been trying with the 0000:03:03 and 0000:03:06 ids with no success - hopefully that hasn't broken other hardware :S)

So I guess my question is:

how do I get the ID of my wireless card?

---

### Post by wieman01 on 2006-10-19
Ok, to start with, what does this say:
> ndiswrapper -l
We'll guide you through the rest. Have you used this guide by chance?

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by DavidJE13 on 2006-10-19
thanks,

ndiswrapper -l says:

> PRISMA00

which is the name of the .inf driver file I installed. I haven't seen that guide you posted. I'll take a look now...


Edit: that guide mentions ndisgtk, which I haven't installed. I'm about to try it now.

---

### Post by wieman01 on 2006-10-19
Is that all that is says? When you deploy the *.INF file please make sure that ALL other driver files (e.g. *.SYS, etc.) are in the same directory as *.INF. Otherwise the installation will fail.

This is a common problem so that's why I am writing this. 

If you have problems with the guide, let us know... I have guided people through it a couple of times so I know it DOES work (ahem... most of the time).

---

### Post by DavidJE13 on 2006-10-19
As far as I remember, that is all it says. I'll have a check when I install this ndisgtk program. And yes, the other files were in the same directory (one called PRISMA00.sys and one called prismnic.cat)

---

### Post by DavidJE13 on 2006-10-19
Ok, ndiswrapper -l says "driver installed, hardware installed" after PRISMA00 if that's any help

I've worked through that list, and it fails on the "sudo ifup wlan0" bit (I'm using eth2 instead of wlan0 though) (I tried it with wlan0 too)

The error it gives is something like this:

Error "Set Encode" (8B2A)
SIOCADDRT: File Exists
Failed to bring up eth2

I'm done for today though, I'll try again tomorow

---

### Post by inkybutton on 2006-10-19
> **DavidJE13 said:**
> Ok, ndiswrapper -l says "driver installed, hardware installed" after PRISMA00 if that's any help

I've worked through that list, and it fails on the "sudo ifup wlan0" bit (I'm using eth2 instead of wlan0 though) (I tried it with wlan0 too)

The error it gives is something like this:

Error "Set Encode" (8B2A)
SIOCADDRT: File Exists
Failed to bring up eth2

I'm done for today though, I'll try again tomorow

Hi,
I have had the same *annoying* problem, but I took another approach.

According to your first post, your wireless network is using shared-key authentication, which is (I think) analogeous to Linux's wireless restricted security mode. So I wrote a script that configures the kernel to use the wireless restricted security mode.

I'll post the script later, but I hope the information helps.

---

### Post by wieman01 on 2006-10-19
> **DavidJE13 said:**
> Ok, ndiswrapper -l says "driver installed, hardware installed" after PRISMA00 if that's any help

I've worked through that list, and it fails on the "sudo ifup wlan0" bit (I'm using eth2 instead of wlan0 though) (I tried it with wlan0 too)

The error it gives is something like this:

Error "Set Encode" (8B2A)
SIOCADDRT: File Exists
Failed to bring up eth2

I'm done for today though, I'll try again tomorow
Ok, now please do the following and post the output:
> iwlist scan
> ifconfig
> iwconfig
> sudo gedit /etc/network/interfaces
> sudo /etc/init.d/networking restart
The first thing we'll do is edit your "/etc/network/interfaces" file so that it reflects your network environment. I think we are close.

---

### Post by wieman01 on 2006-10-19
> **inkybutton said:**
> Hi,
I have had the same *annoying* problem, but I took another approach.

According to your first post, your wireless network is using shared-key authentication, which is (I think) analogeous to Linux's wireless restricted security mode. So I wrote a script that configures the kernel to use the wireless restricted security mode.

I'll post the script later, but I hope the information helps.
No offense, but I would rather avoid any kind of script because the disadvantage is that you don't get to *understand* how networks are configured & what the script actually does. If our "manual" approach fails we should give your script a go - by all means. But let's try to figure it out first.

---

### Post by inkybutton on 2006-10-19
> **wieman01 said:**
> Ok, now please do the following and post the output:

...

The first thing we'll do is edit your "/etc/network/interfaces" file so that it reflects your network environment. I think we are close.

Editing /etc/network/interfaces does not work for shared-key authentication. BTW this is the script I wrote: (words in italics are to be replaced with your information.

```

#!/bin/sh
#Enable Restricted security mode Wifi Key. 

echo "Enabling restricted mode (shared key authentication) of Wifi."

sudo iwconfig eth2 essid *[Your SSID here]*
sudo iwconfig eht2 key restricted *[Your WEP key here]*

echo "Commands executed."

echo "Resetting eth2..."

sudo ifdown eth2

sudo ifup eth2

echo "Resetted."

echo "Checking status..."

sudo iwconfig eth2

echo "End executing script."

```

Paste the code into your favourite text editor (e.g. gedit), edit the parts that need your information, and save it under the name of "wifi.sh" in your home directory (/home/*[your username]*)Open up a terminal and type "./wifi.sh". Wait until it displays "End executing script." Then open up your browser and hopefully, you can browse the web! If there is any problems, ask...

To the above post owner: it is merely a script. Better call it a batch file! ;) No offence taken.

---

### Post by wieman01 on 2006-10-19
Ah... I see. :-) Give it a go then!

> Editing /etc/network/interfaces does not work for shared-key authentication.
Mmm... Am I am missing something here? I have been using shared-key methods for a while now (WEP, WPA1 with TKIP, WPA2 with AES) and have never had a problem configuring it. What could be the issue with it? It all runs through "/etc/network/interfaces", no problem.

_**EDIT:**_
See this for instance: [http://www.ubuntuforums.org/showthread.php?t=202834&highlight=wpa2+rsn]("http://www.ubuntuforums.org/showthread.php?t=202834&highlight=wpa2+rsn")

---

### Post by inkybutton on 2006-10-20
> **wieman01 said:**
> Ah... I see. :-) Give it a go then!


Mmm... Am I am missing something here? I have been using shared-key methods for a while now (WEP, WPA1 with TKIP, WPA2 with AES) and have never had a problem configuring it. What could be the issue with it? It all runs through "/etc/network/interfaces", no problem.

_**EDIT:**_
See this for instance: [http://www.ubuntuforums.org/showthread.php?t=202834&highlight=wpa2+rsn]("http://www.ubuntuforums.org/showthread.php?t=202834&highlight=wpa2+rsn")

Oops... well I use 64bit WEP with restricted security mode. I don't think restricted security mode is shared-key method then... Well I can't set /etc/network/interfaces so it automatically uses restricted security mode. Any idea? Thanks...

(So embarrasing, trying to help people in the start but end up asking for help...)

---

### Post by wieman01 on 2006-10-20
Ok, can you share your "/etc/network/interfaces" with us? Don't want to sidetrack from the real issue, but this could be a quick win. Post your "interfaces" file & I'll make the changes.

---

### Post by inkybutton on 2006-10-20
> **wieman01 said:**
> Ok, can you share your "/etc/network/interfaces" with us? Don't want to sidetrack from the real issue, but this could be a quick win. Post your "interfaces" file & I'll make the changes.

I unquoted all the "auto"s so Ubuntu boots up faster. But anyway here is the interfaces file.

```

auto lo
iface lo inet loopback

#auto eth0
iface eth0 inet dhcp

#auto eth1
iface eth1 inet dhcp

#auto eth2
iface eth2 inet dhcp

#auto ath0
iface ath0 inet dhcp

#auto wlan0
iface wlan0 inet dhcp
wireless-essid any
wireless-key XXXXXXXX

iface wlan1 inet dhcp
wireless-essid XXXXX
wireless-key XXXXXXXX

#auto wlan1

```

Note: I tested different wireless cards... but the one I want to configure is wlan0. Thanks!

---

### Post by inkybutton on 2006-10-20
> **wieman01 said:**
> Ok, can you share your "/etc/network/interfaces" with us? Don't want to sidetrack from the real issue, but this could be a quick win. Post your "interfaces" file & I'll make the changes.

I quoted all the "auto"s so Ubuntu boots up faster. But anyway here is the interfaces file.

```

auto lo
iface lo inet loopback

#auto eth0
iface eth0 inet dhcp

#auto eth1
iface eth1 inet dhcp

#auto eth2
iface eth2 inet dhcp

#auto ath0
iface ath0 inet dhcp

#auto wlan0
iface wlan0 inet dhcp
wireless-essid any
wireless-key XXXXXXXX

iface wlan1 inet dhcp
wireless-essid XXXXX
wireless-key XXXXXXXX

#auto wlan1

```

Note: I tested different wireless cards... but the one I want to configure is wlan0. Thanks!

Oops double post...sorry about that... BTW in your signature, business is spelt with an "i", not "y", but I guess you want to distinguish the different meanings. ;)

---

### Post by wieman01 on 2006-10-20
Please also do this please (plus post the output):
> iwlist scan
Then edit the "interfaces" file:
> auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid [COLOR="Red"]your_essid[/COLOR]
wireless-key s:[COLOR="Red"]your_plain_text_key[/COLOR]
Then restart the network & post the output:
> sudo /etc/init.d/networking restart
Alternatively you can replace "s:[COLOR="Red"]your_plain_text_key[/COLOR]" with the "WEP hexadecimal key".

---

### Post by inkybutton on 2006-10-20
> **wieman01 said:**
> Please also do this please (plus post the output):

Then edit the "interfaces" file:

Then restart the network & post the output:

Alternatively you can replace "s:[COLOR="Red"]your_plain_text_key[/COLOR]" with the "WEP hexadecimal key".

iwlist scan result (omitted other interfaces' output)

wlan0     Scan completed :
          Cell 01 - Address: 00:11:2F:CB:E7:51
                    ESSID:"XXXXXX"
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Quality:0/0  Signal level:42/255  Noise level:0/0
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s

Well, so far so good. I will restart so the my script/batch file is not in force.

OK, after rebooting the network did not go up. When I restarted the network, here is what happens:
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/00:40:f4:ab:1e:f4
Sending on   LPF/wlan0/00:40:f4:ab:1e:f4
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/00:40:f4:ab:1e:f4
Sending on   LPF/wlan0/00:40:f4:ab:1e:f4
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
...The DHCPDISCOVER thing just goes on forever...

---

### Post by wieman01 on 2006-10-20
Have you tried both HEX and plain-text key?

No firewall running?

---

### Post by DavidJE13 on 2006-10-20
Hi, back again

I tried those suggestions;

After trying the script idea, I couldn't run the file, so I tried typing the lines in manually. It failed on "sudo iwconfig eht2 key restricted XXXXXXXXXX" with:

Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth2 ; Unknown error 524.

which is what I always seem to get...

The first suggestion; here are the results:

> root@MBBFC:~# iwlist scan
lo        Interface doesn't support scanning.

eth2      No scan results
eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

root@MBBFC:~# ifconfig
eth2      Link encap:Ethernet  HWaddr 00:07:CA:05:22:19
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:169 Memory:f8b20000-f8b22000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:75 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6596 (6.4 KiB)  TX bytes:6596 (6.4 KiB)

root@MBBFC:~# iwconfig
lo        no wireless extensions.

eth2      IEEE 802.11b  ESSID:"xxxxx"
          Mode:Auto  Channel=14  Access Point: Invalid
          Sensitivity=0/200
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

/etc/network/interfaces:

> auto lo
iface lo inet loopback


auto eth1
iface eth1 inet dhcp


iface eth2 inet static
pre-up modprobe ndiswrapper
post-down rmmod ndiswrapper
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid xxxxx
wireless-key XX:XX:XX:XX:XX

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



auto eth2

> root@MBBFC:~# /etc/init.d/networking restart
 * Reconfiguring network interfaces... Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth2 ; Unknown error 524.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth2 ; Unknown error 524.

---

### Post by inkybutton on 2006-10-20
> **DavidJE13 said:**
> Hi, back again

I tried those suggestions;

After trying the script idea, I couldn't run the file, so I tried typing the lines in manually. It failed on "sudo iwconfig eht2 key restricted XXXXXXXXXX" with:

Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth2 ; Unknown error 524.

which is what I always seem to get...

The first suggestion; here are the results:



/etc/network/interfaces:

It seems like there is a driver error. (sorry can't be sure because I am a newbie myself :) ) It's kind of beyond my scope... When I did a Google search on "Creatix driver for Linux", a link to DriverGuide may be relevant but "temporarily down" for the moment... Here is the link, BTW. [http://list.driverguide.com/list/LINUX/company259/index.html ]("http://list.driverguide.com/list/LINUX/company259/index.html")
EDIT: Don't bother about the above link. I checked in Google Cache and found that the only driver present is a HAM Modem. Talk about comprehensiveness!
**EDIT AGAIN:**I know it's frustrating to try to get a wireless network card working (trust me, I have been through this before.) Calm down. After looking at the list at NDISWrapper website, the chipset of your card(PRISMA00) seems to work well under SUSE and Debian. The chipset is the heart of the matter: it doesn't matter which manufacturer it comes from, it works. So, don't give up! 

Can you please give me the outputs of:
```
sudo ifdown eth2
sudo lspci
sudo ifup eth2
```
Don't give up!

---

### Post by fragos on 2006-10-20
Far from being an expert I will make an observation.  The first Ethernet port is normally eth0 which will assign eth1 to your 2nd network port which in this case is wireless.  I see you are using eth1 for the Ethernet port resulting eth2 for wireless.  I wonder if starting with 1 rather than 0 is causing you problems.

---

### Post by wieman01 on 2006-10-20
David:

A couple of things or observations: 

"iwlist scan" confirms that "eth2" is your wireless adapter. However, it does not recognize your wireless card, otherwise it would detect your wireless network. Having installed "ndiswrapper" your alias will definitely be "wlan0", so we don't need "eth2" anyway.

Please do me a favor... I want to start with the easiest possible setup, so please turn off WEP and enable DHCP on the router. Then open your interfaces file:
> sudo gedit /etc/network/interfaces
Paste this (delete ALL remaining lines):
> auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
This is all you need for wireless... Want to keep it simple in the first place.

The restart the network (and post the output):
> sudo /etc/init.d/networking restart
One more scan:
> iwlist wlan0 scan

---

### Post by wieman01 on 2006-10-20
> **inkybutton said:**
> It seems like there is a driver error. (sorry can't be sure because I am a newbie myself :) ) It's kind of beyond my scope... When I did a Google search on "Creatix driver for Linux", a link to DriverGuide may be relevant but "temporarily down" for the moment... Here is the link, BTW. [http://list.driverguide.com/list/LINUX/company259/index.html ]("http://list.driverguide.com/list/LINUX/company259/index.html")
EDIT: Don't bother about the above link. I checked in Google Cache and found that the only driver present is a HAM Modem. Talk about comprehensiveness!
**EDIT AGAIN:**I know it's frustrating to try to get a wireless network card working (trust me, I have been through this before.) Calm down. After looking at the list at NDISWrapper website, the chipset of your card(PRISMA00) seems to work well under SUSE and Debian. The chipset is the heart of the matter: it doesn't matter which manufacturer it comes from, it works. So, don't give up! 

Can you please give me the outputs of:
```
sudo ifdown eth2
sudo lspci
sudo ifup eth2
```
Don't give up!
Nah... We would never give up, would we?! :-)

---

### Post by inkybutton on 2006-10-21
> **wieman01 said:**
> Nah... We would never give up, would we?! :-)

Hey what about my case ? ;)

I have firestarter running at level 2-5. but I was able to get wireless working with my script/batch file when firestarter is on. The problem is, how do I enable restricted security mode in /etc/network/interfaces?

---

### Post by wieman01 on 2006-10-21
> **inkybutton said:**
> Hey what about my case ? ;)

I have firestarter running at level 2-5. but I was able to get wireless working with my script/batch file when firestarter is on. The problem is, how do I enable restricted security mode in /etc/network/interfaces?
I would shut down Firestarter for the time being... That may conflict with the network.

As for the second question... What are you exactly referring to as "restricted security mode"? I am a bit lost to be honest. Is is WEP? Or WPA? Or Radius? Perhaps you can outline that a bit more and help me undestand.

---

### Post by DavidJE13 on 2006-10-21
lol, I think this needs to be split into 2 threads

anyway, I've done those things; still not working but here are the results:

Results of
> sudo ifdown eth2
sudo lspci
sudo ifup eth2
> dave@MBBFC:~$ sudo ifdown eth2
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth2 ; Unknown error 524.
dave@MBBFC:~$ sudo lspci
0000:00:00.0 Host bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Processor to I/O Controller (rev 0e)
0000:00:01.0 PCI bridge: Intel Corporation 915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 0e)
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 71c0
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 71e0
0000:03:00.0 Network controller: Intersil Corporation ISL3886 [Prism Javelin/Prism Xbow] (rev 01)
0000:03:01.0 Multimedia controller: Philips Semiconductors SAA7134 Video Broadcast Decoder (rev 01)
0000:03:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:03:04.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
0000:03:06.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 8b)
dave@MBBFC:~$ sudo ifup eth2
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth2 ; Unknown error 524.

And the results of changing /etc/network/interfaces:
> dave@MBBFC:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... Ignoring unknown interface eth2=eth2.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                         [ ok ]
dave@MBBFC:~$ iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

So I tried changing wlan0 to eth2 in the file;

> dave@MBBFC:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth2/00:07:ca:05:22:19
Sending on   LPF/eth2/00:07:ca:05:22:19
Sending on   Socket/fallback
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 19
(continues until cancelled...)

---

### Post by wieman01 on 2006-10-21
David:

Ok, I suspect that your old Linux driver is still loaded. To check that please edit "interfaces" once again & paste this:
> auto lo
iface lo inet loopback

auto [COLOR="Red"]eth2[/COLOR]
iface [COLOR="Red"]eth2[/COLOR] inet dhcp
What does the scan say:
> iwlist [COLOR="Red"]eth2[/COLOR] scan
If the scan discovers your local wireless network, we'll forget about "ndiswrapper" for a moment.

---

### Post by DavidJE13 on 2006-10-21
I already tried with eth2 instead of wlan0 - still not working :(

---

### Post by wieman01 on 2006-10-21
David:

Ok, then your driver has not installed & the wireless card not been recognized. All I can offer now is to guide you through the configuration of "ndiswrapper". 

To test "ndiswrapper" please open this file & tell us what it says"
> sudo gedit /etc/modprobe.d/ndiswrapper


[http://https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("http://https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by DavidJE13 on 2006-10-21
It just says:
> alias wlan0 ndiswrapper

should it have eth2 in as well?

---

### Post by DavidJE13 on 2006-10-21
I'm online!

It's not a great solution (I'm using a USB Netgear connection instead of the inbuilt one) but it's a start :)

I'm downloading as much as I can while it lasts ;) I still want to get it working with the inbuilt card, but this means I won't have to keep rebooting & copying files accross via memory stick :D

One small thing (not as important as getting the inbuilt wireless working) If I boot with the USB plugged in, it fails to connect, but if I boot with it removed, then plug it in after logging on, it works. Any idea why?

---

### Post by fragos on 2006-10-21
This may relate to the device being recognized before before the GUI starts.

---

### Post by wieman01 on 2006-10-21
David:

Perhaps this helps... UPdate "interfaces":
> auto lo
iface lo inet loopback

[COLOR="Blue"]mapping hotplug
script grep
map eth2[/COLOR]

auto eth2
iface eth2 inet dhcp

---

### Post by wieman01 on 2006-10-21
> **DavidJE13 said:**
> It just says:

> alias wlan0 ndiswrapper

should it have eth2 in as well?
Oh well, then apparently "ndiswrapper" has installed correctly.

---

### Post by wieman01 on 2006-10-21
David:

Ok, I got a bit carried away because this thread has two users posting their problems. :-) So I have been confusing things quite a bit. Now... As far as your network is concerned I want to highlight this:

[COLOR="Blue"]1. "eth2" refers - most likely - to your new USB device, NOT "ndiswrapper" (Creatix CTX465).
2. "wlan0", however, is your Creatix network adapter & "ndiswrapper".[/COLOR]

So let's start all over again from there.

You have installed "ndiswrapper" and you Windows driver, the system has recognized it. So "/etc/network/interfaces" should contain "wlan0" so that you use Creatix. 
> auto lo
iface lo inet loopback

# Hotplug for USB Netgear
mapping hotplug
script grep
map [COLOR="Red"]eth2[/COLOR]

# USB Netgear
auto [COLOR="Red"]eth2[/COLOR]
iface [COLOR="Red"]eth2[/COLOR] inet dhcp

# Creatix network adapter & ndiswrapper
auto [COLOR="Red"]wlan0[/COLOR]
iface [COLOR="Red"]wlan0[/COLOR] inet dhcp
wireless-essid [COLOR="Blue"]your_network_name[/COLOR]
[COLOR="Blue"]your_network_name[/COLOR] is to add the name of the network (ESSID) you are trying to connect to. Please add it and restart the network (this time we try Creatix, but you can move the line to "eth2" as well):
> sudo /etc/init.d/networking restart
The scan should also work now (output please):
> iwlist scan
And it show results for both your network adapters. I would comment (#) or delet the lines that refer to "USB Netgear" when you are testing the other one. It may confuse the system if it finds 2 wireless adapters in "interfaces".

---

### Post by inkybutton on 2006-10-21
Back again...

I am using WEP. And the restricted security mode I talk about comes from here:

```
sudo iwconfig

...

wlan0     IEEE 802.11-DS  ESSID:"XXXXXX"  Nickname:"okuwlan"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:11:2F:CB:E7:51
          Bit Rate:11 Mb/s   Tx-Power=15 dBm
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B
          Encryption key:XXXXXXXXXX   **Security mode:restricted**
          Power Management:off
          Link Quality=0/0  Signal level=125/255  Noise level=0/0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Also, I tried your method with firestarter off. Still doesn't work.

Thanks!

---

### Post by wieman01 on 2006-10-21
> **inkybutton said:**
> Back again...

I am using WEP. And the restricted security mode I talk about comes from here:

```
sudo iwconfig

...

wlan0     IEEE 802.11-DS  ESSID:"XXXXXX"  Nickname:"okuwlan"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:11:2F:CB:E7:51
          Bit Rate:11 Mb/s   Tx-Power=15 dBm
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B
          Encryption key:XXXXXXXXXX   **Security mode:restricted**
          Power Management:off
          Link Quality=0/0  Signal level=125/255  Noise level=0/0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Also, I tried your method with firestarter off. Still doesn't work.

Thanks!
Question: Have you access to the router? Can you turn WEP off for a minute and see if you can connect? In that case you would have to remove 1 lines from "interfaces": **wireless-key**

I want to know if the encryption is the real problem or something else.

---

### Post by wieman01 on 2006-10-21
Inkybutton:

Also make sure that **MAC Filtering** is turned off. That a router settings and prevents unauthorized PCs from gaining access to the network.

---

### Post by inkybutton on 2006-10-22
Sorry I can only connect to the router via wireless. The MAC ID Filter was never turned on. The problem is, I know that restricted security mode is a problem, so how do I set up /etc/network/interfaces so it can use restricted security mode? Thanks again!

---

### Post by wieman01 on 2006-10-22
> **inkybutton said:**
> Sorry I can only connect to the router via wireless. The MAC ID Filter was never turned on. The problem is, I know that restricted security mode is a problem, so how do I set up /etc/network/interfaces so it can use restricted security mode? Thanks again!
Ok, that's the point of my question: I am not sure what "restricted security mode" is but basically there are 3 ways to secure your network:

1. WEP
2. WPA(1)
3. WPA(2)

Could you upload a snapshot of your wireless settings? Just take a screenshot of your wireless security settings so that I understand what's going on. Something is weird and I'd like to show you what options you have. Would that be possible?

---

### Post by inkybutton on 2006-10-22
> **wieman01 said:**
> Ok, that's the point of my question: I am not sure what "restricted security mode" is but basically there are 3 ways to secure your network:

1. WEP
2. WPA(1)
3. WPA(2)

Could you upload a snapshot of your wireless settings? Just take a screenshot of your wireless security settings so that I understand what's going on. Something is weird and I'd like to show you what options you have. Would that be possible?

Umm, didn't I say I use WEP in this post?

> 
I am using WEP. And the restricted security mode I talk about comes from here:

But anyway here are screenshots showing 1)network-admin, and 2)sudo iwconfig.

---

### Post by wieman01 on 2006-10-22
> **inkybutton said:**
> Umm, didn't I say I use WEP in this post?
Yes, you did but I still don't really understand why it does not work the way we're trying to set it up. :-) No worries, we're getting there.

Is there any chance you take a screenshot of your router's security settings? Normally you access the router through a browser & there should be a security section. Could you "print-screen" it & attache the image? Really want to see for myself what's going on...

---

### Post by inkybutton on 2006-10-22
> **wieman01 said:**
> Yes, you did but I still don't really understand why it does not work the way we're trying to set it up. :-) No worries, we're getting there.

Is there any chance you take a screenshot of your router's security settings? Normally you access the router through a browser & there should be a security section. Could you "print-screen" it & attache the image? Really want to see for myself what's going on...

Ooops u want the router's image... here it is...

---

### Post by wieman01 on 2006-10-22
> **inkybutton said:**
> Ooops u want the router's image... here it is...
Ok, I think I got it now. Please try the following:

1. Network Authentication: **[COLOR="Red"]Enabled[/COLOR]**
2. Data Encryption: **[COLOR="Red"]WEP[/COLOR]**
3. Shared Key Authentication: **[COLOR="Red"]Required[/COLOR]**
4. Encryption Strength: **[COLOR="Red"]128-bit[/COLOR]**

The update your wireless-key in "interfaces" (128-bit) and restart the network:
> sudo /etc/init.d/networking restart
I think we're close now, mate.

---

### Post by inkybutton on 2006-10-22
> **wieman01 said:**
> Ok, I think I got it now. Please try the following:

1. Network Authentication: **[COLOR="Red"]Enabled[/COLOR]**
2. Data Encryption: **[COLOR="Red"]WEP[/COLOR]**
3. Shared Key Authentication: **[COLOR="Red"]Required[/COLOR]**
4. Encryption Strength: **[COLOR="Red"]128-bit[/COLOR]**

The update your wireless-key in "interfaces" (128-bit) and restart the network:

I think we're close now, mate.

Actually, the "Network Authentication", provides a pull-down list of WPA, WPA-PSK, or 802.11x. I dont want to get into the WPA water. I'll try the 128 bit part later, but need to tell all people who are using this wireless network first...

---

### Post by wieman01 on 2006-10-22
> **inkybutton said:**
> Actually, the "Network Authentication", provides a pull-down list of WPA, WPA-PSK, or 802.11x. I dont want to get into the WPA water. I'll try the 128 bit part later, but need to tell all people who are using this wireless network first...
Ok, got your point. Not sure if Linux can cope with the current encryption/authentication method. Perhaps if you installed "Wifi-Radar" that would be possible.

To keep it straight, I would go for my proposed solution. What other options does "Network Authentication" give you? Please list all of them...

_**EDIT:**_
Perhaps you find some time to test all the different settings. That'd be best.

---

### Post by inkybutton on 2006-10-22
> **wieman01 said:**
> Ok, got your point. Not sure if Linux can cope with the current encryption/authentication method. Perhaps if you installed "Wifi-Radar" that would be possible.

To keep it straight, I would go for my proposed solution. What other options does "Network Authentication" give you? Please list all of them...

_**EDIT:**_
Perhaps you find some time to test all the different settings. That'd be best.

WPA, WPA-PSK, or 802.11x. that's it.

---

### Post by wieman01 on 2006-10-22
Ok, not sure what "802.11x" stands for because it could be WPA1, WPA2, or WEP. But when you test it, set it to "802.11x" and if that does not work, try "Disabled". 

Let us know the results of your tests. Interesting.

---

### Post by inkybutton on 2006-10-22
Sorry really busy now... Post the result later ok?

**EDIT:** The 802.11x option, when select, invokes a menu prompting for RADIUS server settings. Definitely not what we are looking for...

---

### Post by wieman01 on 2006-10-22
Alright, then simply choose **"Disabled"** and try the **128-bit** key. Take your time then. See you later.

---

### Post by DavidJE13 on 2006-10-24
Sorry for the long delay - I've been trying to install as much as possible while online :D

> **wieman01 said:**
> David:

Ok, I got a bit carried away because this thread has two users posting their problems. :-) So I have been confusing things quite a bit. Now... As far as your network is concerned I want to highlight this:

[COLOR="Blue"]1. "eth2" refers - most likely - to your new USB device, NOT "ndiswrapper" (Creatix CTX465).
2. "wlan0", however, is your Creatix network adapter & "ndiswrapper".[/COLOR]

So let's start all over again from there.

You have installed "ndiswrapper" and you Windows driver, the system has recognized it. So "/etc/network/interfaces" should contain "wlan0" so that you use Creatix.

[COLOR="Blue"]your_network_name[/COLOR] is to add the name of the network (ESSID) you are trying to connect to. Please add it and restart the network (this time we try Creatix, but you can move the line to "eth2" as well):

The scan should also work now (output please):

And it show results for both your network adapters. I would comment (#) or delet the lines that refer to "USB Netgear" when you are testing the other one. It may confuse the system if it finds 2 wireless adapters in "interfaces".

In regard to:

[COLOR="Blue"]1. "eth2" refers - most likely - to your new USB device, NOT "ndiswrapper" (Creatix CTX465).
2. "wlan0", however, is your Creatix network adapter & "ndiswrapper".[/COLOR]

I know for a fact that this is the other way around - eth2 is the inbuilt card and wlan0 is the USB. (I know this because I have eth2 disabled and wlan0 dissapears when I unplug the USB) (perhapse I should note that I used ndiswrapper to configure the USB connection too)

After changing the interfaces file (switching eth2 and wlan0 for the reason above) it reads: (origonal content commented out)

> #auto lo

#iface lo inet loopback

#

#auto eth2

#iface eth2 inet dhcp
#wireless-essid xxxxx
#wireless-key XXXXXXXXXX
#
#iface wlan0 inet dhcp
#wireless-essid xxxxx
#wireless-key XXXXXXXXXX
#
#auto wlan0

auto lo
iface lo inet loopback

# Hotplug for USB Netgear
mapping hotplug
script grep
map eth2

# USB Netgear
auto wlan0
iface wlan0 inet dhcp

# Creatix network adapter & ndiswrapper
auto eth2
iface eth2 inet dhcp
wireless-essid xxxxx
#wireless-key XXXXXXXXXX

With this file, sudo /etc/init.d/networking restart returns the following:

> dave@MBBFC:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/00:0f:b5:92:a4:04
Sending on   LPF/wlan0/00:0f:b5:92:a4:04
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.0.1 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/00:0f:b5:92:a4:04
Sending on   LPF/wlan0/00:0f:b5:92:a4:04
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.0.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.6 -- renewal in 38799 seconds.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth2/00:07:ca:05:22:19
Sending on   LPF/eth2/00:07:ca:05:22:19
Sending on   Socket/fallback
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ ok ]

eth2 still seems to be unable to connect

iwlist scan shows this:

> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth2      No scan results
sit0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:B5:B0:5A:E6
                    ESSID:"xxxxx"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-67 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=2

---

### Post by wieman01 on 2006-10-24
Ok, got it. What happens if you comment those lines, restart the computer & then scan:
> #mapping hotplug
#script grep
#map eth2
Since "eth2" is your built-in card, you don't need this.

I still don't think your "Creatix" device (= eth2) has been installed correctly. If the scanning does not work, there is a pretty good chance there is an issue with the driver. Any idea what could be the problem?

---

### Post by DavidJE13 on 2006-10-24
> I still don't think your "Creatix" device (= eth2) has been installed correctly. If the scanning does not work, there is a pretty good chance there is an issue with the driver. Any idea what could be the problem?

before I get your hopes up: what I'm about to say still didn't fix it:

lol, I just remembered that I uninstalled the drivers for the creatix card when I was setting up the USB device. I've reinstalled them now (but as the note above says; it didn't help)

I installed the same driver files in XP and it worked - perhapse my drivers just won't work in ndiswrapper?

I haven't rebooted yet - about to try that now.

---

### Post by wieman01 on 2006-10-24
Ok, if you use "ndiswrapper" with the Windows drivers for Creatix, then your wireless device will show as "wlan0"... Same as the USB device. "eth2" will be obsolete.

I would give "ndiswrapper" a shot. Will be much easier to help you there.

---

### Post by DavidJE13 on 2006-10-24
Sorry, I mean that I *am* using ndiswrapper with the same drivers as I used in XP

Restarted now - still not working.

---

### Post by wieman01 on 2006-10-24
Ok, just to recap: What does this say?
> ndiswrapper -l

---

### Post by wieman01 on 2006-10-24
Perhaps there is a chance that we get together over the weekend. I have an AIM account (see upper right corner) so we could hook up & resolve it via chat.

---

### Post by DavidJE13 on 2006-10-25
> dave@MBBFC:~$ ndiswrapper -l
Installed ndis drivers:
netwg111                driver present, hardware present
prisma00                driver present, hardware present
dave@MBBFC:~$

I'm trying to get aMSN working (didn't like using GAIM) so if it can talk to AIM then sure, hopefully the problem can finally be resolved.



btw, a thought on what could be wrong; since the USB connection fails if I have it plugged in on startup, could the same thing be happening with the card? I think you said something about the default drivers loading when they shouldn't, so how can I fix this?

My /etc/modprobe.d/blacklist file has "blacklist bcm43xx" at the end. Is that all it should need?

---

### Post by wieman01 on 2006-10-25
> **DavidJE13 said:**
> btw, a thought on what could be wrong; since the USB connection fails if I have it plugged in on startup, could the same thing be happening with the card? I think you said something about the default drivers loading when they shouldn't, so how can I fix this?
That is possible. Simply try it out.
> **DavidJE13 said:**
> My /etc/modprobe.d/blacklist file has "blacklist bcm43xx" at the end. Is that all it should need?
That's not the right driver for your card I guess... This example is taken from the "ndiswrapper" tutorial but does not relate to your chipset (but Broadcom as far as I know). So this won't help.

Another thought: Now you have 2 devices installed via "ndiswrapper". This could be a problem as well as they may conflict.

---

### Post by DavidJE13 on 2006-10-25
Ok, any idea how I can find out which driver I need to blacklist?

---

### Post by wieman01 on 2006-10-25
> **DavidJE13 said:**
> Ok, any idea how I can find out which driver I need to blacklist?
Unfortunately not. I could not find anything useful on the web, either.

But I would try the following:

1. Remove the driver for the USB wireless device:
> ndiswrapper -e netwg111
2. Then scan to see if the other device detects your network:
> iwlist wlan0 scan
Seems that is all I can offer right now. We need to get "ndiswrapper" together with "prisma00" working. And we eventually will...

---

### Post by DavidJE13 on 2006-10-29
It works at last!

I found the answer here: [https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111](https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111)

by getting the WG111 device working on reboot, it also seems to have made my inbuilt card work too :)

For future reference, the specific things to make it work were:

1:

> You must add the following line to the end of /etc/modules to ensure the ndiswrapper is also loaded at boot time

ndiswrapper

and 2:

> sudo gedit /etc/modprobe.d/blacklist

[...add to the bottom of the listing....]
blacklist islsm_pci
blacklist islsm
blacklist islsm_usb
blacklist prism2_usb



so I guess one of those 4 drivers was the problem one

Anyway, **big thank you** to wieman01 for all the help and patience :D and I hope that this thread will prevent anyone else having the same problem for so long ;)

---

### Post by wieman01 on 2006-10-29
> **DavidJE13 said:**
> Anyway, **big thank you** to wieman01 for all the help and patience :D and I hope that this thread will prevent anyone else having the same problem for so long ;)
Welcome. :-) And thanks for the howto that you have included. Good reference for others next time. See you then!

_**EDIT:**_
Although I got a bit lost & confused by your using 2 different devices. ;-) That was a bit too much of complexity for my taste. Lol! Usually I try to keep things simple.

---

### Post by Ultimadark on 2006-12-04
Hello!

Im new to Linux, and this problem seems to be exactly the same like mine (you can view it here [http://ubuntuforums.org/showthread.php?t=311811)](http://ubuntuforums.org/showthread.php?t=311811)).

I read all pages in this thread, but I had a hard time following everything and what is necessary and whats not, so if someone who is a little bit more experienced with Linux (I dont even know what ndiswrapper is lol) would like to try to help me, that would be great :D.

I have 128-bit WEP encryption and MAC filter on, but I disabled both and then tried scanning, no results :(.

After reading this thread, I did an iwlist scan and it said "No scan results" for the wireless connection (eth2).

Also, I dont have any chance to plug in a network cable to this computer, wireless is the only way I can connect to the internet. However, I can transfer files through a USB flash drive if necessary.

(Edit: It works fine in Windows with WEP and MAC filter enabled).

Hopefully someone will be able to help :)

---

### Post by wieman01 on 2006-12-04
I think there have been responds on the other thread. So I'll keep an eye on it.

---

### Post by fragos on 2006-12-04
The general methodology is similar for all WiFi however depending on which WiFi chipset you have the details will be different.  We can't help if we don't know.  lspci on the command line might tell us what chip set you have.  You can also try Google of your device name and model like "Acer Aspire 4000" and see what chip set was designed in.  ndiswrapper may not even be required in your case.

---

