---
title: "broadcom wireless problems"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by oldelfy on 2008-04-16
OK, since my last post i completely gave up on wireless and wpa from command line, but i'm back! i've got the proper desktop install this time since people seemed to be saying that's easier to get wpa working with. however i'm having no luck, network manager on the taskbar is unable to find any wireless networks

iwconfig shows eth1 as the wirless connection
essid is off/any
/rts off /fragment off /access point invalid /mode managed/

lshw shows *-network:1 DISABlED
product bcm4306
driver=bcm43xx

lsmod shows the driver loaded"used by" is 0

sudo iwlist eth1 scan gives
eth1 interface doens't support canning : no such device

anyhelp?

---

### Post by wolfen69 on 2008-04-16
i doing WEP instead of WPA out of the question? it will be much easier to get going.

---

### Post by spiderbatdad on 2008-04-16
Have you got bcm43xx-fwcutter from synaptic?
This wiki offer links to specific releases...[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by stchman on 2008-04-16
> **elfy said:**
> OK, since my last post i completely gave up on wireless and wpa from command line, but i'm back! i've got the proper desktop install this time since people seemed to be saying that's easier to get wpa working with. however i'm having no luck, network manager on the taskbar is unable to find any wireless networks

iwconfig shows eth1 as the wirless connection
essid is off/any
/rts off /fragment off /access point invalid /mode managed/

lshw shows *-network:1 DISABlED
product bcm4306
driver=bcm43xx

lsmod shows the driver loaded"used by" is 0

sudo iwlist eth1 scan gives
eth1 interface doens't support canning : no such device

anyhelp?

This supposedly helps to get Broadcom 43xx cards working.

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Broadcom_wireless_driver](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Broadcom_wireless_driver)

---

### Post by oldelfy on 2008-04-16
> **wolfen69 said:**
> i doing WEP instead of WPA out of the question? it will be much easier to get going.

i can't get it to work without any encryption, let alone with wep or wpa

---

### Post by oldelfy on 2008-04-16
> **spiderbatdad said:**
> Have you got bcm43xx-fwcutter from synaptic?
This wiki offer links to specific releases...[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

i think these are meant to enhance the ability of the card though, since it's not working AT ALL despite being detected not much help

---

### Post by spiderbatdad on 2008-04-16
> **elfy said:**
> i think these are meant to enhance the ability of the card though, since it's not working AT ALL despite being detected not much help

Nope. Those guides are intended to help you enable the firmware and get the card working...not to enhance features. Maybe reading the link to your version will help you.

---

### Post by oilchangeguy on 2008-04-16
i know this will be a cop out to those hard core linux command line junkies out there. but the best way around this, is to get a pcmcia card that will work with linux. and disable the onboard card.

---

### Post by spiderbatdad on 2008-04-16
> **oilchangeguy said:**
> i know this will be a cop out to those hard core linux command line junkies out there. but the best way around this, is to get a pcmcia card that will work with linux. and disable the onboard card.

There isn't a command line called for in the tutorial...it is all done via point and click.
```
4) Double-click the bcm43xx-fwcutter-*.deb package to install with the package installer. You may receive a warning that there is the same version available from the channel, but as it's not currently accessible you will have to proceed with this file.

5) During installation it will ask you if you would like it to fetch and extract the firmware. This step will fail without an Internet connection so just click Forward and then close the the package installer.

6) Open System -> Administration -> Restricted Driver Manager and you will see that under the Firmware drop down arrow it says Firmware for Broadcom 43xx chipset family and under Status it says Not in Use.

6) Tick the box under Enabled to enable the firmware.

7) Click Enable Firmware to continue.

8) Select Use a local file and browse to the wl_apsta-3.130.20.0.o firmware file and click Open.

9) Click Ok to extract the firmware. 
```

---

### Post by oilchangeguy on 2008-04-16
> **spiderbatdad said:**
> There isn't a command line called for in the tutorial...it is all done via point and click.
```
4) Double-click the bcm43xx-fwcutter-*.deb package to install with the package installer. You may receive a warning that there is the same version available from the channel, but as it's not currently accessible you will have to proceed with this file.

5) During installation it will ask you if you would like it to fetch and extract the firmware. This step will fail without an Internet connection so just click Forward and then close the the package installer.

6) Open System -> Administration -> Restricted Driver Manager and you will see that under the Firmware drop down arrow it says Firmware for Broadcom 43xx chipset family and under Status it says Not in Use.

6) Tick the box under Enabled to enable the firmware.

7) Click Enable Firmware to continue.

8) Select Use a local file and browse to the wl_apsta-3.130.20.0.o firmware file and click Open.

9) Click Ok to extract the firmware. 
```

i think you missed the point, it does not matter if no commands are in whatever how-to. the point is to by-pass the on-board wireless.

---

### Post by oldelfy on 2008-04-17
> **oilchangeguy said:**
> i think you missed the point, it does not matter if no commands are in whatever how-to. the point is to by-pass the on-board wireless.

not a laptop

---

### Post by oldelfy on 2008-04-17
> **spiderbatdad said:**
> Nope. Those guides are intended to help you enable the firmware and get the card working...not to enhance features. Maybe reading the link to your version will help you.

ok i'll give it a try tomorrow

---

### Post by joshrobinson on 2008-04-17
> **oilchangeguy said:**
> i think you missed the point, it does not matter if no commands are in whatever how-to. the point is to by-pass the on-board wireless.

why spend money when you can get it working for free?

broadcom cards aren't as hard as some people claim they are
they catch alot of crap

---

