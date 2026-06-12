---
title: "[SOLVED] ethernet card - checking and possibly installing driver"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2008-03-15
My onboard ethernet card doesn't work sometimes so I had an additional one put in.
Now how do I figure out if it was picked up by Gutsy or if I need to install the drivers?

---

### Post by kleo skywalker on 2008-03-15
I know it's too early to bump, but I'm hoping to get this sorted out before my onboard ethernet card conks out and I'm stranded without internet.

---

### Post by ugm6hr on 2008-03-15
Try plugging it into your router and restart.

If it works, then you have your answer!

If you want to check within Ubuntu, this command will identify the driver
```
lshw -C network
```

---

### Post by kleo skywalker on 2008-03-15
> **ugm6hr said:**
> Try plugging it into your router and restart.

If it works, then you have your answer!
I'll try this out.
In the meantime, I ran
```
lshw -C network
```
and got the following result:
>   *-network:0 DISABLED    
       description: Ethernet interface
       product: Hangzhou Silan Microelectronics Co., Ltd.
       vendor: Hangzhou Silan Microelectronics Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 01
       serial: 00:e0:20:73:47:2c
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sc92031 driverversion=2.0c duplex=half latency=32 link=yes maxlatency=40 mingnt=20 module=sc92031 multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 01
       serial: 00:11:11:5e:36:17
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=full firmware=N/A ip=192.168.1.5 latency=32 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
I have no clue what any of it means though. Could someone please tell me?
Thanks.

---

### Post by ugm6hr on 2008-03-15
OK.

This demonstrates you have 2 network cards.

I assume the one you are using is eth0, which is the Intel chipset.

The other one might be a bit of a problem (presumably the card that you have just bought):
[http://ubuntuforums.org/showpost.php?p=4060137&postcount=74](http://ubuntuforums.org/showpost.php?p=4060137&postcount=74)

If it doesn't work (which I suspect it won't), I'd save your energy and get another one.

---

### Post by kleo skywalker on 2008-03-15
ugm6hr, I checked out that post. One of the links refers to a very similar model, but a rather old one. I bought mine just a couple of months ago.
It came with a CD, which has something for Linux - a .tgz archive. No instructions though. (A screenshot of the contents of the CD is attached.)
I suppose it's worth a shot? I have no idea what to do though.

---

### Post by ugm6hr on 2008-03-15
You may be in luck.... but I am not sure.

The CD may have a driver, but you need to check the readme to see if it is a driver for Linux kernel 2.6.

Also, Ubuntu seems to have already installed a driver.

If it is going to work, it will probably work without any further intervention.

---

### Post by kleo skywalker on 2008-03-15
> **ugm6hr said:**
> You may be in luck.... but I am not sure.

The CD may have a driver, but you need to check the readme to see if it is a driver for Linux kernel 2.6.

Also, Ubuntu seems to have already installed a driver.

If it is going to work, it will probably work without any further intervention.

There is no readme.

I'll just plug my modem into this other card and see if it works. Or do I need to enable it or something? It says "DISABLED" next to it in the output to that command.

---

### Post by ugm6hr on 2008-03-15
> **kleo skywalker said:**
> There is no readme.

I'll just plug my modem into this other card and see if it works. Or do I need to enable it or something? It says "DISABLED" next to it in the output to that command.

Not 100% sure how to change the DISABLED status.

Do you have Windows on the machine too (or was the card previously on a Windows box)?  If so - it may be a power-saving issue, which needs to be corrected in Windows before installation in Ubuntu.

But it is more likely to be that the driver doesn't work properly.

---

### Post by kleo skywalker on 2008-03-15
> **ugm6hr said:**
> Not 100% sure how to change the DISABLED status.

Do you have Windows on the machine too (or was the card previously on a Windows box)?  If so - it may be a power-saving issue, which needs to be corrected in Windows before installation in Ubuntu.

But it is more likely to be that the driver doesn't work properly.

No, I don't have Windows, and the card was not previously on a Windows box.
Isn't there a setting for this in the BIOS somewhere?

---

### Post by ugm6hr on 2008-03-15
> **kleo skywalker said:**
> Isn't there a setting for this in the BIOS somewhere?

Have a look in BIOS.

But generally it should be on by default.

---

### Post by Cyanic420 on 2008-03-15
I suspect that you would not see it if it was disabled in the BIOS. Does Ubuntu have ethtool and the ifup and ifdown scripts? Sorry I have a RedHat background, and I'm downloading Ubuntu to check it out.

---

### Post by kleo skywalker on 2008-03-17
I just had to disable the onboard LAN in the BIOS for the additional LAN card to work. I did that, and opened up a couple of websites, seemed to work ok.
Thanks.

---

