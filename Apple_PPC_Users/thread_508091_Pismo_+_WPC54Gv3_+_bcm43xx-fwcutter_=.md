---
title: "Pismo + WPC54Gv3 + bcm43xx-fwcutter = ?"
date: 2007-07-23
forum: Apple PPC Users
---

### Post by Alterscape on 2007-07-23
So, I just installed Ubuntu 7.10 PowerPC on my G3 Pismo -- 500mhz, 256mb RAM, 12gb hdd, no internal airport.  When I had OSX on this box, I used a Linksys WPC54G v3 PC card wireless adapter. The Ubuntu community documentation project points me to the following page to install it, but it doesn't seem to be PPC specific: [http://help.ubuntu.com/community/WifiDocs/Device/LinksysWPC54GS-UK](http://help.ubuntu.com/community/WifiDocs/Device/LinksysWPC54GS-UK) which despite the URL actually does contain info on my PC card. ```
sudo lspci
``` returns the string that page says it should, but when I run ```
sudo apt-get install bcm43xxfwcutter
``` I get the following output: first, standard apt-get cruft -- 1 new package installed. Then I get a blue screen warning me that it needs to download the firmware.  It downloads  wl_apsta.o from boredklink.googlepages.com but then gives me the following error: ```
sorry, the input file is either wrong or not supported by bcm43xx-fwcutter.
This file has an unknown MD5sum a58843b5ee79d015adf8c54178186487.
dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 255
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Can I make bcm43xx-fwcutter work on PPC? How? Thanks!

---

### Post by stmiller on 2007-07-23
Try this:

```
$ sudo apt-get install bcm43xx-fwcutter
```

---

### Post by Alterscape on 2007-07-23
Oops, that was a typo in my post, not in what I typed into the terminal. My bad. To be clear, the command I entered was 
```

$ sudo apt-get install bcm34xx-fwcutter

```
so to the best of my knowledge I did not typo while entering the command, just while typing up my first post above.

---

