---
title: "[Help] Mac, Ubuntu and the Internet"
date: 2011-01-14
forum: Apple Hardware Users
---

### Post by sydney.unc on 2011-01-14
hello :D!

i have partitioned my hard drive and am running Ubuntu 10.10 on my MacBook Pro - it is working beautifully with one major kink. no internet  -.-

i am hoping someone can help me find (or make me o.O?)* a network adapter driver for a MacBook Pro 6,2 to use with Ubuntu 10.10

& i also provided a wonderful picture of the ifconfig info Ubuntu gives me when my computer is plugged into an ethernet connection (it simply does not pick up on anything wireless)

p.s. virtual box is not a solution

[FONT=System][I][SIZE=1]

*should anyone create a network adapter driver to fix this solution homemade: bread, muffins, fudge, etc can be mailed to your home within a week[/SIZE][/I][/FONT]

---

### Post by hawkmage on 2011-01-14
Since it shows eth0 it has a driver.  How are you assigning an IP address to the interface?  Are you using DHCP or static addresses?

---

### Post by darkdragn on 2011-01-14
Most prefer a wireless network adapter, which your macbook should have. Can you show the output of:

ifconfig -a

So we can see if you have one? If you do, you should have a network connection applet docked in the top right of the screen, on the main bar. If not, you can either install it, install wicd (An alternate option), or learn the cli method for connecting to either WEP enabled wireless networks, or WPA enabled wireless networks.
If you are hard wiring it, since it reads that there is an eth0 just run dhclient, or use the same network GUIs mentioned earlier.

---

### Post by sydney.unc on 2011-01-14
> **hawkmage said:**
> Since it shows eth0 it has a driver.  How are you assigning an IP address to the interface?  Are you using DHCP or static addresses?

ipv4 is auto (DHCP)
ipv6 is set to ignore

---

### Post by sydney.unc on 2011-01-14
> **darkdragn said:**
> Most prefer a wireless network adapter, which your macbook should have. Can you show the output of:

ifconfig -a


op - sorry forgot to mention i already did this and had the same result as "ifconfig"

---

### Post by teh603 on 2011-01-15
Check proprietary drivers. My 3,1 Mac Mini requires bcmwl for wifi service, and yours might have the same chipset. You'll need a wired connection to get it, though.

---

### Post by sydney.unc on 2011-01-16
> **teh603 said:**
> Check proprietary drivers. My 3,1 Mac Mini requires bcmwl for wifi service, and yours might have the same chipset. You'll need a wired connection to get it, though.

i do not think this is the case since i have perfectly fine wireless and ethernet connection when i am running my mac through OS X

---

### Post by teh603 on 2011-01-16
> **sydney.unc said:**
> i do not think this is the case since i have perfectly fine wireless and ethernet connection when i am running my mac through OS XHow do you think Apple gets wifi working on their computers? They're probably using the exact same driver and just burying it somewhere in the kernel.

Jockey calls it "Broadcomm STA," and Synaptic/Kpackagekit calls it "bcmwl."

---

### Post by ZeroLinux on 2011-01-18
For us to help you we need to know what driver you need.
In terminal you should do this command:

sudo lspci

After entering password you will see among others string something like:

0b:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)

Tell us what the string is with a word "wireless"

After that we can find a page for you to download driver.
The sign that the driver is installed is - when you do
ifconfig -a
you can see wlan0 interface along with eth0 and lo

---

### Post by sydney.unc on 2011-01-18
> **ZeroLinux said:**
> For us to help you we need to know what driver you need.
In terminal you should do this command:

sudo lspci

After entering password you will see among others string something like:

0b:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)

Tell us what the string is with a word "wireless"

After that we can find a page for you to download driver.
The sign that the driver is installed is - when you do
ifconfig -a
you can see wlan0 interface along with eth0 and lo

okie dokie - here is the information you requested::

BCM 43224 802.11a/b/g/n

---

### Post by teh603 on 2011-01-19
> **sydney.unc said:**
> okie dokie - here is the information you requested::

BCM 43224 802.11a/b/g/nFrom a little google work, that one won't be properly supported until brcm80211 gets added to Ubuntu, probably in 11.10 or so.

Which is frustrating because my 3,1 mac mini uses a driver supported by bcmwl.

---

### Post by sydney.unc on 2011-01-19
> **teh603 said:**
> From a little google work, that one won't be properly supported until brcm80211 gets added to Ubuntu, probably in 11.10 or so.

Which is frustrating because my 3,1 mac mini uses a driver supported by bcmwl.

so basically someone has to make me a driver, or i make one myself or wait until Ubuntu updates ....

---

### Post by Moonreaper205 on 2011-02-03
Hate searching the forums to find a dead end ><

I'm in the same boat as you, ill keep Ubuntu running on my partition for now, would love to browse the internet on it soon.

---

### Post by sydney.unc on 2011-02-04
i hate the spark of hope i get when i get the email notification that someone has replied

:cry:

---

### Post by ronbirrell on 2011-02-08
The BCM43224 driver is available here [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

regards

Ron Birrell

---

### Post by linuxopjemac on 2011-02-08
if you like to go the open source way:
[http://wireless.kernel.org/en/users/Drivers/brcm80211](http://wireless.kernel.org/en/users/Drivers/brcm80211)

---

