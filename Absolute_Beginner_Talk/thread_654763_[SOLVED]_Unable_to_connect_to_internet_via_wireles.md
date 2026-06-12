---
title: "[SOLVED] Unable to connect to internet via wireless router"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by marvuk on 2007-12-31
Hi all,

I'm a complete newb to Linux & have just installed Ubuntu 7.10 gutsy gibbon on Dell Vostro laptop dual booting with Vista. I intended to connect to internet & begin my Linux learning path from there but have already hit this 1st hurdle! 

I usually connect to internet using a Linksys WAG54g wireless router and make use of the laptop's in-built wifi capability to connect (using Windows). I am wondering if there is a setting i'm missing here as I input the correct network details upon configuration (within network setting window).

Have rebooted 3 times (once using CD) but to no avail. Looked through other posts similar & discovered my wireless chipset is Broadcom wlan & all ok.

Thanks in advance guys

---

### Post by nick_h on 2007-12-31
Please post the output of:
```
sudo iwconfig
```

---

### Post by punkybouy on 2007-12-31
Also can we get the results of an lspci?  Does your restricted drive manager applet report the wireless card?

---

### Post by marvuk on 2007-12-31
Hi, it states:

lo no wireless extensions.

eth0 no wireless extensions.

eth1 IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
mode:managed  access point: Invalid
RTS thr:off  Fragment thr:off
Encryption key:off
Link Quality=0/100 signal level=-256 dbm noise level=-256 dbm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0  Missed beacon:0

---

### Post by nick_h on 2007-12-31
OK that's good.

Now try to scan for routers with:
```
sudo iwlist eth1 scan
```

---

### Post by marvuk on 2008-01-01
Hi nick & thanks for your help, after scanning for routers using the above - the system states:

eth1   Interface doesn't support scanning : No such device

---

### Post by nick_h on 2008-01-01
You are not alone - other people are having the same problem - [link](http://ubuntuforums.org/showthread.php?t=635207).

It seems that you need to go down the ndiswrapper route rather than using the native driver.  There are a couple of guides [here](http://ubuntuforums.org/showthread.php?t=185174) and [here](http://ubuntuforums.org/showthread.php?t=475963).

---

### Post by punkybouy on 2008-01-03
You might check out this link to another who has the same card but using it on an earlier version of Ubuntu.

[http://ubuntuforums.org/showthread.php?t=281990](http://ubuntuforums.org/showthread.php?t=281990)

---

### Post by gbold on 2008-01-03
Can you see your network in the Network Manager?
You can try the stickies on the wireless networking forums:

[http://ubuntuforums.org/forumdisplay.php?f=136](http://ubuntuforums.org/forumdisplay.php?f=136)

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

I had the same problem (Intel chipset) and i solved it by deleting everything except the first 2 lines in the /etc/network/interfaces file (about the lo connection) and rebooted...
Greg

---

