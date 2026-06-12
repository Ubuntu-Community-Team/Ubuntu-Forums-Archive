---
title: "PPC - Netgear usb wireless working on my G5 iMac!"
date: 2009-01-05
forum: Apple Hardware Users
---

### Post by stream303 on 2009-01-05
Thanks to ringsofsaturn for motivating me not to give up!  He basically showed that the old urban-legend about usb wireless not working on Apple ppc boxes is not true.

To save some time, (and being a post that could really just go into the networking forum now that everything works) I'll post some quick details here hoping that it might inspire other ppc owners not to give up the ship.

Ok, right now I'm running Debian Lenny, but this should work with Ubuntu just fine.

1) Using a Netgear WG111v2 usb stick.  Made sure that the side of the box had "v2" in it.  Nice to see gpl-licensing leaflets fall on the floor.

2) Got the ralink-firmware from the repos and installed via synaptic.  apt-get install fine too.

3) Disabled (uninstalled) Network Manager.  This caused problems on my ibook in the past, so I decided to take one more problem out of the equation. :)

4) To make a long story short, I'm editing **/etc/network/interfaces** directly, and not running wpa.  Even though wpa-supplicant was installed, I couldn't get that to work for some reason.  Maybe a project for later, but too burned out with it now.  Fell back to using WEP-128 bit key in router.  Also relying on hex-keys rather than ascii passcodes.

(Maybe THAT is the ppc-specific gotcha - I wonder if wpa is supported on ppc?)

5) Contents of my /etc/network/interfaces file (the essid and hex key passphrase are obviously bogus - use your own)

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug eth0
iface eth0 inet dhcp

# My custom wireless setup
auto wlan0
iface wlan0 inet dhcp
wireless-key 6a322f2b 
wireless-essid magical 

```

And now, I did come across a disconnect a few times, so I dropped the speed back to 11M in **/etc/rc.local** by adding an iwconfig line *before* exit 0 :

```

# By default this script does nothing.

iwconfig wlan0 rate 11M fixed

exit 0

```

I made sure my router's channel was at least 2 channels away from my neighbors, and by dropping the rate a little bit, I'll see if I still suffer from any random disconnects.  If so, I'll play with 24M, 11M, 5.5M, 2M and 1M if need be.

So far, so good!

---

### Post by stream303 on 2009-01-05
Ok, got the Belkin F5D7050 working too.

Installed the zd1211-firmware from the repos.

The only change I had to make was to reference **wlan1** instead of wlan0.  Not sure if it is because I am testing two devices that show up in a list somewhere, or if the Belkin just likes to be wlan1.

For some reason the signal strength / link quality is fluctuating, but I'm not sure if this is due to some sort of built-in idling.  No wireless expert here that's for sure.

However, the Belkin seems to be holding it's own just as well.

---

