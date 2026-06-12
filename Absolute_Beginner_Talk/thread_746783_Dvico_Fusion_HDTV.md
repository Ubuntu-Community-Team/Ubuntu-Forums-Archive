---
title: "Dvico Fusion HDTV"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by Dionikon on 2008-04-05
Hey there, I'm an absolute noob when it comes to linux, to remedy this situation I decided to build myself a combination HTPC and Asterisk Server.  

So, I have mythtv (mythbuntu) installed and the front/back ends kind of work.  But I can't get my TV Tuner card to work.

I have a Dvico Fusion HDTV express card.  I specifically bought a Dvico as everything I read said it was supported and would work out of the box.  I'm not 100% certain of the model as the manual is for all the different Dvico cards, but I'm fairly certain it's a DVB-T Express.

If I run dmesg (as suggested in a thread I found) I can't find the Dvico board at all, no mention of HDTV, DVB, Fusion, or Dvico.

The way I installed was to install Ubuntu on it's own, then went to the Mythbuntu site and clicked "add to ubuntu".  For the most part this has worked perfectly, I actually thought I must have missed something as it couldn't have been this easy. :p

My system is as follows:

Gigabyte GA-73PVM-S2H
Intel Core 2 Duo 2.2
Pioneer BlueRay ROM
Nvidia 7300 video card
2Gb RAM
320Gb HDD
Dvico Fusion DVB-T Express (I think, but definitely a Dvico Fusion)

Any help would be greatly appreciated, the whole plan kind of falls apart without the TV card.

:)

---

### Post by Dionikon on 2008-04-06
Update: I have found the real model of card I have.

[http://www.fusionhdtv.co.kr/eng/Products/fusion5express.aspx](http://www.fusionhdtv.co.kr/eng/Products/fusion5express.aspx)

---

### Post by Dionikon on 2008-04-06
I guess I'll just keep updating with any new info as it comes to hand.  

Since my last post I found this:

>  Tuners: Dvico FusionHDTV5 Express (PCIE version) Updated 1/5/08 I had to get the latest linuxtv drivers to use the pcie card since kernel 2.6.22.14 doesn't support it.

So off I went and found some instructions on how to do this.

here:
[http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers](http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers)

I did all of this but still no joy.  Although it may have worked, I actually don't really know how to check.  MythTV still says there is an error with the capture card though.

When I add a capture card in MythTV setup it gives me this error message:
```
Could not open card #0 subtype:   No such file or directory
```

---

### Post by Dionikon on 2008-04-07
More progress:
```

[   30.145113] cx23885 driver version 0.0.1 loaded
[   30.145460] cx23885[0]: Your board isn't known (yet) to the driver.  You can
[   30.145461] cx23885[0]: try to pick one of the existing card configs via
[   30.145462] cx23885[0]: card=<n> insmod option.  Updating to the latest
[   30.145463] cx23885[0]: version might help as well.
[   30.145465] cx23885[0]: Here is a list of valid choices for the card=<n> insmod option:
[   30.145467] cx23885[0]:    card=0 -> UNKNOWN/GENERIC
[   30.145469] cx23885[0]:    card=1 -> Hauppauge WinTV-HVR1800lp
[   30.145470] cx23885[0]:    card=2 -> Hauppauge WinTV-HVR1800
[   30.145472] cx23885[0]:    card=3 -> Hauppauge WinTV-HVR1250
[   30.145473] cx23885[0]:    card=4 -> DViCO FusionHDTV5 Express
[   30.145475] cx23885[0]:    card=5 -> Hauppauge WinTV-HVR1500Q
[   30.145476] cx23885[0]:    card=6 -> Hauppauge WinTV-HVR1500
[   30.145483] CORE cx23885[0]: subsystem: 18ac:db30, board: UNKNOWN/GENERIC [card=0,autodetected]
[   30.245609] cx23885[0]: i2c bus 0 registered
[   30.245625] cx23885[0]: i2c bus 1 registered
[   30.245639] cx23885[0]: i2c bus 2 registered
[   30.272352] cx23885_dev_checkrevision() Hardware revision = 0xb0
[   30.272359] cx23885[0]/0: found at 0000:03:00.0, rev: 2, irq: 16, latency: 0, mmio: 0xe5000000

```

As you can see my card is actually listing in the dmesg now.  W00T!!

 So I have tried insmod to manually specify the card number (4), but I get this error:

```

insmod: error inserting '/lib/v4l-dvb/v4l/cx23885.ko': -1 File exists

```

So now I'm really stuck.  Haven't been able to find anything helpful online for this one.

---

