---
title: "intel server board and XP and nvidia driver cant install"
date: 2011-09-01
forum: Any Other OS
---

### Post by sdowney717 on 2011-09-01
[http://www.geeks.com/details.asp?InvtId=S875WP1-E-P428-NP&cpc=SUGG](http://www.geeks.com/details.asp?InvtId=S875WP1-E-P428-NP&cpc=SUGG)

I have this board and I cant get the latest nvidia driver going.

I get "graphics driver could not find compatible hardware" error

however the card is a nvidia geforce 6200 NV44a which the driver 280 supports.

I dual boot between linux and XP and want XP simply cause I have a vbox cats eye 3560 that linux knows zero about.

found some info and going to try it with the 260 driver for xp
[http://blog.komeil.com/2010/04/nvidia-driver-windows-7-notebook-laptop.html](http://blog.komeil.com/2010/04/nvidia-driver-windows-7-notebook-laptop.html)

---

### Post by Duncan Williams on 2011-09-03
if your still stuck, post back...

---

### Post by sdowney717 on 2011-09-03
oh yes, it still wont install!
that inf copy file method, there is no inf file in that archive from nvidia, so it did not work.

This is not a laptop, it is a desktop pc.

---

### Post by mips on 2011-09-03
First go to the Intel site and download the chipset drivers for that MB before trying to install the GPU drivers. Something worth trying.

---

### Post by Duncan Williams on 2011-09-03
**Windows drivers are here:**
(just choose details and XP)
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
[IMG]http://files.myopera.com/DuncanWilliams/usercss/6200.png[/IMG]

**vvv   Linux drivers from this ppa:   vvv**
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by Duncan Williams on 2011-09-03
motherboard chipset drivers:
[http://www.intel.com/p/en_US/support/highlights/server/s875wp1-e](http://www.intel.com/p/en_US/support/highlights/server/s875wp1-e)

---

### Post by sdowney717 on 2011-09-03
could be the problem, under system devices the exclamation mark is on for 

Intel(R) 82875P Processor to AGP Controller - 2579

and something about windows cant start the device.

here is a chipset driver.
[http://download.cnet.com/Intel-Chipset-Driver-7-2-2-1006-zip/3000-2122_4-162211.html#rateit](http://download.cnet.com/Intel-Chipset-Driver-7-2-2-1006-zip/3000-2122_4-162211.html#rateit)

So do you think that is the problem?

---

### Post by mips on 2011-09-03
> **sdowney717 said:**
> could be the problem, under system devices the exclamation mark is on for 

Intel(R) 82875P Processor to AGP Controller - 2579


Why won't you install the chipset driver from the Intel site? Do you like struggling? It's worth a shot.
[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=5997&ProdId=960&lang=eng&OSVersion=Windows%20XP%20Professional*&DownloadType=Drivers](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=5997&ProdId=960&lang=eng&OSVersion=Windows%20XP%20Professional*&DownloadType=Drivers)

---

### Post by sdowney717 on 2011-09-03
ok, thanks for the link, I got it and will try it out Sunday. 

The only reason I have XP on there is for watching TV. I have a vbox cats eye 3560 USB which linux driver has not been written.

[http://www.vboxcomm.com/product3.htm](http://www.vboxcomm.com/product3.htm)

it works well with a free ware program called watchhdtv.
[http://watchhdtv.net/default.aspx](http://watchhdtv.net/default.aspx)

so it would be nice to have decent video to watch tv.

---

### Post by sdowney717 on 2011-09-04
ye-haw! It installed fine after installing those intel chipset drivers.

---

