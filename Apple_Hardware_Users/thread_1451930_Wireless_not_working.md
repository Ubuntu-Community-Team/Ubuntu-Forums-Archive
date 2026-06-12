---
title: "Wireless not working"
date: 2010-04-11
forum: Apple Hardware Users
---

### Post by all123me on 2010-04-11
First of all, I've followed all the tutorials about installing ubuntu on a MacBook and installing all the drivers. Everything is working nice, except wireless.

I've installed b43-fwcutter and no wireless networks appear on network-manager, better, it doesn't even say that I have a wireless card.

I've already installed and uninstalled both b43 and STA thru the Hardware Drivers, synaptic and apt (although I think it is the same) and nothing happens.

My MacBook is 5.2 and I'm running 2.6.31-14-generic.

Regards ;)

---

### Post by linuxopjemac on 2010-04-11
Maybe the Debian wiki helps you.
[http://wiki.debian.org/MacBook/Wireless](http://wiki.debian.org/MacBook/Wireless)

---

### Post by marshag63 on 2010-04-11
What kind of card you trying to setup?

MarshaG.

---

### Post by all123me on 2010-04-11
@linuxopjemac, ok, I'll try.

@MarshaG, Broadcom b4322, if I remember correctly.

---

### Post by linuxopjemac on 2010-04-11
b4322 is not supported by b43...

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

So you will need the STA driver by Broadcom in combination with b43-fwcutter.

I would start from scratch, meaning that you should not have b43 as module...(you can lsmod to see if you have b43 loaded, to remove 'sudo rmmod b43' or 'sudo rmmod -f b43'). I would also first purge b43-fwcutter:

```
sudo apt-get remove --purge b43-fwcutter
```

blacklist b43:
 You will need to blacklist the open source drivers (as they can not co-exist). In Ubuntu 9.10 you will need to add the following two lines to /etc/modprobe.d/blacklist.conf:

blacklist b43
blacklist ssb


Step 1. Install the b43/STA hybrid drivers/firmware:

```
sudo apt-get install bcmwl-kernel-source
```

Step 2. Under the desktop menu System > Administration > Hardware Drivers, the driver can be activated for use.

Note: A computer restart may be required before using the wifi card.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

