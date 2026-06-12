---
title: "Wireless USB Problems with Ubuntu"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by rhyswynne on 2006-11-30
I installed Ubuntu last night as a dual boot from Windows XP. Setup went okay, but I have had problems setting up my wireless card with it to work with Ubuntu. So far I have installed the ndiswrapper module.

I have installed what I believe was the driver (my dongle is a Inventel UR054 (RO1) it is a USB device - it comes with Wanadoo Broadband, however I'm no longer on Wanadoo). I have used the ndiswrapper -l command and it says that the both the driver and hardware is present, however when I go to the Network Tools, the wireless connection is shown to be not configured.

I apologise for being a newbie, however I would like some advice what I am doing wrong? 

I am at my computer pretty much all night, so I can easily obtain readouts from commands you need.

Thanks in advance

---

### Post by Neobuntu on 2006-11-30
Remember to simply Google the desired type of wireless device for instant compatibility with your Ubuntu first; if you haven't already. 

Do not fight with poor chip-set providers. Go with zero configuration; whenever you can. For under say, $20 or so. Sell your old device for the difference.

With that said, two guesses come to mind.

1. Either you simply need to enter your (in range) wireless network name (SSID)  

or

2. Ndiswrapper may be conflicting with another native auto driver that isn't cooked yet. Type in lsmod (and add "|more" to it so it will not scroll off the screen) and look for module names that might be wireless modules.

```
lsmod |more
```

If ndiswrapper just doesn't work after rebooting then you need to add it to the top of your modules list. 

```
sudo gedit /etc/modules
```
or
```
sudo kate /etc/modules
```

> 
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ndiswrapper
lp
psmouse

Just like you may have to add an offending natively auto configured modules to the blacklist text file. These are in /etc directory and require "sudo" to edit.

```
sudo gedit /etc/modprobe.d/blacklist
```

> blacklist acx
blacklist bcm43xx

...are two I have had to blacklist for two old wifi cards. "acx" because it doesn't work with "g" cards (acx111) and the "bcm43xx" for a Linksys "b" card that also only works with ndiswrapper.

Install ndis-gtk when you get it on the net somehow. It's point and click easy. Just then select "Install Windows Drivers" off the admin menu.

Also for ease of management, copy your XP drivers into a directory in your home directory that is short named, such as "wifi".

Watch out for kernel image upgrades when upgrading (or simply clean installing) as you may have to blacklist (or allow) something else (like a new named driver for you device) and/or stop using or reset ndiswrapper.

---

### Post by rhyswynne on 2006-11-30
Thanks for your help!

Quick update.

I found out I had what I believed to be the driver installed however redid the "ndiswrapper -l" and it showed "driver prsent" (without the hardware present). I managed to find the USBID of 1435:0427, which I checked in the ndiswrapper wiki, no joy.

Seems like a driver issue, which I'm unable to find :(

---

### Post by Neobuntu on 2006-12-01
You may need the device installed when you boot up.

Maybe this will help too.

```
sudo modprobe -r ndiswrapper

sudo modprobe ndiswrapper

iwlist scan
```

---

### Post by rhyswynne on 2006-12-01
Okay I tried those three commands. modprobe ones didn't return anything, however the iwlist scan returned this:-

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth2      No scan results
sit0      Interface doesn't support scanning.

```

This mean anything to anybody?

Thanks for your help! Trust me, I really do appreciate it!

---

### Post by Neobuntu on 2006-12-01
Well the modprobe ones would remove and then reinstall the ndiswrapper, which might have made sure it was installed. No messages are probably a good thing.

Now the iwlist scan is cool. Had your driver been working, it would show you the wireless networks (like your wireless router if ready) in range.

---

### Post by rhyswynne on 2006-12-03
> **Neobuntu said:**
> Well the modprobe ones would remove and then reinstall the ndiswrapper, which might have made sure it was installed. No messages are probably a good thing.

Now the iwlist scan is cool. Had your driver been working, it would show you the wireless networks (like your wireless router if ready) in range.

Ah right, so it seems to be a driver issue. Thank you.

I was sure I downloaded the right ones for my device (the USBID is 1435:0247). Is there anywhere that gives that information that links USBID's to driver downloads?

Failing that, is there anyway I can contribute to the project, to try and make my dongle compatible with future versions of Ubuntu?

Thanks once again, I really appreciate it!

---

### Post by steveandarchie on 2006-12-03
Probably not much use but I downloaded the same driver to use that dongle on Win ME and I couldn't get it to work in windows.

I tried to unlock the livebox (after some success with another type of router) but my firmware seems too new. Wanadoo want a fee for providing the unlock code (I paid £70 for the box) but won't tell me how much - I have to write to them for that.

Waffle over, I hope you get it to work. I now have an Acer 5000 series that has a built in Broadcom adapter so I'm due some hassles soon.

---

