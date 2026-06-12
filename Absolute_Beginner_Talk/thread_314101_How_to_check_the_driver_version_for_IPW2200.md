---
title: "How to check the driver version for IPW2200?"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by kilou on 2006-12-07
Hi,

is there any command to check what version my Intel wireless card (IPW2200) is using? I need to know this because there are firmwares available but it depends on the driver version ([http://ipw2200.sourceforge.net/index.php)](http://ipw2200.sourceforge.net/index.php)).

PS: I'm running Edgy.

---

### Post by djf_jeff on 2006-12-07
If you are running Edgy, the firmware version is 1.3. But to be sure, open a terminal and go in /lib/firmware/2.6.17-10-generic/.

You will see file named ipw2200-1.3.fw or something like that. The 1.3 is the firmware version.

---

### Post by amo-ej1 on 2006-12-07
```

e@lap:~$ dmesg | grep ipw
[   31.886992] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
[   31.886996] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   31.886998] Driver 'ipw2200' needs updating - please use bus_type methods
[   31.887103] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   32.333263] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)

```

edit: why are you searching for firmwares ? the kernel images comes with the required firmwares, it worked out of the box for me.

---

### Post by kilou on 2006-12-07
I checked in /lib/firmware/2.6.17-10-generic/ and there is a file named ipw2100-1.3.fw (not ipw2200-1.3.fw). Don't know if this is a problem though.

Anyway I wonder if this 1.3 is the version of the driver or the one of the firmware....because according to [http://ipw2200.sourceforge.net/firmware.php](http://ipw2200.sourceforge.net/firmware.php) I should download firmware 3.0 (if I have a driver version 1.1 or above).

I have some troubles getting wifi to work and I though a firmware update may help.

---

### Post by djf_jeff on 2006-12-07
Like amo-ej1 say in his post, do :

dmesg | grep ipw

And check for the line that say :

Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq

So, with edgy, you are already at the lastest version. What is your problem with your wireless connection?

---

### Post by kilou on 2006-12-07
Thanks for your replies! Probably I already have the latest firmware then. I have troubles with DNS: I can ping an IP but not the name of a website. Don't know if a firmware may help but I tried every advice but still cannot use wifi (I can connect but cannot browse or ping website with their names). But I will still regularily check the other threads that mention this problem.

Thanks

---

### Post by pourya on 2007-02-07
Hi guys I have the exact same problem the funny part is that it used to work fine few months ago,... I have installed a fresh version of the 6.10 but same problem...
For instance firefox works fine as long as i insert the ip it doesnt work with the domain names.....

---

### Post by pourya on 2007-02-07
hi kilou I have just solved the problem its not the driver thats causing it. the thing is that the DNS is not being resolved.
I just changed
 /etc/resolv.conf to:


search server
nameserver 145.253.2.75
nameserver 193.174.32.18
nameserver 194.25.0.60


and its working fine save a backup of the file before doing it though....
cheers.

---

