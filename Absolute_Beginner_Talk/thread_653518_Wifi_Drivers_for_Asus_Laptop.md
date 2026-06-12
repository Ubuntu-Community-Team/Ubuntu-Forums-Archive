---
title: "Wifi Drivers for Asus Laptop"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by beastrace91 on 2007-12-30
Have not posted anything on here in awhile things have been working great. I <3 Kubuntu.

How ever I recently just purchased [this laptop](http://www.newegg.com/Product/Product.aspx?Item=N82E16834220237) and the first thing I did was remove Vist-Aids and but kunbuntu 7.10 on it. How ever it does not detect my wifi card and I am unable to find drivers for it :(

Anyone help? I hate booting it into Xp....

~J3ff

---

### Post by Sef on 2007-12-30
Could you please post your wi-fi card.  thank you.

---

### Post by beastrace91 on 2007-12-30
> WLAN  	 802.11b/g Wireless LAN

Looking for a brand/model now...

~J3ff

---

### Post by beastrace91 on 2007-12-30
Model:

Atheros AR 5006X Wireless Network Adapter

~J3ff

---

### Post by bwtranch on 2007-12-30
Probably want to Google for the chipset, cause I don't know off hand.

---

### Post by beastrace91 on 2007-12-30
I found these links:

[http://ubuntuforums.org/showthread.php?t=429960](http://ubuntuforums.org/showthread.php?t=429960)

and

[http://ubuntuforums.org/archive/index.php/t-541991.html](http://ubuntuforums.org/archive/index.php/t-541991.html)

The second has a broken link and the download from the first keeps giving me errors when running 'make'

~J3ff

---

### Post by bwtranch on 2007-12-30
Well, yeah I read those. First thing to do is find the chipset used in your equipment. Model numbers and brands mean nothing. A company can make a change in chipset at the drop of a hat. It all has to do with cost and market. Serial no. and manufacturer for the chipset and then we can find the driver that works.

---

### Post by Dngrsone on 2007-12-30
Try doing this(items after # are notes, no need to copy them):

```

sudo ifconfig eth0 down   #turn off hard-wired ethernet adapter
sudo modprobe ath_pci   #turn on the Atheros PCI driver, if installed
sudo ifconfig ath0 up      #turn on atheros wifi card
sudo iwlist ath0 scan      #use ath0 to scan for wifi transcievers

```

... and see if you can get some SSIDs.

If so, then you can try

```

sudo dhclient ath0    #log into DHCP server

```

You might be able to get an IP issued.

Now, if you have WEP shared set on your wifi, you may try:

```

sudo iwpriv ath0 authmode 2    #set mode to shared

```

... then run dhclient.

---

