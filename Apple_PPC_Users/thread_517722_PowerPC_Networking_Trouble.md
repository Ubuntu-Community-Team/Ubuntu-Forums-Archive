---
title: "PowerPC Networking Trouble"
date: 2007-08-04
forum: Apple PPC Users
---

### Post by contrivereality on 2007-08-04
Recently made the switch to Ubuntu on a Powerbook G4 12'. I love it so far, although I am having trouble connecting the internet. I originally installed at a friends house and was able to use his ethernet cable to connect directly to the internet. Unfortunately when i returned home I discovered that my Wireless Network card (BCM4306) was not supported, thus it would be necessary to install ndiswrapper to gain support. I connected directly to my belkin "n wireless router" via ethernet, and connection properties recognized it instantly although no internet. I promptly opened network settings although it freezes and must be forced to quit. Any help would be greatly appreciated, I realize it might be a multitude of problems.

cheers

---

### Post by stmiller on 2007-08-05
Are you running Feisty? I recommend upgrading to Feisty if you are not already running Feisty.

The Broadcom / Airport Express card driver is built in, however you must fetch the firmware, as the firmware is no an open license which Ubuntu could distribute.

Do this in a terminal:
```

sudo apt-get install bcm43xx-fwcutter

```

reboot, and wireless will work.

---

