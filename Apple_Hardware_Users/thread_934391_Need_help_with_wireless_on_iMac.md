---
title: "Need help with wireless on iMac"
date: 2008-09-30
forum: Apple Hardware Users
---

### Post by matdombrock on 2008-09-30
I have been trying to get my wireless internet to work in my Intel iMac 20" white. I cannot get the driver off of the leopard cd because I cant seem to extract the .inf file that is needed for ndiswrapper. So I have been using the alternative driver available from dell. The dell driver works, but I cannot connect to any encrypted networks and even more annoying, I cant download at more than about 400 Kbs without the internet freezing and requiring me to reboot in order to get it working again.(I can go into more detail if you really want).

So my questions are these:
1.) How can I get the .inf file off of the leopard cd?
else
2.) I will buy a USB wireless card.

If I do indeed need to purchase a USB wireless card which ones (that is relatively cheap) will work in Gnu/Linux, specifically Ubuntu.

---

### Post by shifty_powers on 2008-09-30
no idea on leopard cd i'm afraid but

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

will help with the second...

---

### Post by phidia on 2008-09-30
If you know the name of the inf file (I don't have an intel mac) you might be able to search for it.

Also you could open a terminal and enter lspci -nn and post or search that output.

---

### Post by waspbr on 2008-09-30
I have this little bugger and it works out of the box.
[http://www.amazon.com/D-Link-DWL-G122-Compact-Wireless-Adapter/dp/B0002DQUHC]("http://www.amazon.com/D-Link-DWL-G122-Compact-Wireless-Adapter/dp/B0002DQUHC")


giving it a (long) shot, you could try to find out which wireless card you have, do

```
lspci
```

in terminal and post the output

---

### Post by sdowney717 on 2008-09-30
I have a USB wgu-210 that works perfect with ndiswrapper-gtk.
All it needed was the inf file which was on the CD and perfection, works fine.
I actually was shocked it worked so easily.

I bought mine on ebay, here is what it looks like.

[http://shop.adc-ast.com/cgi/display.cgi?item_num=WGU-210](http://shop.adc-ast.com/cgi/display.cgi?item_num=WGU-210)

[http://support.gateway.com/s/NETWORK/7004807/7004807nv.shtml](http://support.gateway.com/s/NETWORK/7004807/7004807nv.shtml)

I also have wireless router by Gateway WGR-250 that works so much better than a WGT-624 v3
netgear. The netgear turned out to be trash, kept locking up. The gateway router I never have to reboot.

---

### Post by matdombrock on 2008-09-30
Hey thanks shifty_powers! I was just there actualy, and it didn't see the column for usb (i'm on my eee so i have a super tiny screen), but you link made me take a second look and i found it! I'll have to save that page and bring it to the store with me.

---

### Post by matdombrock on 2008-09-30
I would really prefer a wireless card that is natively supported. and that output is on it's way.

---

### Post by shifty_powers on 2008-09-30
glad to be of service.

but hopefully we can get your existing card working...

---

### Post by matdombrock on 2008-09-30
Here is that output and I really apreciate the help!

```
mat@mat-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:07.0 Performance counters: Intel Corporation Unknown device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 01)
04:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
mat@mat-desktop:~$ 
```

---

### Post by matdombrock on 2008-09-30
UPDATE ON .INF FILE:

I have searched high and low for the .inf file mentioned in [https://help.ubuntu.com/community/Intel_iMac]("https://help.ubuntu.com/community/Intel_iMac")

it is simply not on my cd.

---

### Post by shifty_powers on 2008-09-30
you are using one of the infamous bm43xx chips of which i ahve one :D

you have two choices:

[https://help.ubuntu.com/community/WifiDocs/Driver/b43](https://help.ubuntu.com/community/WifiDocs/Driver/b43)

to find out abotu and install b43-fwcutter or you could do like me and use the pre-release version of ubuntu (or kubuntu 8.10 with kde 4.1) which has greatly improved wireless support...

[[IMG]http://img142.imageshack.us/img142/4938/kde4ru6.th.png[/IMG]](http://img142.imageshack.us/my.php?image=kde4ru6.png)[[IMG]http://img142.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

my desktop in kubuntu 8.10...

---

### Post by waspbr on 2008-09-30
you seem to have the same network card as I do... ndiswrapper is needed for this as far as I know, there is a method described in the link in my signature.

I got the drivers here[http://rapidshare.com/files/79251578/driver.zip]("http://rapidshare.com/files/79251578/driver.zip")

[COLOR="Red"]Alternatively[/COLOR]

you can try to see if installing the package

```
b43-fwcutter
```

in synaptic may work

The good news is that the card is going to be natively supported in the next release (intrepid) that is due in a month

---

### Post by shifty_powers on 2008-09-30
yup, if you read the preceding post you'll see i'm already using kubuntu 8.10 and the wireless support is much better, including the bcm cards...

---

### Post by cyberdork33 on 2008-09-30
> **matdombrock said:**
> UPDATE ON .INF FILE:

I have searched high and low for the .inf file mentioned in [https://help.ubuntu.com/community/Intel_iMac](https://help.ubuntu.com/community/Intel_iMac)

it is simply not on my cd.
The file is inside a self-extracting archive (.exe file). You can follow the directions here to extract it:
[https://wiki.ubuntu.com/MacBookPro/Penryn#Installing%20the%20Broadcom%20Wireless%20Driver]("https://wiki.ubuntu.com/MacBookPro/Penryn#Installing%20the%20Broadcom%20Wireless%20Driver")

> **shifty_powers said:**
> you have two choices:

[https://help.ubuntu.com/community/WifiDocs/Driver/b43](https://help.ubuntu.com/community/WifiDocs/Driver/b43)

to find out abotu and install b43-fwcutter
That driver does not support the Mac Broadcom cards.

I would suggest the wl driver as it seems to be working well for people with these cards:
[http://ubuntuforums.org/showthread.php?t=914697](http://ubuntuforums.org/showthread.php?t=914697)

---

### Post by shifty_powers on 2008-09-30
bugger, shouldn't post whilst listening to music and not concentrating.

that is in fact the driver i'm using, and is natively included in 8.10...

---

### Post by matdombrock on 2008-10-02
Ok, looks like im going to be using use 8.10.
How exactly should i go about getting it though?

---

### Post by cyberdork33 on 2008-10-03
The beta was released today:
[http://www.ubuntu.com/testing/intrepid/beta](http://www.ubuntu.com/testing/intrepid/beta)

---

### Post by matdombrock on 2008-10-05
Ok, I don't even know if anyone is reading this any more but, 

I downloaded the 8.10 beta and my wireless driver was in the restricted drivers menu. I clicked the activate button and nothing happened. I tried restarting my computer anyway to see what would happen and it just said that it was unactivated again. It doesn't even attempt to download that driver or anything.

Should I just wait until the stable release?

Also, I heard some stuff about the 8.10 beta irreparably destroying some Intel wireless cards.

---

### Post by kosumi68 on 2008-10-05
> **matdombrock said:**
> 
Also, I heard some stuff about the 8.10 beta irreparably destroying some Intel wireless cards.

There was a problem with the e1000e driver, but the dangerous part has been fixed, both upstream and in Intrepid. You can read more about it here: [http://lkml.org/lkml/2008/10/1/368](http://lkml.org/lkml/2008/10/1/368). I am also appending an excerpt of the Intrepid change log.

-----------------------------------------------

commit 519974172e5b579203b5b053bca2cb00c4fc0fa6
Author: Tim Gardner <tim.gardner@canonical.com>
Date:   Fri Oct 3 09:46:24 2008 -0600

    UBUNTU: Add support in e1000e for a couple of ICH10 PCI IDs
    
    Signed-off-by: Tim Gardner <tim.gardner@canonical.com>

commit da65b693562fd62d3cb265d4631480a2de9ea957
Author: Tim Gardner <tim.gardner@canonical.com>
Date:   Thu Oct 2 07:48:32 2008 -0600

    UBUNTU: Ubuntu-2.6.27-5.8
    Ignore: yes
    
    Signed-off-by: Tim Gardner <tim.gardner@canonical.com>

commit 7c08c3c8e46f0c1ec24614c33cedeceddce4d07f
Author: Tim Gardner <tim.gardner@canonical.com>
Date:   Thu Oct 2 07:28:23 2008 -0600

    UBUNTU: Enabled CONFIG_E1000E, disabled CONFIG_E1000E_NEW
    
    Use the upstream driver (with the NVM protectrion patch) instead of
    the SourceForge version in ubuntu/e1000e.
    
    Signed-off-by: Tim Gardner <tim.gardner@canonical.com>

commit 08047b1ec0f796216d3f787f8349a8beca024778
Author: Bruce Allan <bruce.w.allan@intel.com>
Date:   Wed Oct 1 17:18:35 2008 -0700

    e1000e: write protect ICHx NVM to prevent malicious write/erase
    
    Set the hardware to ignore all write/erase cycles to the GbE region in
    the ICHx NVM.  This feature can be disabled by the WriteProtectNVM module
    parameter (enabled by default) only after a hardware reset, but
    the machine must be power cycled before trying to enable writes.
    
    Signed-off-by: Bruce Allan <bruce.w.allan@intel.com>
    Signed-off-by: Jesse Brandeburg <jesse.brandeburg@intel.com>
    CC: [email]arjan@linux.intel.com[/email]
    Signed-off-by: Linus Torvalds <torvalds@linux-foundation.org>

---

### Post by cyberdork33 on 2008-10-05
> **kosumi68 said:**
> There was a problem with the e1000e driver, but the dangerous part has been fixed, both upstream and in Intrepid. 
and it doesn't effect Macs...

---

