---
title: "who knows anything about mint?"
date: 2008-01-25
forum: Apple Intel Users
---

### Post by stealthsniper96 on 2008-01-25
still cant get my wifi to work with ubuntu. does mint (3.0) include any drivers ubuntu doesnt?

---

### Post by cyberdork33 on 2008-01-25
> **stealthsniper96 said:**
> still cant get my wifi to work with ubuntu. does mint (3.0) include any drivers ubuntu doesnt?
No. 

What hardware do you have? You still never posted the output of lspci .

Broadcom cards really only have one option (on the Mac) and that is ndiswrapper.

Atheros cards should use the latest madwifi drivers, but can also use ndiswrapper (with the proper windows driver).

Also, try to stick to one thread for one problem so that we can all see what you have tried and what you haven't.

---

### Post by stealthsniper96 on 2008-01-25
> **cyberdork33 said:**
> No. 

What hardware do you have? You still never posted the output of lspci .

Broadcom cards really only have one option (on the Mac) and that is ndiswrapper.

Atheros cards should use the latest madwifi drivers, but can also use ndiswrapper (with the proper windows driver).

Also, try to stick to one thread for one problem so that we can all see what you have tried and what you haven't.

i know i should i get anoyed when other people do it. anyway, i could never get lspci to work...

---

### Post by cyberdork33 on 2008-01-25
If you have Ubuntu installed, you have this.

That is an L in lspci

---

### Post by stealthsniper96 on 2008-01-25
> **cyberdork33 said:**
> If you have Ubuntu installed, you have this.

That is an L in lspci

yea ik. ok now it works.
> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
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
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
02:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)
03:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

---

### Post by cyberdork33 on 2008-01-25
ok, you do indeed have an atheros card. I am assuming you have downloaded the latest madwifi drivers and compiled them?

make sure you that you add "ath_hal" to /etc/default/linux-restricted-modules-common so that the normal Ubuntu module is not trying to load instead.

---

### Post by tgalati4 on 2008-01-25
Try a Live CD of Linux Mint 4.  If the wifi works then you will know the answer.

Your Atheros card is the latest generation chip, so it's possible that LInux support for it is behind, but you might be able for force an older wireless g driver.

---

### Post by stealthsniper96 on 2008-01-26
> **cyberdork33 said:**
> ok, you do indeed have an atheros card. I am assuming you have downloaded the latest madwifi drivers and compiled them?

make sure you that you add "ath_hal" to /etc/default/linux-restricted-modules-common so that the normal Ubuntu module is not trying to load instead.

i found some guides for compiling drivers but they didnt help (remember im a linux noob so i dont know how to do it). how do i do it?

---

### Post by cyberdork33 on 2008-01-26
> **stealthsniper96 said:**
> i found some guides for compiling drivers but they didnt help (remember im a linux noob so i dont know how to do it). how do i do it?
well, the guide explains it just as well as I can. You just need to download the latest source from madwifi.org

Then extract it (right-click, extract here), then open a terminal and navigate to the folder where you extracted it. you have to install the build requirements (in the how to) then compile as instructed (make, sudo make install) then load the module.

The only difference you need to take from the posted instructions are that you do not have to checkout the svn source, but instead get the latest stable release from their website. 

[http://ubuntuforums.org/showpost.php?p=2731459&postcount=25](http://ubuntuforums.org/showpost.php?p=2731459&postcount=25)

Try the posted instructions, and if you have a problem with a particular part, don't be afraid to ask for help. There are some other instructions in the Macbook wiki as well:
[https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688](https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688)

---

