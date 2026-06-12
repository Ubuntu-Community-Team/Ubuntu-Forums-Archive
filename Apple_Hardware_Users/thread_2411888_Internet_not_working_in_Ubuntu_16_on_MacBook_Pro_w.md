---
title: "Internet not working in Ubuntu 16 on MacBook Pro with WiFi"
date: 2019-02-05
forum: Apple Hardware Users
---

### Post by kaategikya on 2019-02-05
Hi,

I installed Ubuntu 16.04 on my macbook pro few month back, on that time WiFi & Internet both was working fine. From last few day's I am not able to access internet through wifi ( with WLAN its working fine). I tried everything which available on internet including reinstall OS from scratch.

Can someone help me to solve my issue, please. I am trying from last 5 days but no luck.

---

### Post by praseodym on 2019-02-05
Please run the wireless script from the sticky thread and show the outputs

---

### Post by kaategikya on 2019-02-06
Please download from here.  [https://we.tl/t-zXDFrFA8A5](https://we.tl/t-zXDFrFA8A5)

---

### Post by kaategikya on 2019-02-07
Hi, Can you please help.

---

### Post by howefield on 2019-02-07
Thread moved to the "*Apple Hardware Users*" forum.

Might be a better idea to paste the output from the wireless script here instead of forcing others that might be able to help to go to an unknown site.

---

### Post by kaategikya on 2019-02-09
Hi,

I am getting below output when doing dmesg | grep wl. Its seems my firmware not correctly installed. please let me know how I can be fix.

rishabh@rishabh-MacBookPro:~$ dmesg | grep wl
[   18.258581] wl: loading out-of-tree module taints kernel.
[   18.258585] wl: module license 'MIXED/Proprietary' taints kernel.
[   18.259920] wl: module verification failed: signature and/or required key missing - tainting kernel
[   18.431753] wlan0: Broadcom BCM4331 802.11 Hybrid Wireless Controller 6.30.223.271 (r587334)
[   18.771320] wl 0000:02:00.0 wlp2s0: renamed from wlan0
[   27.991558] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   29.425158] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   81.565027] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready

---

### Post by praseodym on 2019-02-09
SecureBoot is disabled?

---

### Post by kaategikya on 2019-02-09
Thank you for reply. Yes its showing me  “Secure Boot not enabled on this system”.

---

### Post by gsahli on 2019-02-10
Can you look through this and tell us what you've done/not done for your broadcom?

[https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by kaategikya on 2019-02-11
Its showing me 

01:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4] (rev 10)
01:00.1 SD Host controller [0805]: Broadcom Corporation BCM57765/57785 SDXC/MMC Card Reader [14e4:16bc] (rev 10)
02:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)

I installed this package as per instruction " sudo apt-get install firmware-b43-installer" but having same issue.

---

### Post by praseodym on 2019-02-15
Install the Broadcom-STA driver via "Additional Drivers" and deactivate SecureBoot

---

