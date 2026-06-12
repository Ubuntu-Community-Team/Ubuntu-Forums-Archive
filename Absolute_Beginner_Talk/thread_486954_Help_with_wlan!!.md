---
title: "Help with wlan!!"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by jonttix on 2007-06-28
Can anybody help get my wlan working? I have tried with ndiswrapper but then I the System -> Administration -> Network will not find it at all. With the original install it finds it as eth1 but then it cant find the wireless network. I have installed windows on the same laptop and there it works fine. Please help!

---

### Post by nick_h on 2007-06-28
If you post the output of *ndiswrapper -l* and *iwconfig* it will help us know what the problem is.

---

### Post by jonttix on 2007-06-28
ndiswrapper -l:

bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)

iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by speaker219 on 2007-06-28
Hmm, some people might say that you haven't blacklisted your bcm43xx drivers because it says that under the output of ndiswrapper -l, but I am using the same driver (bcmwl5) with ndiswrapper and it says "alternate driver: bcm43xx" on mine even though i have blacklisted the drivers. It works fine on mine, but continues to say it is using an alternate driver. I know it wasn't working before I setup ndiswrapper, so It can't be using those drivers.
Also, can you post the output of:
```
sudo iwlist eth1 scanning
```

If you see your wireless network after that command, then the wireless card is working properly.

---

### Post by tarek on 2007-06-28
Hi, I have bcm43xx and I followed this how-to and it worked:  [http://ubuntuforums.org/showthread.php?t=197102]("http://ubuntuforums.org/showthread.php?t=197102")

Give a try.

tk

---

### Post by speaker219 on 2007-06-28
> **tarek said:**
> Hi, I have bcm43xx and I followed this how-to and it worked:  [http://ubuntuforums.org/showthread.php?t=197102]("http://ubuntuforums.org/showthread.php?t=197102")

Give a try.

tk
He has already done that.

---

