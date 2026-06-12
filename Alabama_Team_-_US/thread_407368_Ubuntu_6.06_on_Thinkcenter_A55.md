---
title: "Ubuntu 6.06 on Thinkcenter A55"
date: 2007-04-12
forum: Alabama Team - US
---

### Post by Ira on 2007-04-12
Hi

Im installing ubuntu 6.06 on Thinkcenter a55 but my ethernet is not detected. Can anyone help me solve this? How can I get the driver for the gigabit lan, it uses Broadcom Gigabit lan. Would appreciate very much for immediate reply. Thanks

---

### Post by josephus on 2007-04-12
can you post :

```
ifconfig -a
lspci | grep Eth
lshw -class network
```

---

### Post by josephus on 2007-04-12
I think that you have an ethernet controller based on the BCM5786, and from what I've read this is not supported in the kernel that comes with Ubuntu 6.04 (this is solved by default in 6.10, and so reinstalling with Edgy is an easy solution).

If you want to stick it out with 6.04 then you need to compile new drivers.

[http://www.broadcom.com/support/ethernet_nic/netlink.php](http://www.broadcom.com/support/ethernet_nic/netlink.php)
related posts are:
[http://ubuntuforums.org/showthread.php?t=323667](http://ubuntuforums.org/showthread.php?t=323667)
I'm not sure how easy this is to do given that you do not have an internet connection on that machine, as this involves installing several packages that you need to first download.  You'll likely try to download a package and install it, only to find that you are missing some dependency.  It'll probably take a couple of tries but eventually you'll get everything you need. Give it a shot if you want.

Another post suggests that this problem might be solved in a recent kernel update:
[https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/72696/+viewstatus](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/72696/+viewstatus)

*If* this is true then all you need to do is just copy the newest kernel over to your system and restart, and your network card should work.  To install the package, copy the file and install it using
```
sudo dpkg -i <package_name>
```

[http://packages.ubuntu.com/dapper/base/linux-image-2.6.15-28-386](http://packages.ubuntu.com/dapper/base/linux-image-2.6.15-28-386) or
[http://packages.ubuntu.com/dapper/base/linux-image-2.6.15-28-686](http://packages.ubuntu.com/dapper/base/linux-image-2.6.15-28-686)
depending on which kernel you are currently using.  (type in a terminal: uname -a).  Mind you I've never updated a kernel using this method before, and it might break your system (I would say the chances of that happening are low, but I feel it's necessary for me to put this disclaimer).

These are just some ideas.  Hope one these helps.

(Then again this might all be because something is just misconfigured on your current system - but can't tell for sure based on my current information of your system)

---

