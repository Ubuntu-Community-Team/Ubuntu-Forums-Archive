---
title: "Wireless Freeze in 7.10"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by F4ll3ngo3th3 on 2007-12-02
I'm a new Ubuntu User and I had just finished installing it a few hours ago. I'm still suffering from culture shock but the internet had been a really great help. I'm now able to dual-boot Ubuntu and Vista with no problem...

However, I have a problem with connecting to the internet through Ubuntu 7.10

It recognizes my adapter and even scans the wireless networks around me, but, when I try to connect on my home network, it hard freezes.

I've been looking all over the internet for a solution but I just can't find any. When I boot to Vista (which I'm on rite now), the internet works fine. My Wireless card is a **Realtek 8185 Extensible 802.11b/g Wireless Device**. I've seen from [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek) that 8185 is supported in 6.06 and 6.10 with no problems. 

Since I have a fresh install, I could always switch to 6.10. I installed 7.10 thinking that it would be the most compatible but I guess I was wrong. Maybe 7.4 would be okay too. The problem is that, it's kinda frustrating if I have to re-install Ubuntu versions just to make my internet work. If there is a way to downgrade, I guess it would be a lot more easier.

Btw, this is my 1st post and 1st day as a linux user :)

---

### Post by ebeard on 2007-12-03
I can't help, I've had the same problem.

I had a good setup with 6.10, even had my graphics working via openchrome. Upgraded and things have never been the same. 

Tried clean install of 7.10 (upgrade stepped through 7.04 crashed). And spent too much time just trying to get xserver to run on 7.10. Once I had a desktop running I tried to get my Realtek 8185 to run. Seemed to install fine, but then got a Kernal Panic on reboot. Turned off wireless at bios (set to manual start) and rebooted, then tried to get wireless turned on. Only thing I got if I turned on the wireless was hardlock of my computer. 

More relevant to your situation. Avoid 7.04. Graphics were flaky and Realtek 8185 wireless will not work (at least not for us novices). I even tried ndswrapper without success. 

I finally went back to 6.10. Wireless works, but it's frustrating that I can't get back to the way things were. Things that worked in 6.10 have been changed or are no longer available (OpenChrome, Automatix). I know 7.04 and 7.10 work for a lot of people, but for me they were a non-functional downgrade on two computers. I hope 8.04 is better. 

If you decide to try another version after you get something working (6.10?) make an image file (partimage) so you can go back. I kick myself for not doing that, but I thought I would be able to reconstruct (wish I had known support for 6.10 was gone).

---

### Post by alan34 on 2007-12-03
Hi all,

I might be able to help those with a rtl8185 chipset.

My card is a Peak pci wireless card with rtl8185 chipset I also had the kernel panic when I tried to connect to my wireless router, really annoyed as the card worked with Edgy and Fiesty.

The solution is to use the Window drivers and ndiswrapper and blacklist the linux r818x driver.

Get the Window files - should have something,inf and something.sys in the same directory. I got net8185.inf and rtl8185.sys from the cd that came with my card.

In System - Administration - Software Sources make sure there is a tick against the Ubuntu 7.10 cd. Load the cd
(you may have to untick all the other software sources just note which ones are ticked now!!)

In System - Administration - Synaptic Package Manager search for ndiswrapper and install.

In a terminal change directory to where the Window files are then (in my case)
(Go to Applications - Acessories - Terminal) 

then copy and paste

sudo ndiswrapper -i net8185.inf
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
sudo ndiswrapper -l
------------You should see something like this

alan@alan-desktop:~$ sudo ndiswrapper -l
[sudo] password for alan:
net8185 : driver installed
device (10EC:8185) present (alternate driver: r8180)

Now to load the driver when you boot

sudo gedit /etc/modules
----------You should see something like this add ndiswrapper at the end of the file

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ndiswrapper


Now we blacklist the linux driver

sudo gedit /etc/modprobe.d/blacklist
---------------At the end of the file add

# wireless network card driver
blacklist r8180

Reboot and you should be okay well at least I was. Only re-installed three times to get it to work

Good luck

Might find me in this post - I only copied and pasted it:)

