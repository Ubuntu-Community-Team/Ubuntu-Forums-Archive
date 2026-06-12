---
title: "EeePC upgrade try to 12.04 - no network"
date: 2012-08-30
forum: Asus Ubuntu Support (CLOSED)
---

### Post by ELMIT on 2012-08-30
I upgraded my EeePC from 11.04 to 11.10 and further to 12.04
I used the Ethernet cable to connect to the Internet.

Now at 12.04 I do not have a network anymore!

sudo start networking
=> networking stop/waiting

sudo /etc/init.d/networking restart
* Reconfiguring network interfaces...
Cannot find device "wwan0"

dmesg shows me many lines similar to:
cfg80211: Updating information on frequency 2408 MHz for a 20 MHz width channel with regulatory rule:
cfg80211: 2474000 KHz - 2494000 KHz @ 20000 kHz), (300 mBi, 2000 mBm
....
rt2800pci 0000:01:00.0: PCI INT A disabled

...

eeepc_laptop: BIOS says wireless lan is unblocked, but the pci device is absent
eeepc_laptop: skipped wireless hotplug as probably inapproriate for this model
...



How can I use my EeePC again?


bye

Ronald

---

### Post by ELMIT on 2012-09-02
I downgraded accordingly:
> 

    Roman,

    I had the same issue, luckily I was able to figure out a fix. There appears to be an issue with the latest update of Network Manager. If you open the Ubuntu Software Center, go to History, search the keyword "Network" and you will probably see "network-manager (0.9.4.0-0ubuntu4, 0.9.4.0-0ubuntu4.1)".

    If you see this then you have the same problem as I did. The solution is to downgrade to version 3: Search in Google "ubuntu network-manager package" and select the ubuntu.com link, then scroll down the page to "network-manager-dbg" select the precise (debug) ubuntu3 version.

    [http://packages.ubuntu.com/precise/network-manager-dbg](http://packages.ubuntu.com/precise/network-manager-dbg)

    Download the 4 related packages for your system (amd64 or i386):

    network-manager (= 0.9.4.0-0ubuntu3)
        network management framework (daemon and userspace tools)

    libnm-util2 (= 0.9.4.0-0ubuntu3)
        network management framework (shared library)

    libnm-glib4 (= 0.9.4.0-0ubuntu3)
        network management framework (GLib shared library)

    libnm-glib-vpn1 (= 0.9.4.0-0ubuntu3)
        network management framework (GLib VPN shared library)

    Install each of them using the command sudo dpkg -i FILENAME.

    Restart your computer and that should fix your problem!


Now, I still get during reboot messages about Network problems, but with sudo NetworkManager (nothing else), the Network starts and I have connection. I get now even a 802.11n connection.


How can I get this automatic, so that the Network problem will not be reported with the extra delay of more than 2 minutes?

---

