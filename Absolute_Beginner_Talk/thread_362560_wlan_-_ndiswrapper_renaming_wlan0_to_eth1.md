---
title: "wlan - ndiswrapper renaming wlan0 to eth1???"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by c00ch on 2007-02-15
WLAN and Ubuntu (edgy) seems to be a never-ending story. :( 

I thought I had figured it all out until I booted up this morning and my wlan adapter was gone. (I probably should add that I did no updates or installs in the previous session, so I was a bit flabbergasted). I checked my configuration via

```
dmesg
```

and - WTH! - for some reason there is this line

```

[17179596.980000] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
```

So using the Gnome-network-manager I changed the active 'eth0' to 'eth1' and back I am in business. :confused: 

Has anybody an idea what that was all about? 

Cheers,
c00ch

---

### Post by thenetduck on 2007-02-16
I don't know what that is all about, but I took a look around in some files and think I found what might be a good solution. Ok so the names of your networking devices are stored in a file, just edit that file and name them to what ever you want them to be (I like to name my Quacker)

It is located here:
  etc/network/interfaces

Make sure to edit it with the sudo command. Should be good to go, Tell me how it goes. 

 Hope this helps,

 The Net Duck

---

### Post by c00ch on 2007-02-16
tee-hee... :) 

bad idea. After fiddling with /etc/network/interfaces/ my wireless adapter is gone for good. \\:D/ 

Ah well... let's see if a ndiswrapper re-install can fix this.

---

### Post by c00ch on 2007-02-16
uh-oh... :-? 

Reinstalling the driver did not help at all. My wireless adapter is gone. Why the hell didn't I back up the interfaces file??? 

Any idea what a pristine /etc/network/interfaces looks like?

---

### Post by Ephack on 2007-02-17
Did you try to reinstall ndiswrapper via this method:
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

If you have a bcm-card of course. It says that you have to comment out the line about eth1 in the file /etc/iftab **before** installing ndiswrapper so that the device gets installed correctly as wlan0.

---

### Post by c00ch on 2007-02-17
Thanks for the link Ephack... sometimes searching the forums just directs you straight past good sources.

Anyway, my network adapter is back up and running. In the end rebooting and manually loading ndiswrapper (**sudo modprobe ndiswrapper**) did the trick. I also had to add a line to /etc/modules in order to get ndiswrapper started automatically upon reboot. To say that this confused me big-time is an understanding as ndiswrapper was autoloading before I fiddled with the interfaces file - I guess it must have something to do with re-installing ndiswrapper.

Most amazingly however, the manual start of ndiswrapper also led to a rename of my wlan adapter from eth1 back to wlan0.  So that is fixed - one of those miraculous linux-self-repairs that leave you wondering whether you're going to be as lucky next time.

Now the last minor inconvenience I have is that my wlan will not connect to the network automatically after boot. I have to use **dhclient** to kickstart it.

---

### Post by MetalMusicAddict on 2007-02-17
Here's my interfaces file:
```
[SIZE="1"]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map wlan0


iface eth0 inet static
address 192.168.1.106
netmask 255.255.255.0
gateway 192.168.1.1

# The primary network interface
iface wlan0 inet static
address 192.168.1.105
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid **********
wireless-key *************************

auto wlan0[/SIZE]
```

Also look at your **iftab** file. **/etc/iftab**

Make sure it has the adapter(s) there with the correct MAC addresses.

---

### Post by c00ch on 2007-02-22
Thanks for that MetalMusicAddict.

I have since somehow fixed the problem. I've fiddled with the interfaces file for quite a while and looking at it today it pretty much resembles what you have posted there. But in the end it was [GTKWifi]("http://gtkwifi.sourceforge.net/") that solved my auto-connect problem.

Although I would love to fully understand how it all worked out, I have now other more imminent problems to deal with (e.g. dual-screen operation). 

So thanks everyone.

---

