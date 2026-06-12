---
title: "Wireless Network Adapter requires plug switched off"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by pdbaker on 2008-03-15
Hi

My wireless network adapter works fine after a complete restart with plug switched off.

However if I restart for some reason without turning off at the plug then I get no connection. The blue light on my Netgear WPN111 USB wireless adapter still flashes but FireFox tells me I have no connection.

Being a real beginner and having no other ideas I just turn it off and switch off at the plug but I'm sure there must be something behind it!

I've checked the forums: and find mention of two things /etc/network/interfaces and NetworkManager.

In my interfaces file I have:

====

auto lo
iface lo inet loopback


iface wlan0 inet static
address 192.168.1.30
netmask 255.255.255.0
gateway 192.168.1.1
wpa-psk c4f73....b3c04
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA2
wpa-ssid NETGEARPDB

auto wlan0

=====

[I've removed part of the psk key because I'm not sure if I should post that or not!]

I've also got a folder called NetworkManager in etc:

NetworkManager --> dispatcher.d --> 01ifupdown which contains

====

#!/bin/sh -e
# Script to dispatch NetworkManager events
#
# Runs ifupdown scripts when NetworkManager fiddles with interfaces.

if [ -z "$1" ]; then
    echo "$0: called with no interface" 1>&2
    exit 1;
fi

# Fake ifupdown environment
export IFACE="$1"
export LOGICAL="$1"
export ADDRFAM="NetworkManager"
export METHOD="NetworkManager"
export VERBOSITY="0"

# Run the right scripts
case "$2" in
    up)
	export MODE="start"
	export PHASE="up"
	exec run-parts /etc/network/if-up.d
	;;
    down)
	export MODE="stop"
	export PHASE="down"
	exec run-parts /etc/network/if-down.d
	;;
    pre-up)
	export MODE="start"
	export PHASE="pre-up"
	exec run-parts /etc/network/if-pre-up.d
	;;
    post-down)
	export MODE="stop"
	export PHASE="post-down"
	exec run-parts /etc/network/if-post-down.d
	;;
    *)
	echo "$0: called with unknown action \`$2'" 1>&2
	exit 1
	;;
esac

=====

Not really sure whether NetworkManager is enabled of disabled or how to find out.

I've probably done something dumb. Still very much feeling my way around.

New info: Doing a bit more digging and found a couple more suggestions but without success:

sudo /etc/init.d/networking restart launcher command on desktop but that doesn't work

This useful article:
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)
suggests putting a startup script in to restart netwokring but that doesn't seem to work either.

If I click the Network Monitor icon I get the message:

SIOCGIFFLAGS error : no such device

The only thing that seems to work is completly switching the computer plug off and on again. No need to switch off the router however.

Regards

Paul

---

### Post by dstew on 2008-03-15
Do you really need Network Manager? It is a special program that allows (supposedly) seamless switching between different interfaces to maintaing a network connection. If you do not switch networks during your usual desktop sessions, you do not need Network Manager. There are some bugs in it that might be causing some of your problems. See if it is installed by entering **nm-applet** at the command line. If a little network icon appears on your tool bar, then you have Network Manager installed. When you close the terminal window, the icon should disappear. You can also look in Synaptic to see if it is installed. I think it is part of the default installation.

To disable Network Manager, see [this Wiki]("https://help.ubuntu.com/community/WifiDocs/NetworkManager"). Look down the page, and there is a section on disabling Network Manager. Before you disable it, go to the System --> Administration --> Networking and disable your wlan0 connection. Then disable Network Manager. Then re-enable the wlan0 connection.

Another apparent problem is that with WPA encryption, the card drivers do not always work well with Network Manager. You can disable Network Manager, as above, or you can change to WEP encryption if you want to. This is also in the Wiki.

---

### Post by ellgor on 2008-03-15
Hi,

What is happening here is normal for a router, when I got mine it took months to find out that all I had to do was to switch everything off for minute then reconnect and voila, after changing settings here there and everywhere thats all it took, if you can manage to leave the router on all the time you shouldn't have to reset when you boot up, the router knows the IP of your comp and connects automatically, hope this of help.

Regards, Ellgor.

---

### Post by pdbaker on 2008-03-15
Thanks to you both.

I have managed to disable Network Manager now : I don't think I needed it.

However still not fixing the original issue.

I do leave the router on. The router is not rebooting.

But when I switch off the computer the blue light on the wireless adapter is still flashing unless I completely turn the plug off on the computer. Which seems a little strange because I don't think that happens on my other computer. Power to the wireless adapter is not cut and that seems to cause the problem because if I do switch off at the plug (on the comptuer not the router) then all is well again.

Not a major issue; just frustrating.

Thanks

Paul

---

### Post by George M on 2008-03-19
I've trying . as a newbee (absolute) to understand my ignorance in getting a wireless connection.   Ive looked at a large number of postings on the wireless forum,  but I must be missing something.  I read that a wireless icon is supposed to be  in the sys>preferences menu....ain't no such thing there!!!!  I have internet access with a D link PCI ethernet card. but Zero luck with anything having to do with wreless connection.   I know the wireless card works under windowsXP in this computer-a Dell Latirude CPx--when I had a "trial" version
 When I try to select  manual configuration,  I get either nothing, or a message telling me that an administrator is needed, and something about  a "root"  I don't understand why this has to be so complicated!!!  My card is a newer Linksys WPC300N V1-- has a Broadcom chip 43XG.  I get some basic  info on the card,ie vendor and sub vendor under advanced, but nothing that identifies a Name ie wlan0.  IF there is, I don't know what that would be.
    I've been messin' around with this for several months.  It seems like, I get more roadblocks the more things I try from the postings!!!   The power  and active link have never been on under this Ubunut 7.1.   Also, do I have to have the Ubuntu CD running in the laptop.  Is an administrator password needed to get the wireless manual configuration going.  ( I can't even get that function to work)  I there a better version of Ubuntu that will get this thing going?????    I read where the Linksys cards are an issue and that a firmware is required to be loaded and isses with drivers, but that is apparently way past my immediate problems... This card was a Christmas present, and I want to use it.   George M

---

### Post by dstew on 2008-03-20
> I read that a wireless icon is supposed to be in the sys>preferences menuThe place to configure the wireless card is in System --> Administration --> Network. If your wireless adapter does not appear there, it means that you need to install the driver for it. Many wireless cards will not function in Ubuntu because the makers of those card do not allow developers to create open-source drivers. They are operating under a business model dominated by the closed-source (Windows) operating system. Some card makers will create open-source drivers, but often these are not directly useable in Ubuntu. Most cards can be made to work in Ubuntu using the ndiswrapper program, which "wraps" a closed-source binary Windows driver with a kind of software shell that allows it to connect to the Linux operating system. Another thing to try is WiFi Radar. Here is a [blog entry]("http://www.cnet.com/8301-13880_1-9848471-68.html") where this worked. However, I don't think WIFi Radar will work if you don't first have a driver. The blog writer may have "accidentally" installed a working driver during his attempts to get his card working, and WiFi Radar just picked up the card and enabled it.

---

