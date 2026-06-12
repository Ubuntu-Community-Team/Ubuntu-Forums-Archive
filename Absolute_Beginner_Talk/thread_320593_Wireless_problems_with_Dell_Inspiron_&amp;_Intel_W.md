---
title: "Wireless problems with Dell Inspiron &amp; Intel Wireless"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by bobfarrell on 2006-12-17
Hi,

I install Ubuntu and it detects my ipw2200 chipset without any trouble at all, and from the research I've done, most people seem to have it working right away when they install (even when running the Live CD), but I can't seem to get it to activate.

The driver's loaded, but the little WiFi light above my keyboard (next to the caps lock light) doesn't switch on.  In Windows, this switches on as Windows loads.

There's a shortcut key to switch it on/off (Fn+F2), but if I press it once, it's switched off when I boot Windows, twice and it's on: i.e., as far as the shortcut key's concerned, it's switched on.  Does anyone know how to enable radio, or is there something else I need to do first?

I've tried everything I can think to do (which isn't very much), including downloading and attempting to install new drivers, but I did more harm than good.  I just want to get my net connection up so I can learn the rest from the web, rather than keep switching between the two operating systems trying in vain to get something working.

Thanks for any help.

---

### Post by jpkotta on 2006-12-17
The light can be enabled by a patch, I think, but is not on by default.  You can check if your radio is on by running the command```
iwconfig
```On my laptop (which is a Lattitude D610 with ipw2200), the wireless interface is eth1.  Here is the output:> 
eth1      IEEE 802.11g  ESSID:"NDSU"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0B:85:51:08:EF   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=78/100  Signal level=-51 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3274   Missed beacon:0
It is active.  If the radio is off, it will say "radio off".  BTW, my FN+F2 works to turn it on and off out of the box.

---

### Post by bobfarrell on 2006-12-17
I've just had another crack at it and I'm still not getting anywhere.

The progress I've made is that the device *is* working - I can use
```
sudo iwlist eth1 scan
```

and it shows me a list of all the wireless networks within range, but it all goes wrong when I try to get an IP address - ```
sudo dhclient eth1
```

I'm afraid I can't copy & paste the terminal output as I'm in Windows now but it basically just tries in numerous slots and comes back without being able to assign an IP.

So, as far as I can see, the drivers are fine, as the interface is operational, but it won't connect to my router, but it connects fine under Windows.

---

### Post by houstonbofh on 2006-12-17
> **bobfarrell said:**
> I've just had another crack at it and I'm still not getting anywhere.

The progress I've made is that the device *is* working - I can use
```
sudo iwlist eth1 scan
```

and it shows me a list of all the wireless networks within range, but it all goes wrong when I try to get an IP address - ```
sudo dhclient eth1
```

I'm afraid I can't copy & paste the terminal output as I'm in Windows now but it basically just tries in numerous slots and comes back without being able to assign an IP.

So, as far as I can see, the drivers are fine, as the interface is operational, but it won't connect to my router, but it connects fine under Windows.
Is it an open AP?  If you are not running WEP or WPA it should just work.  If you are running WEP, you need to configure it within the network manager.  WPA may require additional software.

---

### Post by bobfarrell on 2006-12-17
Yeah, it's WEP, I've put the network name and password in to the network manager but that doesn't help.  I'm going to try a few more things (maybe just bypass DHCP and set a static IP).

Here's as extensive a checklist as I can think of right now:

Checked modules are loaded, and the driver seems to be working fine, as I can detect all local networks.

I've set network name and password in network manager.

Well, I mean, that's about it, really, isn't it?  Like you said, it should just work.  :(

Thanks for all the help anyway.  I really want to get this working, I've become more than fed up with Windows lately.

---

### Post by bobfarrell on 2006-12-17
Right, well bypassing DHCP made one thing obvious that I hadn't noticed before:
the signal strength is at 0%.  Once I bypassed DHCP and set a static IP, the connection appeared in the connection monitor, and there it showed the strength (I know it was in the iwconfig thing too but didn't seem as obvious then).

I was fiddling round with a few things and I noticed that every now and then the strength would shoot to 100% and then fall back down straight away to zero, maybe every five minutes or so.  So that seems to me to be the problem, but I'm afraid I have no idea how to fix that.  The only thing I can think to try is to change power management settings like it says to [here]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-2e426b202454e898950d58705107ed41c99dc25b")

"Try booting with kernel option pci=noacpi or acpi=off as acpi sometimes conflicts with network devices. The second option will affect power management."

Edit: I tried adding that flag into /boot/grub/menu.lst for the kernel I'm using and it didn't make any difference - still no signal being picked up. :(

---

