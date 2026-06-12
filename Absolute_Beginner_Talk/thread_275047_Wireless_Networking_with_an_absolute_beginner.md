---
title: "Wireless Networking with an absolute beginner"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by msomers on 2006-10-10
I kept telling myself I'd hold off posting on here, going through pages and pages of wikis to figure out how to do this, but now I'm stumped.

My wireless card is listed as this on the ndiswrapper wiki:
> Card: Buffalo Tech WLI2-PCI-G54

    * Chipset: Buffalo BCM94306 (rev 03)
    * pciid: 14e4:4320
    * Driver: [ftp://ftp.dell.com/network/R81433.EXE](ftp://ftp.dell.com/network/R81433.EXE)
    * Other: Use the .inf in the AR directory. Works with ndiswrappers 0.11 and RHEL 3.
    * Other: Ubuntu 5.04 (Hoary), ndiswrapper 1.0rc2, dell drivers from file R81433.EXE. I used the bcmwl5, not bcmwl5a drivers in the AR directory, not sure of the difference. No luck until I editted *every* .conf file in /etc/ndiswrapper/bcmwl5/, replacing RadioState|1 with RadioState|0. Now it appears to be working perfectly on an open network. 

Anyways, I've been following [these instructions](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) and I finally got up to the part where it tells me to try the commands ifconfig and iwconfig, and when I do this, it lists eth0, eth1, and lo, but no wlan0, and then on iwconfig it gives eth2 as being an IEEE 802.11b/g blah blah, so I'm assuming it finds my card.

Now what...I'm completely lost. I've tried going to the Network Settings and enabling the "Wireless Connection eth2" and going into properties, but then under Network name (ESSID) my wireless network doesn't show up on the drop down menu, and my router is WPA anyways, and only WEP shows up as an option.

Help?

---

### Post by WhiteDawn on 2006-10-10
can you type the ESSID manualy?

---

### Post by msomers on 2006-10-10
Well, the problem is that I have WPA encryption, and only WEP shows up as an option

---

### Post by fazavon on 2006-10-10
this one worked for me

1.2.2.2. Firmware Packages

As an alternative to running the script, you can install the firmware files from a package. To automatically keep up to date, add this repository line to your /etc/apt/sources.list:

deb [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) dapper-cafuego bcm43xx

and make sure apt knows about the GnuPG key used to sign the packages:

wget [http://ubuntu.cafuego.net/969F3F57.gpg](http://ubuntu.cafuego.net/969F3F57.gpg) -O- | sudo apt-key add -

Then update your package listsings and install the bcm43xx-firmware package.

or download the package directly:

wget -c [http://ubuntu.cafuego.net/pool/dappe...buntu1_all.deb](http://ubuntu.cafuego.net/pool/dappe...buntu1_all.deb)

and then install it manually:

sudo dpkg -i bcm43xx-firmware_1.3-1ubuntu1_all.deb

Enjoy!!

---

### Post by msomers on 2006-10-10
How would I do that without an internet connection?

---

### Post by msomers on 2006-10-11
Bump...anyone?

---

