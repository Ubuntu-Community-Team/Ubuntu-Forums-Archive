---
title: "Macbook Wireless"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by Activeobserver on 2008-04-03
I am having quite a hard time trying to get my wireless card to work with ubuntu. I am a complete beginner i just got up OS running and now the wireless wont work. I tried to install anything under the sun. I even asked my friend (an experienced user) for help and he couldnt figure it out.

lspci | grep Broadcom\ Corporation
02:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

I tried to use Ndiswrapper with the instructions from [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

It did not seem to work. I was wondering if anyone has a site or a better program to use for my mac. THank you.

---

### Post by ferdostar on 2008-04-03
I'm not sure that your thread is for this section, but nevermind. What kind of Macbook do you have? Have you tried to install the Madwifi driver using the snapshots?

```
sudo apt-get install build-essential autoconf automake
wget http://snapshots.madwifi.org/madwifi-ng-current.tar.gz
tar -zxvf madwifi-ng-current.tar.gz
cd madwifi<tab>
make
sudo make install-modules
echo -e '#!/bin/sh\n/sbin/iwpriv ath0 bgscan 0' | sudo tee -a /etc/acpi/resume.d/99-madwifi-bgscan.sh
sudo chmod 755 /etc/acpi/resume.d/99-madwifi-bgscan.sh
```

---

### Post by Activeobserver on 2008-04-03
i have a duo core intell macbook. It has a BCM4328 wireless. I have tried Madwifi and Subversion. They are not supported with this wireless. Only Ndiswrapper from what i see. However, after i install it, it doesnt seem to work still.

---

### Post by ferdostar on 2008-04-03
This should work with Ndiswrapper  [ftp://ftp.us.dell.com/network/R151517.EXE](ftp://ftp.us.dell.com/network/R151517.EXE)

---

### Post by dark_harmonics on 2008-04-03
> **Activeobserver said:**
> i have a duo core intell macbook. It has a BCM4328 wireless. I have tried Madwifi and Subversion. They are not supported with this wireless. Only Ndiswrapper from what i see. However, after i install it, it doesnt seem to work still.

Actually madwifi does work for that type of card now. I have a new macbook pro (santa rosa) and it works perfectly with madwifi (it used to populate with random wifi errors after 15 minutes but not anymore).

---

### Post by Activeobserver on 2008-04-03
i tried to install madwifi 3times... it just didnt work i used the documentation site for mac with the code posted above.

---

### Post by 3rdalbum on 2008-04-03
Don't Broadcom devices use the bcm firmware cutter? Madwifi is for Atheros and Ndiswrapper is for using Windows-based drivers, unless something has completely changed.

---

### Post by liquidfunk on 2008-04-03
I wish they would put these drivers into the Kernel. Then my Macbook would be powered by the penguin.

---

### Post by Activeobserver on 2008-04-03
Well I am having a hard time with this. I am currently trying to install the R151517 driver see where that takes me. At this point being a complete noob i am totally lost. Does anyone have a good site with instructions to install ndisswrapper or whatever i need to install?

---

### Post by ferdostar on 2008-04-03
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
[http://ubuntu-tutorials.com/2007/03/18/how-to-configure-wireless-on-a-macbook-using-ndiswrapper/](http://ubuntu-tutorials.com/2007/03/18/how-to-configure-wireless-on-a-macbook-using-ndiswrapper/)

---

