---
title: "wusb54g wireless networking"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by cheetah_thompson on 2008-01-28
I am a newbie trying to configure my Ubuntu "Gutsy" PC for home wireless networking with a Linksys WUSB54g card. I have previously had this Ubuntu PC working through a wired connection directly to my Zonet switch/wireless router, so I know the router is fine and there is nothing inherently wrong with my Ubuntu installation.

Four steps so far:

1. I know my wireless network is working as I can connect from Windows XP. And I am just using 'default' as the name without any encryption. And both lights are on on the Linksys wireless receiver.

2. I have installed ndiswrapper and ndisgtk from the Ubuntu Gutsy CD using sudo apt-get.

3. I have copied the drivers directory from my Linksys WUSB54g CD, and installed rt2500usb.inf driver (there are drivers for version 1, 2 and 4 on the CD, so I chose the latter).

4. I did 'sudo depmod -a'.

Its taken me a lot of head scratching to get this far, looking at different forum posts, and frankly I have little idea what I'm doing. The point is the wireless network still does not work, so what should I try next.

Below are the results of running different commands at the command prompt. Its encouraging that ndiswrapper believes rt2500usb is installed, and that iwconfig brings up some information under wlan0. The Link Signal level looks like a small number, but right next to the Ubuntu PC this Windows laptop is picking up the wireless network with Strength: Very Good. Do I need to edit my /etc/network/interfaces file and if so, how should it look?

Under the Network Settings GUI, wlan0 Properties dialog box has Network Name (ESSID) = default, Password type = WPA Personal, Network password = (blank, there is no password), Configuration = Automatic Configuration (DHCP). IP address, subnet mask and Gateway address are all set to blank. My router ip address is 192.168.1.1, but I don't have this set anywhere on the Ubuntu PC. I have changed the Password type to WEP key hexadecimal but it makes no difference.

When I try to browse using Firefox it just sits there with status "Looking up (url)" and fails after a minute or two.

Here are the results of those commands:

(i) ndiswrapper -l
rt2500usb : driver installed
        device (13B1:000D) present (alternate driver: rt2500usb)
wusb54g : driver installed

(ii) iwconfig:
wlan0     IEEE 802.11g  ESSID:"default"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 08:10:74:0F:26:BC   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


(iii) more /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp



auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

iface wlan0 inet dhcp
wireless-essid default

auto wlan0



auto eth0

---

### Post by coolbrook on 2008-01-28
```

sudo modprobe ndiswrapper
```

...should follow sudo depmod -a

Are you set up with roaming mode enabled?  If so then consider a manual configuration.  System > Administration > Network > Properties

---

### Post by cheetah_thompson on 2008-01-28
Thanks Coolbrook. Tried that and rebooted. No difference.  
I don't have roaming mode enabled.

---

