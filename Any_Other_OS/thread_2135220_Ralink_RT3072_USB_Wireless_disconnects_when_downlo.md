---
title: "Ralink RT3072 USB Wireless disconnects when downloading, and other issues"
date: 2013-04-13
forum: Any Other OS
---

### Post by fa6ista on 2013-04-13
A little history. 

Mint 11 Katya 32-bit, 2.6.38-16-generic-pae, 4GB RAM, Gnome 2

Moved to a new place, 3-story house, router is upstairs on the 3rd floor, no access to it, 
I am on the first floor; phone and 2 laptops pick the signal fine (3/5 bars, about 800k download speed).

My desktop however is in the corner of the living room, and has an old RTL 8185 wireless PCI adapter, 
which wouldn't even see the wireless network. I tried with an external USB stick (wireless G) on a 6 feet USB cable -
barely sees the network, don't even talk about connecting to it.

So I bought this external USB-N adapter: [USB Wireless Lan 802.11N High Power Adapter w/ 2 Antenna - 2T2R (300Mbps)](http://www.monoprice.com/products/product.asp?c_id=105&cp_id=10501&cs_id=1050109&p_id=8076&seq=1&format=2) - two big antennas, bla-bla.
It has the Ralink RT2770 / RT2720, I needed some time to find good linux drivers (the ones supplied didn't work - d'oh!!!).
The drivers avail for download were for the RT2870 family and compiled fine after some playing with the config.mk file.
The only funny thing is that lsusb shows it as RT3072:
```
	Bus 001 Device 002: ID 148f:3072 Ralink Technology, Corp. RT3072 Wireless Adapter
```

However in modprobe it is rt5370sta:
```
	modprobe rt5370sta
```

Which didn't really bother me as the adapter worked FINE with these drivers, I see twice the amount of networks
compared to my laptop, and it gets 5/5 bars to my wireless when connected. Here's the result of a speedtest:
[img]http://speedtest.net/result/2634362380.png[/img]

Output of /usr/lib/linuxmint/mintWifi/mintWifi.py:
```
	ra0       Ralink STA  ESSID:"D9GY0"  Nickname:"RT2870STA"
		  Mode:Managed  Frequency=2.462 GHz  Access Point: 00:26:B8:18:86:D6   
		  Bit Rate=48 Mb/s
```






So... To the point. To the point**s**, actually.

1.
Upon restart and upon coming back from sleep, the blue light on the wireless adapter is not even on.
I have NO "Wireless Networks" in network manager AT ALL.
As if the adapter is not seen/installed AT ALL. It takes disable/enable network a few times,
a good 2 or 3 tries before it shows up in the network manager and connects.
Sometimes this won't even help, I have to open Additional Drivers and disable/enable the driver, 
then it is back to playing with network manager.

I am at the point where I am not even restarting the computer, nor putting it to sleep!

2.
When it connects, it stays connected - no problem, see history above.
But when I open deluge - IT WILL ONLY STAY CONNECTED FOR A FEW MINUTES, **IF THAT**!!!
Then the adapter drops the signal and reconnects. 

However, if I am downloading something through my browser, or using wget, it is okay - no matter how big of a file...
Almost seems like the adapter doesn't like me deluge - at all...

**So... is it a driver issue or what?!?!** I am really losing my mind...

---

### Post by Gnobody on 2013-04-13
Have you tried the rt2800usb kernel module?

sudo modprobe -r [COLOR=#000000][FONT=Ubuntu Mono]rt5370sta
sudo modprobe rt2800usb[/FONT][/COLOR]

---

### Post by Perfect Storm on 2013-04-14
Moved to Other OS/Distro Support.

---

### Post by fa6ista on 2013-04-14
> **Gnobody said:**
> Have you tried the rt2800usb kernel module?

sudo modprobe -r [COLOR=#000000][FONT=Ubuntu Mono]rt5370sta
sudo modprobe rt2800usb[/FONT][/COLOR]

Returns this:
```
modprobe -r rt5370sta
FATAL: Module rt5370sta is in use.
```

---

### Post by fa6ista on 2013-04-15
Update after a few days of running with said adapter...

ANY big file I try to download, OR when making a call either via Google Talk or Skype will make the adapter disconnect.
I can't even talk for a minute and bam.

Any input?

---

