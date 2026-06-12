---
title: "Wireless option has disappeared from my Network Settings"
date: 2007-10-24
forum: Apple Intel Users
---

### Post by Room 34 on 2007-10-24
I'm running Gutsy on a MacBook Core Duo (late 2006 model).

When I first installed Gutsy last week, and up until last night, my wireless was working perfectly. Last night I used Synaptic Package Manager to install all of the packages pertaining to Ubuntu Studio, which went successfully. (This may be irrelevant, but it's what I was doing immediately before the problem appeared.)

Then, strangely, after another reboot, my wireless networking wasn't working. I went into Network Settings, and discovered to my surprise that wireless is not even showing up as an option there anymore!

I rebooted into Mac OS X and it automatically connected to my wireless network perfectly, so it's not a problem with the wireless card itself.  I've tried a few things I've seen online and in the built-in help system, but nothing really seems to address the issue I'm having.  I'm wondering if something in one of the Ubuntu Studio packages uninstalled (or severely misconfigured) something I need for wireless.

Here's what seems to be the pertinent problem, but I have only found minimal and unhelpful mentions of this online.  When I run ```
lshw -C network
``` I see this:

```

  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0

```

When I look for help on that "network UNCLAIMED" portion, in [this document](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) all I see is that adding info on it is a "to-do" item. Does anyone know any more about this problem?

---

### Post by Room 34 on 2007-10-24
I found a solution (or at least a workaround) to the problem, although I have no explanation for it.

I rebooted and instead of selecting the default, **2.6.22-14-rt**, I chose **2.6.22-14-generic**. I'm still a n00b so I'm not even sure what the difference is between the two, but at any rate, when I booted up with generic, the wireless interface was showing up in Network Settings again, and it appears to be working properly. (I'm not at home so I can't actually test my network.)

---

### Post by cyberdork33 on 2007-10-24
> **Room 34 said:**
> I found a solution (or at least a workaround) to the problem, although I have no explanation for it.

I rebooted and instead of selecting the default, **2.6.22-14-rt**, I chose **2.6.22-14-generic**. I'm still a n00b so I'm not even sure what the difference is between the two, but at any rate, when I booted up with generic, the wireless interface was showing up in Network Settings again, and it appears to be working properly. (I'm not at home so I can't actually test my network.)

The rt kernel is the modified kernel that comes with ubuntu studio. Did you compile Madwifi drivers before? you  have to do that again for each kernel update. (when running the kernel that doesn't work)

---

### Post by Room 34 on 2007-10-30
No, I didn't do anything with Madwifi (or ANYTHING) when I first installed Ubuntu -- my wireless just WORKED right away.

I've modified the GRUB config so the generic kernel is the default, so for now that works (besides, I'm too distracted by Leopard to spend much time in Ubuntu right now).

I'm considering dumping Ubuntu Studio and just going back to a clean install, then just picking the specific apps I'm interested in from Studio to install individually.

---

### Post by cyberdork33 on 2007-10-30
> **Room 34 said:**
> No, I didn't do anything with Madwifi (or ANYTHING) when I first installed Ubuntu -- my wireless just WORKED right away.

I've modified the GRUB config so the generic kernel is the default, so for now that works (besides, I'm too distracted by Leopard to spend much time in Ubuntu right now).

I'm considering dumping Ubuntu Studio and just going back to a clean install, then just picking the specific apps I'm interested in from Studio to install individually.Many people are having trouble with the rt kernel anyway. I think you will be ok if you use the default Ubuntu kernel.

---

### Post by wip on 2007-12-13
hi,

i need the rt kernel for doing low latency audio... but the kernel is not compiled with wireless. i tried to recompile madwifi and got a message saying that the kernel is missing wireless.

who's in charge of the compilation of this kernel for gutsy? i compile my kernel for so many years that i would rather not do it again.

how can i ask this option to be enable in rt kernel?
pat

---

### Post by cyberdork33 on 2007-12-13
try to contact the dev in the wishlist, or the mailing lists, or even IRC:
[https://wiki.ubuntu.com/UbuntuStudio](https://wiki.ubuntu.com/UbuntuStudio)

and it looks like the realtime kernel is made by the normal Ubuntu devs anyway, 
[https://wiki.ubuntu.com/RealTime/Gutsy](https://wiki.ubuntu.com/RealTime/Gutsy)

so you should be able to file a bug in launchpad
[https://launchpad.net/ubuntu/gutsy](https://launchpad.net/ubuntu/gutsy)

---

### Post by Sirex on 2007-12-25
Hello,
   I had the identical problem. I have an IBM Thinkpad Lenovo T60 with the Intel 3945 wireless chip in it. I installed Feisty (7.10) and everything worked great out of the box. Then I used Synaptic to install Ubuntu Studio and suddenly my network devices were no longer working. The devices are listed by lshw. They show the correct drivers being loaded and they are on the PCI bus but the configuration is "network UNCLAIMED". The GUI device manager does not show the network devices at all. Nothing I have tried gets ETH0 or WLAN0 to show up. All of the proper drivers seem to be loaded. 

Unfortunately when I tried booting the generic kernel it just freezes. 

Any help would be greatly appreciated. I would rather not have to reinstall.

Thanks

---

### Post by boboyo on 2007-12-28
same thing happened to me today.

i rly dont know how to fix this so plz someone help me

---

### Post by alpinesatan on 2007-12-29
i too am trying to get airport working :(
It has never worked with ubuntu.
Ive tried getting it to work for hours and hours but with no luck.
Ill keep trying and ill post my findings if it works out.
:guitar:

---

### Post by changuito on 2007-12-30
FWIW, I lost my wireless on my macbook pro as above, but I was still only using the generic kernel.
wifi worked fine ever since i installed madwifi as per [https://wiki.ubuntu.com/MacBookPro]("https://wiki.ubuntu.com/MacBookPro").

I had the same result as above for 

```
lshw -C network
```

but i was using the generic kernel 

```
$ uname -a
Linux divide 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux

```

But I simply reinstalled madwifi following the same instructions as the first time (above) and now it works again! Seems easy enugh, just hope this dosent become a habit. (and thank god for a usb wireless card for when madwifi is not working.)

peace

---

### Post by cyberdork33 on 2008-01-02
note that anytime there is a kernel update/upgrade, you may have to to recompile any previously compiled modules that link against the kernel, such as madwifi, ATI drivers, etc that are not from the repos.

---

