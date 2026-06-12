---
title: "MBP Penryn, no wireless"
date: 2008-09-21
forum: Apple Hardware Users
---

### Post by JairunCaloth on 2008-09-21
I followed the directions on the wiki page, but for whatever reason I can't use my wireless adapter.

$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

$ ndiswrapper -l

bcmwl5 : driver installed
	device (14E4:4328) present

dmesg | grep ndis

[  230.193156] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  230.207241] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[  230.208556] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[  230.213247] ndiswrapper (NdisWriteErrorLogEntry:191): log: C000138D, count: 1, return_address: ffffffff88c205de
[  230.213251] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x10b
[  230.213260] ndiswrapper (mp_init:216): couldn't initialize device: C0000001
[  230.213264] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[  230.213272] ndiswrapper (mp_halt:259): device ffff810069696700 is not initialized - not halting
[  230.213273] ndiswrapper: device eth%d removed
[  230.213493] ndiswrapper: probe of 0000:0b:00.0 failed with error -22
[  230.216850] usbcore: registered new interface driver ndiswrapper

$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0

---

### Post by cyberdork33 on 2008-09-21
That windows driver seems to not be working... It will not initialize the hardware. Where did you get it?

You can alternatively try the wl driver:
[http://ubuntuforums.org/showthread.php?t=914697](http://ubuntuforums.org/showthread.php?t=914697)

---

### Post by JairunCaloth on 2008-09-22
I got the driver out of one of the threads here, I can't seem to find/remember the specific one now (I've looked at a lot of these today lol). After that I tried the wl driver, which appeared to work, however I lost my touchpad again in the kernel upgrade.

Although I would very much like to make linux the primary OS on this, it's not exactly critical. I can just continue to use OS X at work until I get ubuntu ready to replace it. So I decided to start testing Ibex. 

So far it's been pretty decent, and I'm looking forward to the full release. I haven't attempted to get wireless up and running yet, and the touchpad seems to be behaving well out of the box. I'm about to try to tweak the touchpad for some multi tap stuff and see about getting wireless up.

---

### Post by cyberdork33 on 2008-09-22
> **JairunCaloth said:**
> Although I would very much like to make linux the primary OS on this, it's not exactly critical. I can just continue to use OS X at work until I get ubuntu ready to replace it. So I decided to start testing Ibex. 

So far it's been pretty decent, and I'm looking forward to the full release. I haven't attempted to get wireless up and running yet, and the touchpad seems to be behaving well out of the box. I'm about to try to tweak the touchpad for some multi tap stuff and see about getting wireless up.A lot of improvements have been incorporated into Intrepid for your machine. It should be well-supported.
I would stick with the wl driver there too. There is information about using it in Intrepid in the same thread I linked to.

---

