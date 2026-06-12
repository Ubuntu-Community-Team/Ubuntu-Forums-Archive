---
title: "24&quot; LED Cinema Display + BT keyboard/mouse"
date: 2009-03-29
forum: Apple Hardware Users
---

### Post by hajk on 2009-03-29
I've been trying to install Jaunty Beta on my 2009 Mac Mini 3,1 + Apple BT keyboard and mouse + 24-inch Apple LED Cinema Display (ALCD):

1. The BT keyboard and mouse work in USB-HID mode, alas without scroll-ball support on the mouse and 
fn-key support on the keyboard. This can be fixed with temporary USB keyboard and mouse, more or less as 
described in [http://idebian.wordpress.com/2008/07/06](http://idebian.wordpress.com/2008/07/06).

Note that the *hidd* command is not available in Jaunty, as its functionality has been subsumed by the 
Bluetooth applet, which also scans for connectable BT devices.
Unfortunately, the resulting Bluetooth pairings in Jaunty did not survive a reboot...

As an aside: the recipe at the above noted site, using the *hidd* command, works fine in Debian Squeeze/Sid, 
also after a reboot. I'll keep an eye out for the next version of the Bluetooth applet to incorporate the same 
functionality.

2. The combination of nVidia GeForce 9400M graphics on the Mini and the new ALCD (connected thru the mini display
port MDP) does not work with the latest nVidia driver. It did work fine that way at full 1920x1200 resolution with 
a Samsung LCD monitor connected via the miniDVI-to-DVI adapter.

The best possible ALCD resolution (also found by the Jaunty installer) is 1280x720 with the VESA driver -- I've 
played around with HorizSync and VertRefresh rates in /etc/X1/xorg.conf to no avail. How disappointing...

Note that Jaunty, of all Debian-based distros, uses the latest Xorg 1.6 version; Debian Squeeze/Sid still 
uses 1.4 and there the ALCD would not work at all... I guess we're waiting for a new Xorg version and 
an update of the nVidia driver for this elegant hardware to work.

Meanwhile, I've scratched my efforts for now to get Jaunty or Squeeze/Sid working directly on this 
elegant combination of hardware. Installing and running these distros in VMware Fusion VMs is a snap, however.

---

### Post by cyberdork33 on 2009-03-29
> **hajk said:**
>  Note that the *hidd* command is not available in Jaunty, as its functionality has been subsumed by the 
Bluetooth applet, which also scans for connectable BT devices.
Unfortunately, the resulting Bluetooth pairings in Jaunty did not survive a reboot...
We had a bug open for this in Intrepid. Might be worth reopening *again*...

---

### Post by hajk on 2009-03-30
OK, I left a comment with one of the newer bugs, 346883, about this.

---

### Post by cyberdork33 on 2009-03-30
here:
[https://bugs.edge.launchpad.net/ubuntu/+source/bluez/+bug/281580](https://bugs.edge.launchpad.net/ubuntu/+source/bluez/+bug/281580)

---

