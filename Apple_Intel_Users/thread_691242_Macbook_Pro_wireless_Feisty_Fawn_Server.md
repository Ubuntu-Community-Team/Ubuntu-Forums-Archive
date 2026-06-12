---
title: "Macbook Pro wireless Feisty Fawn Server"
date: 2008-02-08
forum: Apple Intel Users
---

### Post by bluerug88 on 2008-02-08
I have a first generation Macbook Pro, core duo, not C2D. I've installed Feisty Fawn server. After not being able to configure wireless while using a WEP key, I disabled encryption on my wireless router and the Feisty Fawn installer claimed that wireless configuration had worked properly on ath0.

After installation, I rebooted, and wireless networking does not work. 
ifconfig shows only two interfaces, eth0 and lo. No sign of ath0.
iwconfig shows no wireless devices.

I need to use Feisty, I can't use Gutsy Gibbon. I don't want to "desktop" Feisty.

---

### Post by cyberdork33 on 2008-02-08
are the atheros modules loaded?
```
lsmod |grep ath
```

---

### Post by bluerug88 on 2008-02-08
lsmod |grep ath

results in no output, so it appears that the atheros modules are not loaded.
I searched the web and found these commands:

sudo modprobe ath_pci
sudo modprobe ath_rate_sample
sudo modprobe wlan
sudo modprobe ath_hal

any others I'm missing?

I assume this only loads these modules temporarily, until reboot. Which system file do I need to add to in order to have these modules load at boot time? What lines do I need to add to that file?

Thank you

---

### Post by bluerug88 on 2008-02-08
I tried those commands, and the modules did not load. I searched the disk filesystem and there are no files named "ath_*" or "ath*", I searched the install CD, and still no files.

I can't be the first person to try to install wireless networking on a first generation MBP, with Feisty Server. Is it necessary to install madwifi software? I thought wireless networking was operational from the Feisty install CD on first gen MBPs ?

---

### Post by cyberdork33 on 2008-02-08
/etc/modules

maybe not with the server install. It is, afterall, not intended to be used as a desktop distro, and you wouldn't normally have wifi on a server. There are drivers in the repos (linux-restricted-modules), or you can compile madwifi. If you want a commandline system, the server install may not be what you want as it installs several other things besides a base linux install.

---

### Post by bluerug88 on 2008-02-10
"maybe not with the server install. It is, afterall, not intended to be used as a desktop distro, and you wouldn't normally have wifi on a server."

Oh, well. Goodbye Linux.

---

### Post by cyberdork33 on 2008-02-10
> **bluerug88 said:**
> "maybe not with the server install. It is, afterall, not intended to be used as a desktop distro, and you wouldn't normally have wifi on a server."

Oh, well. Goodbye Linux.I think if you want a commandline system, you are looking in the wrong distro. Try a base install of Debian or maybe gentoo.
Sorry to see you go without giving much of a chance to anything.

---

