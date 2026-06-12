---
title: "Report: installing full WiFi (up to WPA2) on a 2nd generation MacBook Pro"
date: 2007-11-07
forum: Apple Intel Users
---

### Post by GeneralSunTzu on 2007-11-07
I am glad to report that I was able to install madwifi on a 2nd generation MacBook Pro with Gutsy Gibbon without any of the apparent voodoo that some people claim is necessary.
I have to thank the good people who maintain this guide:
[https://wiki.ubuntu.com/MacBookPro](https://wiki.ubuntu.com/MacBookPro)

as their pointers are version independent, work and require no unintelligible manipulation.

I executed these instructions:

sudo aptitude install build-essential
wget [http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz](http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz)
tar -zxvf madwifi<tab>
cd madwifi<tab>
make
sudo make install

And I did not even need to reboot, as these commands installed the driver straight away:

sudo modprobe ath_pci
sudo modprobe wlan_scan_sta

I still recommend not to use these commands, but to refer to the page I gave, as they might change.

Once installed the driver, I opened the network manager, which showed all the WiFi networks visible, entered the passphrase of my WPA2 network and I was good to go.
Brilliant!
Now, let's turn to how to tame my trackpad...

---

### Post by david_edmundson on 2007-11-07
Nice summary. I don't think many people need any Voodoo magic if they are going from a clean Gutsy installation

Personally I prefer to user
"fakeroot checkinstall"
rather than
"sudo make install'

(obviously this requires checkinstall and fakeroot to be installed)

checkinstall monitors where it's trying to put files, but rather than copying simply makes a debian package. This can then by installed with dpkg -i madwifi-****.deb or simply double clicking. As files need to be "owned" by root this can be achieved with fakeroot.

The advantage of this is it can be uninstalled easily, and is technically safer.

Just my $0.02.

---