[http://ubuntuforums.org/showthread.php?t=588279&page=2](http://ubuntuforums.org/showthread.php?t=588279&page=2)

If you are unsure about any commands ask on the forum first

Welcome to the wonderful world of linux its great free at last!!

__________________

---

### Post by ebeard on 2007-12-05
Thanks for the step by step Alan34. I may build up the courage to try again. 

Step by step instructions like this are a great learning tool to me.

---

### Post by ebeard on 2007-12-06
Well, I tried again. Re: Realtek 8185 on Gutsy.

No luck. Everything seems okay, no kernal panic. When I try to actually do something no packets seem to move. Tried some stuff on other threads and one thing was apparent, DHCP wasn't working, no lease was obtained. 


Anybody have another idea?

---

### Post by alan34 on 2007-12-06
If you go 

System - Administration - Network then click on the DNS tag have you entered the IP address of your router in DNS - (DNS Server- Add) . Mine is 192.168.0.1 but all the different brands of router are different - should be in your documentation that came with the router. Reboot after does no harm.

Did you get this okay? You really must have something like this can you post yours?
alan@alan-desktop:~$ sudo ndiswrapper -l
[sudo] password for alan:
net8185 : driver installed
device (10EC:8185) present (alternate driver: r8180)

If not we have problems.

Using a terminal we can see how far your network can get.

Applications - Accessories - Terminal

ping "the ip address of your router"

for me
alan@alan-desktop:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=0.977 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=0.969 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=0.926 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=64 time=1.16 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=64 time=1.04 ms

--- 192.168.0.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3997ms
rtt min/avg/max/mdev = 0.926/1.016/1.162/0.082 ms
alan@alan-desktop:~$ 

This shows you are okay out to your router

for the internet
alan@alan-desktop:~$ ping [www.bbc.co.uk](www.bbc.co.uk)
PING [www.bbc.net.uk](www.bbc.net.uk) (212.58.253.70) 56(84) bytes of data.
64 bytes from www1.cwwtf.bbc.co.uk (212.58.253.70): icmp_seq=1 ttl=246 time=49.0 ms
64 bytes from www1.cwwtf.bbc.co.uk (212.58.253.70): icmp_seq=2 ttl=246 time=49.8 ms
--- [www.bbc.net.uk](www.bbc.net.uk) ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 6002ms
rtt min/avg/max/mdev = 48.044/48.967/49.813/0.561 ms

Post how you get on good luck

---

### Post by ebeard on 2007-12-20
Don't want to hijack the thread, but my 8185 is working now. 

Did a fresh install, used ndiswrapper with some different realtek drivers. Key though seemed to be clicking network icon  and setting up "other wireless network" with roaming on. I previously had roaming off and set identity there. The network uses WEP and does not broadcast ssid.

---

### Post by krok on 2008-01-28
Well. it did not work for me. I did exactly as above (including blacklisting the linux driver). After rebooting, my wlan interface appears as "UNCLAIMED" and the network manager does not display any wireless options.

Any ideas? I thought it may be the ndiswrapper driver, which I duly uninstalled and reinstalled, but still no effect. How do i "reclaim" my wireless card?

krok

ps. here is what I get from lspci

krok@krok-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
**01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)**
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
04:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)


AND:

/lib/modules/2.6.22-14-generic/ubuntu/wireless/fsam7400.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/prism2_usb/prism2_usb.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/at76/at76_usb.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/acx/acx.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rtl8180/rtl_ieee80211/ieee80211-rtl.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rtl8180/rtl8180/r8180.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/iwlwifi/mac80211/origin/net/mac80211/iwlwifi_mac80211.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/iwlwifi/mac80211/origin/net/mac80211/iwlwifi_rc80211_simple.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/iwlwifi/iwlwifi/origin/iwl4965.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/iwlwifi/iwlwifi/origin/iwl3945.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/ipw3945/ipw3945.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/p54/p54common.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/p54/p54usb.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/p54/p54pci.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/rt2400pci.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/rt2x00lib.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/rt2500pci.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/eeprom_93cx6.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/rt2500usb.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/rt61pci.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/rt2x00usb.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/rt73usb.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/rt2x00pci.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/p80211/p80211.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rtl818x/rtl8187.ko

AND:

krok@krok-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:1a:92:39:ad:63
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.0.7 duplex=full firmware=N/A ip=192.168.2.12 latency=0 link=yes module=atl1 multicast=yes port=twisted pair speed=100MB/s
**[COLOR="Red"]  *-network UNCLAIMED[/COLOR]**
       description: Ethernet controller
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:01:01.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32

---

