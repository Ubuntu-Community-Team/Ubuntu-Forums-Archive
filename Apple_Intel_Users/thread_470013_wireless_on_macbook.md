---
title: "wireless on macbook"
date: 2007-06-10
forum: Apple Intel Users
---

### Post by XrRydr on 2007-06-10
I've got the newest white macbook and using the page here: [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
I was able to set up a dual boot between Mac OS X and 7.04 Ubuntu.  I was able to install it with no major problems or anything.  The problem is I can't get the wireless to work.  I've tried entering the commands on the macbook documentation page, but they didn't seem to work, I went to the madwifi how to page and that doesn't work either.  Copied from the Apple website: "Built-in AirPort Extreme Wi-Fi (based on IEEE 802.11n draft specification)"  Do you think there was some sort of wireless update with the newest macbooks that makes it harder to get to work?  I going through the documentation, I think I was able to "make" and "install" the driver, when I did it in the terminal it looked succesful enough, the next step in the madwifi page was to load it with this command "modprobe ath_pci".  I would try that one and get this response: "WARNING: Could not open '/lib/modules/2.6.20-15-generic/madwifi/wlan.ko;: No such file or directory
FATAL: Could not open '/lib/modules/2.6.20-15-generic/madwifi/ath_pci.ko;: No such file or directory

Is there anything I can do?  Thanks.

---

### Post by zAo on 2007-06-10
No wireless for me too (iMac C2D)

What does `lspci` say in the linux terminal?

---

### Post by XrRydr on 2007-06-10
bob@bob-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:07.0 Performance counters: Intel Corporation Unknown device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
02:00.0 Network controller: Atheros Communications, Inc. Unknown device 0024 (rev 01)
03:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

---

### Post by ivesjd on 2007-06-10
do this
```
 sudo update-pciids
```
and then this
```
lspci
```
that will tell you what the wireless chipset is, as of now its just saying unknown. There are multiple tutorials on how to get madwifi working. But that is what you need, is the madwifi drivers.

---

### Post by XrRydr on 2007-06-12
I got it working, I tried the instructions here again, and it worked this time, the difference was that I had it connected to a wired internet cable while doing it.

---

### Post by kzm. on 2007-06-14
dont forget that with every update, you might loose your wireless again. so i keep the archive on the disk with the instructions. it confused me a lot (i read but forgot about it).. and it appeared to me random, when my wireless kept working, till i read it again and remembered that i had some update requests from ubuntu i clicked through without thinking. 
i hope the madwifi snapshot becomes trunk very soon.. it reminds me on my nightmares with some nvidia experimental drivers a year ago.. i updated during some day and started the next day my computer and the x-server failed. it kept on happening once in a while and took me the experience of 2-3 times spending frustrated days trying and solving all kind of unnecessary stuff, till i figured out, what caused it everytime.

---

