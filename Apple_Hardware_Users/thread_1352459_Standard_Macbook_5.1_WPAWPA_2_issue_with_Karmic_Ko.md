---
title: "Standard Macbook 5.1 WPA/WPA 2 issue with Karmic Koala"
date: 2009-12-11
forum: Apple Hardware Users
---

### Post by BM1322 on 2009-12-11
Howdy!

I seem to be having some troubles with my fresh install of 9.10 on my macbook in regards to connecting to WPA and WPA 2 encrypted network connections. 

I have no trouble connecting to unsecured networks, but as soon as i try and very my password, or in the case of the WPA on campus, my username/password, the connection never gets through and pups up saying i am disconnected from my wireless.

I've already installed the broadcom drivers that were on my OSX disc, and of course gnome network manager is already installed.

Help!

Please and thank you :popcorn:

---

### Post by linuxopjemac on 2009-12-12
as far as I can read from the 5,1 wiki is that you need the restricted Broadcom STA driver from the hardware driver list.

from wired connection:
apt-get update
apt-get upgrade

then try to select the hardware driver. If you still have problems, you should file a bug report.

---

### Post by linuxopjemac on 2009-12-12
in the past I had some strange problems with networkmanager myself. I then switched to wicd. You could also try that.
```
apt-get install wicd
```

networkmanager will then be automatically suppressed.

---

### Post by BM1322 on 2009-12-12
> **linuxopjemac said:**
> in the past I had some strange problems with networkmanager myself. I then switched to wicd. You could also try that.
```
apt-get install wicd
```

networkmanager will then be automatically suppressed.

This worked PERFECTLY.

Thanks man!

---

