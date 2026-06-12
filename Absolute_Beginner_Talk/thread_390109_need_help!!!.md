---
title: "need help!!!"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by thomas.hoyland on 2007-03-21
ok
got a new laptop
i need to get the wifi working
heres my stuff

any ideas
i tried ndiswrapper aswel - no luck


thomas@thomas:~/Desktop/ipw3945-1.2.0$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8168 (rev 01)
06:07.0 CardBus bridge: Texas Instruments Unknown device 8039
06:07.1 FireWire (IEEE 1394): Texas Instruments Unknown device 803a
06:07.2 Mass storage controller: Texas Instruments Unknown device 803b
06:07.3 Class 0805: Texas Instruments Unknown device 803c

---

### Post by mikewhatever on 2007-03-21
> lspci | grep -network
18:06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
23:08:08.0 Ethernet controller: Intel Corporation Intel(R) PRO/100 VE Network Connection (rev 01)

If you have the same wireless card, you do not need ndisrapper. If it does not work out of the box, install linux restricted modules for your kernel.

---

### Post by thomas.hoyland on 2007-03-21
how do i do that?
sorry, im really new to this
is ther a terminal script i can run to get the module
and what is the module name? please

---

### Post by annda on 2007-03-21
open synaptic (system > administration > synaptic) and search for linux in name ONLY. find the number of your kernel (you can also doing by typing "uname -a" in the terminal). it's linux-image-the_number (if you have more, use the highest one).

then scroll down to linux-resticted-modules-the_number and install that.

reboot.

---

### Post by mikewhatever on 2007-03-21
I think that <sudo aptitude install linux-restricted-modules> will do the trick. Then follow the basic procedure from [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#wireless](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#wireless)
or install gnome nm
<sudo aptitude install network-manager-gnome>

---

