---
title: "Vaio Vgn-nr220e"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by jeanyevenes on 2008-03-09
I can't install Ubuntu in my notebook. The sreen turns black before shows the desktop. What is the best setting/configuration for the screen?

---

### Post by coolbrook on 2008-03-09
Are you installing from a CD you burned?  If so did you check the integrity of the download and the CD?  Is it the Live CD..and which version?

---

### Post by jeanyevenes on 2008-03-09
Yes, I burned the CD. I checked the integrity (7.10 version). I tried with 6.06 version too and that gave me this message:

Failed to start the X server (your graphical interface). It is likely that it is not set up correctly.

and this:

Default setting
(==) Log file: "/var/log/Xorg.O.log"
(==) Using config file: "/etc/X11/Xorg.conf"

I think it is something related to the screen... 

If it is, what is the better configuration?

---

### Post by mikeymckay on 2008-03-10
I had the same problem. Before booting from the install CD, Ubuntu gives a list of options. Change the VGA settings to a different resolution. That worked for me.

---

### Post by jeanyevenes on 2008-03-10
OMG
 I tried with one by one (5 times) and the correct is 800x600x32

Thanks everybody!! A lot!

---

### Post by jeanyevenes on 2008-03-12
Here we go again. 

I installed Ubuntu 7.10. No problem.

But the wireless doesn't work. The light is not turn on. (I'm using a cable for the moment)

I know VAIO and Ubuntu are not friends.

---

### Post by jan quark on 2008-03-12
can you please tell us what your wlan card is?

please post the results of these terminal commands to specify your wlan hardware

```
sudo lshw -C network
lspci
```

---

### Post by jeanyevenes on 2008-03-12
Here is it:

[COLOR="Red"]  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 15
       serial: 00:1a:80:25:a6:03
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 duplex=full firmware=N/A ip=199.17.66.55 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0[/COLOR]

---

### Post by dj_flx on 2008-04-30
I just got a nr220e today.

Did you ever get your wireless working?

---

### Post by jeanyevenes on 2008-04-30
I gave up. At least until i finish my classes ... so busy

---

