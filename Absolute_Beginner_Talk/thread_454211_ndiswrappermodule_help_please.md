---
title: "ndiswrapper/module help please"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by dillinger417 on 2007-05-25
newbie question :) ...

when i run ndiswrapper -l i get:

bcmlw15 : driver installed
device (14E4:4311) present (alternative driver: bcm43xx)


... Now I know this is bad and I tried ' rmmod bcm43xx ' per instructions but then I get
ERROR: Module bcm43xx does not exist in /proc/modules

I added bcm43xx on the blacklist using:

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

and I uninstalled ndiswrapper and reset my computer. Reinstalling ndiswrapper went fine until I typed "ndiswrapper -l " and got the same result... How do I remove reference to bcm43xx as an alternative driver?

---

### Post by shamreez on 2007-05-25
If you are thinking that there might be a problem in your ndis wrapper installation you can use this link

It is pretty usefull helped me a lot

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show")

---

### Post by shamreez on 2007-05-25
it would also be nice to mention your machine specs in the queries

---

### Post by dstew on 2007-05-25
I think "bcm43xx" might need to be modifed to show the real driver name. To list installed drivers, try **modprobe -l bc*** to make sure that name is correct.

Assuming that is the correct name (seems likely) make sure that the driver is blacklisted. Look at the blacklist file:```
cat /etc/modprobe.d/blacklist
```

---

### Post by dillinger417 on 2007-05-25
I'm pretty sure bcm43xx is in fact the driver name and it is on the blacklist...

I did try "rmmod bcm43xx.ko" but I got the same error.

"modprobe -l | grep bcm" gives me...

.../kernel/drivers/bluetooth/bcm203x.ko
.../kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko
.../kernel/drivers/media/dvb/frontends/bcm3510.ko
.../kernel/drivers/ubuntu/wireless/bcm43xx/bcm43xx-mac80211

But "grep bcm /proc/modules" produces nothing...

Does this mean it is listed but not loaded?

I think I can go ahead with the next step for ndiswrapper but I would feel a lot better if the alternative driver wasn't listed.

I'm still trying to straighten this out but I feel I'm making some progress... ;#-o

---

### Post by dstew on 2007-05-26
That should work, or to check installed modules try  ```
lsmod | grep bcm
```

If lsmod doesn't show any bcm modules, it is probably fine to go ahead with ndiswrapper.

---

