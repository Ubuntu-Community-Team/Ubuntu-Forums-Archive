---
title: "MacBook Pro 8,1 (Broadcom BCM4331) + Ubuntu 12.04 - no wireless"
date: 2012-04-26
forum: Apple Hardware Users
---

### Post by kauboy on 2012-04-26
Hi,

I read [here]("http://wireless.kernel.org/en/users/Drivers/b43#Supported_devices") that since linux kernel 3.2-rc3+, the BCM4331 wireless card that comes with my MBP 8,1 (late 2011) is supported by the kernel. I waited for Ubuntu 12.04 and installed the 64-bit version as soon as it was available. But no, the network applet still says "device not ready (firmware missing)" for wireless. :( I know that the instructions [here]("http://homepage.uibk.ac.at/~c705283/archives/2011/09/04/linux_support_for_broadcom_4331_wireless_chip_macbook_pro_81/index.html") work but it needs to be done for every new kernel version. I am attaching some information about my wireless card and the drivers that are loaded.

```

MBP:~$ lspci -nn
03:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)

```

```

MBP:~$ lsmod | grep bcm
bcma5974 17399 0
bcma     26696 1 b43

```

```

MBP:~$ lsmod | grep b43
b43      365785 0
mac80211 506816 1 b43
cfg80211 205544 2 b43,mac80211
ssb       52752 1 b43
bcma      26696 1 b43

```

When I plug in my LAN cable, in Connection Information, the driver shows up as tg3.

```

MBP:~$ lsmod | grep tg3
tg3 152032 0

```

A couple of other things:

```

MBP:~$ dmesg | grep -i broadcom
b43-phy0: Broadcom 4331 WLAN found (core revision 29)
.....
.....
Broadcom 43xx driver loaded [ Features: PNL ]
.....
.....

```

```

MBP:~$ sudo lshw
.....
*-network DISABLED
 description: Wireless interface
 .....
 configuration: broadcast=yes driver=b43 driverversion=3.2.0-23-generic **firmware=N/A** link=no multicast=yes wireless=IEEE 802.11bg

```

I installed firmware-b43-installer and rebooted, but no use. Maybe I missed a step, like rmmod some module and modprobe something else.
**Update:** I just checked the output while installing firmware-b43-installer, turns out "Unsupported device found: PCIe [14e4:4331]", so that is a dead end as well.

Can someone please tell me how to get this working?

Thanks for your help!

---

### Post by logisic on 2012-04-27
i just got this working on my MBP8,1 by following the wireless section on this page -
[https://help.ubuntu.com/community/MacBookPro8-2/Oneiric](https://help.ubuntu.com/community/MacBookPro8-2/Oneiric). No need to for the backports and what follows below it. Simply add the repo, update, install and reboot. Good luck!

---

### Post by kauboy on 2012-04-27
Thanks logisic, I did not know that the mactel repo had its own version of the firmware-b43-installer. :)

However, I did something else and got it working. :)

On Ubuntu 12.04, the b43 driver with the newer linux kernel 3.2+ supports the BCM4331 wireless card but the firmware is missing. "device not ready (firmware missing)"

See [this]("http://www.ubuntubuzz.com/2011/10/macbook-pro-wireless-broadcom-bcm4331.html") for elaborate instructions on getting WLAN to work. **However**, the only things needed to get it working are the b43-fwcutter (available in Ubuntu repos) and the Broadcom proprietary driver tar file mentioned there.

Install b43-fwcutter and download that tar file. Then:

```

tar xf broadcom-wl-5.100.138.tar.bz2
sudo b43-fwcutter -w "/lib/firmware" broadcom-wl-5.100.138/linux/wl_apsta.o

```

This will install the missing BCM4331 firmware for the b43 driver to /lib/firmware/b43, from where it will be picked up automatically on reboot. Check the lshw output to confirm whether the firmware has been picked up.

Suspend-resume and Hibernate might still cause issues, so as mentioned on the Ubuntu Buzz site:

```

# cp /etc/pm/config.d/default /etc/pm/config.d/default.old
# echo 'SUSPEND_MODULES="b43 bcma"' >> /etc/pm/config.d/default

```

If the default file does not exist, you can create it and just put in one line:

```
SUSPEND_MODULES="b43 bcma"
```

Restart/suspend-resume as you wish! :popcorn:

---

### Post by bjordan555 on 2012-08-01
Confirming logisic's remarks, a fresh install of 12.04 on a Macbook 8,1, and then following the instructions at [https://help.ubuntu.com/community/MacBookPro8-2/Oneiric](https://help.ubuntu.com/community/MacBookPro8-2/Oneiric) works. The only remark is that the step of installing "linux-backports-modules-cw-3.2-oneiric-generic" should be updated to installing "linux-backports-modules-cw-3.3-precise-generic".  Otherwise, this works perfectly.

---

### Post by mjuhasz on 2012-08-02
You don't even need the backports module anymore. It was backported from 3.2 kernel and Precise is already on 3.2 kernel.

If you're on kernel 3.2.0-27 (current version if you kept your Ubuntu updated) then you don't need the suspend fix either since kernel 3.2.0-27 had a fix for that issue.

---

### Post by hacksmith44 on 2013-01-08
Confirmed Kauboy's solution worked for me, however I have to run "modprobe -r b43 && modprobe b43" to get the wifi working completely.

Thanks for everyone's help!

---

