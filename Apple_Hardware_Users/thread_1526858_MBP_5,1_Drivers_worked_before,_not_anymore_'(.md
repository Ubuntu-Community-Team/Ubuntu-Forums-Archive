---
title: "MBP 5,1 Drivers worked before, not anymore :'("
date: 2010-07-08
forum: Apple Hardware Users
---

### Post by tjw09003 on 2010-07-08
A couple of months ago I installed Ubuntu 9.10 on my MBP 5,1
After the install I used "Hardware Drivers" window to install the broadcom 4322 drivers. It worked easily.

Now I reformatted the system, and reinstalled ubuntu 9.10 on my mbp for reasons I won't go into.

Wireless doesn't work, as expected but when I got in "Hardware Drivers" to get wireless working it says "No proprietary drivers are in use on this system". 

Any Ideas why? Remember, It all worked flawlessly before...

---

### Post by linuxopjemac on 2010-07-08
You have to hook your Mac up to the internet with a cable connection and do:

```
sudo apt-get update
```

Then try again with Hardware drivers

---

### Post by tjw09003 on 2010-07-08
That did nothing with the "Hardware Drivers" window :D

It's still not showing any devices for proprietary drivers. On My last install the broadcomm, nvidea, and some other devices showed up on the list to enable the drivers. This time there is nothing

---

### Post by alexmurray on 2010-07-08
Try manually installing the bcmwl-kernel-source package from software center.

---

### Post by tjw09003 on 2010-07-09
after restarting the system the broadcomm drivers should up in the list. For the nvidia drivers i just went to the official Nvidia download page [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) , downloaded and installed.

It all works good now :D

---

