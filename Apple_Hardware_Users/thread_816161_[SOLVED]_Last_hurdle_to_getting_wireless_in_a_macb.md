---
title: "[SOLVED] Last hurdle to getting wireless in a macbook pro"
date: 2008-06-02
forum: Apple Hardware Users
---

### Post by a1234 on 2008-06-02
Using this great instruction

[https://wiki.ubuntu.com/MacBookPro/Penryn?highlight=(macbook)|(pro](https://wiki.ubuntu.com/MacBookPro/Penryn?highlight=(macbook)|(pro))

 wireless on my mbp3 has recognized wlan0 as well as shown activities. However it is still not connecting!
It is repeatedly asking for pass word even after being configured. 
Any idea how to get over this hurdle?

a1234@a1234-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 05
       serial: 00:1e:c2:bb:97:73
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,09/20/2007, 4.170. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth0
       version: 13
       serial: 00:1f:5b:e7:1a:b8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
a1234@a1234-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
a1234@a1234-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ]

---

### Post by cyberdork33 on 2008-06-02
There seems to be a problem with this. Many people have reported the problem, but there is no sure-fire solution yet. You can try to compile the latest version of ndiswrapper  since it lists something about an authentication loop being fixed.

>  Version 1.53 has been released. Short summary of changes since 1.52: 

[LIST]
[*]Implemented va_list conversion for x86_64, which fixes oops in     vsprintf() and vsnprintf().
[*]Fixed oops on unload if using our workqueue implementation with SMP enabled.
[*]Don't change the actual thread priority, just pretend it was changed.
[*]Implemented format string conversion for x86_64, so that Windows long     is mapped to Linux int.
[*]Fixed most sparse warnings.
[*]Simplified code and build system to remove already broken support for     Linux versions prior to 2.6.16.
[*]Added .size and .type for all functions in win2lin_stubs.S to improve     backtrace on x86_64.
[*]***Fixed rx key authentication sequence number conversion from Windows to   Linux so WPA authentication doesn't sometimes go into re-key auth loop.***
[/LIST]


---

### Post by a1234 on 2008-06-02
Thank you cyber... for sticking through thick and thin.

---

### Post by hajk on 2008-06-03
> **cyberdork33 said:**
> There seems to be a problem with this. Many people have reported the problem, but there is no sure-fire solution yet. You can try to compile the latest version of ndiswrapper  since it lists something about an authentication loop being fixed.Tried that, doesn't work on MBP 4,1 with the rev 05 Broadcom 4328 chip either.

---

### Post by a1234 on 2008-06-03
> **cyberdork33 said:**
> There seems to be a problem with this. Many people have reported the problem, but there is no sure-fire solution yet. You can try to compile the latest version of ndiswrapper  since it lists something about an authentication loop being fixed.

Good news cyber--. **[COLOR="Red"]It actually is working fine in an none encrypted[/COLOR]** network. Now I have Wifi for my penryn MBP.

Some anecdotal mistakes to avoid are:

1) Do not use the Dell's Driver. It will lock up the CPU guaranteed!
use this one from this link

[http://ubuntuforums.org/showthread.php?t=800618](http://ubuntuforums.org/showthread.php?t=800618)

2)Use this link for the edit instead of the wiki link

[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/197558](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/197558)

It is more explicit in editing the /etc/init.d/ndiswrapper.

3)Must connect only to an unencrypted network for now.

Hope this will help others.

---

