---
title: "Laptop takes a while to connect to network upon boot."
date: 2012-12-29
forum: Any Other OS
---

### Post by Buruk on 2012-12-29
I have linux mint 14 cinnamon. It waits the 60 seconds for a network connection upon boot, then boots without it. It takes about another 3 minutes for the network to connect, what could cause this lag? It's an internal network card being used.

---

### Post by chadk5utc on 2012-12-29
can you post the specs of your laptop, as it could be helpful.

---

### Post by Buruk on 2012-12-29
The laptop is a dell inspiron 1545.

You  should be able to see the network card here, though I'm not entirely sure where though I think it's the one by Broadcom, highlighted.

```
paula@paula-Inspiron-1545 ~ $ lspci -tv
-[0000:00]-+-00.0  Intel Corporation Mobile 4 Series Chipset Memory Controller Hub
           +-02.0  Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller
           +-02.1  Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller
           +-1a.0  Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4
           +-1a.1  Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5
           +-1a.2  Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6
           +-1a.7  Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2
           +-1b.0  Intel Corporation 82801I (ICH9 Family) HD Audio Controller
           +-1c.0-[0b]--
           [COLOR=yellow][COLOR=orange]+-1c.1-[0c]----00.0  Broadcom Corporation BCM4312 802.11b/g LP-PHY[/COLOR][/COLOR]
           +-1c.2-[09]----00.0  Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller
           +-1c.4-[0d-0e]--
           +-1d.0  Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3
           +-1d.7  Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1
           +-1e.0-[03]--
           +-1f.0  Intel Corporation ICH9M LPC Interface Controller
           +-1f.2  Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode]
           \-1f.3  Intel Corporation 82801I (ICH9 Family) SMBus Controller
```

---

### Post by chadk5utc on 2012-12-29
ok that lists a wireless device are you using that or wired connection?

---

### Post by Buruk on 2012-12-29
I'm using the wireless connection.

---

### Post by chadk5utc on 2012-12-30
Have a look here and see if this helps with this card
[http://askubuntu.com/questions/125529/wireless-doesnt-work-on-a-broadcom-bcm4312](http://askubuntu.com/questions/125529/wireless-doesnt-work-on-a-broadcom-bcm4312)

---

### Post by Buruk on 2012-12-30
I don't think the command worked. Look at the highlighted warning.

```
paula@paula-Inspiron-1545 ~ $ sudo apt-get remove --purge bcmwl-kernel-source
[sudo] password for paula: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 6 not upgraded.
After this operation, 3,609 kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 167493 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-17-generic
[COLOR=orange]Warning: No support for locale: en_US.utf8[/COLOR]
```

---

### Post by mamamia88 on 2012-12-30
> **Buruk said:**
> I don't think the command worked. Look at the highlighted warning.

```
paula@paula-Inspiron-1545 ~ $ sudo apt-get remove --purge bcmwl-kernel-source
[sudo] password for paula: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 6 not upgraded.
After this operation, 3,609 kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 167493 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-17-generic
[COLOR=orange]Warning: No support for locale: en_US.utf8[/COLOR]
```

don't see what a locale error would have to do with your network connecting.

---

### Post by xenopeek on 2012-12-31
You can indeed ignore the locale warning, that's a known issue with update-initramfs but doesn't actually do any harm. If you want to fix that warning (though there is no need to ) see here: [http://forums.linuxmint.com/viewtopic.php?f=42&t=111527](http://forums.linuxmint.com/viewtopic.php?f=42&t=111527)

As for having a BCM4312, if you still have a working Internet connection then follow the steps here (you need the LP-PHY): [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#A11.10_.28Oneiric_Ocelot.29_-_12.10_.28Quantal_Quetzal.29-1](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#A11.10_.28Oneiric_Ocelot.29_-_12.10_.28Quantal_Quetzal.29-1)

If you now don't have a working Internet connection, follow instead the steps further down on that page: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access)

Edit: if you didn't know, Linux Mint 14 is based on Ubuntu 12.10. So follow the steps for Ubuntu 12.10.

---

