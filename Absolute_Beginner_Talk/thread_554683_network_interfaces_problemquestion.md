---
title: "network interfaces problem/question"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by leftyfrizzell on 2007-09-19
Here is my etc/network/interfaces file:

auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-key s:xxxxxxxxxxxx
wireless-essid xxxxxxxxxxxx

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0

auto eth1

I have been trying for several months to get my hawkings 8UD working.  Works fine with fedora and several others.  But, for the live of me, I cannot get it to work with UB Tribal 5+ or any other UB derivative.

This is a USB wifi card.  What concerns me is that UB appears to identify this connection as eth1 and not wlan* anything.  Is this correct or should there be other entries.  

Any help would be appreciated.  This thing sees others sites in the network.  But does not seem to get an IP address from dhcp.  Everyone else seems to be working with wlan0...I don't know why mine seems to be eth1.

appreciate it.

---

### Post by ayenack on 2007-09-19
Edit you /etc/network/interfaces to look like this.

auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-key sxxxxxxxxxxx
wireless-essid xxxxxxxxxxxx

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp


auto eth0

auto eth1

Save it and reboot. It's not uncommon for wireless usb cards to show up as eth1 or some other strange name.

Best of luck. ayenack.

Let me know if this works.

---

### Post by leftyfrizzell on 2007-09-20
Thanks, while it didn't solve the problem, it made a significant contribution to the solution.  Things seemed to act differently after the change in the file.  I hacked around with it for a couple of hours this evening.  I mad it into an open system and found out I could now connect.  This is something that I've never been able to work before.  So, your advice definitely helped fix it.

Also, it seems that there is some problem in WEP between the router and my wireless.  WEP wprks with the two other windows machines in my home...but, not with UB.  Same configuration, windows works...UB don't.  Can't use WPA because this POS router only does WEP.  Have a call into Verizon to see about a possible replacement.  May be as simple as a software upgrade.

lefty

---

### Post by ayenack on 2007-09-20
Cool. Glad you got wireless working.

If you want to get WEP working you might try this. Make a backup of network interfaces first.

**sudo cp /etc/network/interfaces /etc/network/interfaces_backup**

Then.

**gksudo gedit /etc/network/interfaces**

Then make eth1 look like this.

[B]iface eth1 inet dhcp
pre-up ifconfig eth1 up
wireless-essid "your_access_point"
#wireless-key sxxxxxxxxxxx #Use this line for hexidecimal keys
#wireless-key xxxxxxxxxxxx #Use this line for ASCII keys (string)
auto eth1[/B]

You will need to un-comment "#" the type of key you are using on the lines "wireless-key". Save the file reboot and see how it goes.

Well good luck. Post back if it works or not. Are you using xubuntu btw?

To restore the Network Interfaces if this does not work do this.

**sudo cp /etc/network/interfaces_backup /etc/network/interfaces**

ayenack.

---

### Post by leftyfrizzell on 2007-09-20
I did that and still have "requesting dhcp address" just sitting there doing nothing.  My browsing around shows that Fedora, et al don't have this problem as they read another config file in another directory.  Any more ideas?

thanks,

lefty

---

### Post by str8line on 2007-09-21
As far as connecting that card using WEP encryption, depending on the modem the SSID (network name) and the default WEP key will be located on the FCC label on the modem.  Default for wireless modem/route's from Verizon is 64bit WEP.

---

### Post by ayenack on 2007-09-21
Oh well worth a try. Can you post the results of these commands. In terminal.

**iwconfig eth1**

**sudo lsusb -v** (post the bit that list your USB wireless card)

**ifconfig eth1**

Edit out anything you don't feel comfortable posting from the results of these. Need to see exactly what card you have.

Thanks. ayenack.

Might be an idea to attach these to a file and post them.

---

