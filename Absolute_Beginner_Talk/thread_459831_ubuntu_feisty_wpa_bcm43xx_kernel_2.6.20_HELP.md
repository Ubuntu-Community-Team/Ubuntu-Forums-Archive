---
title: "ubuntu feisty wpa bcm43xx kernel 2.6.20 HELP"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by oscar44 on 2007-05-31
Im using ubuntu feisty.
I have a bcm4318 wifi card.
I can not seem to get it to use wpa.
ive followed several documents, and now im lost.
Can anyone help? 
Below are the instructions i followed:

[http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)

wpa_passphrase your_ssid your_psk

sudo gedit /etc/wpa_supplicant.conf

ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
       ssid="your_ssid"
       scan_ssid=1
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=your_psk
}

luca@laptop1:~$ wpa_passphrase mywlan thisisthepassword
network={
        ssid="mywlan"
        #psk="thisisthepassword"
        psk=b22ec921c254c73f99b31b76ff876692ecde36839a1f2d92150829e6afcb5515
}

sudo gedit /etc/network/interfaces

pre-up wpa_supplicant -Bw -Dwext -ieth0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

iface eth0 inet static
address 192.168.1.15
netmask 255.255.255.0
wireless-essid my_essid
gateway 192.168.1.1
pre-up wpa_supplicant -Bw -Dwext -ieth0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

sudo wpa_supplicant -Bw -Dwext -i eth0 -c/etc/wpa_supplicant.conf
_________________

Thanks

---

### Post by oscar44 on 2007-05-31
anyone?

---

### Post by oscar44 on 2007-06-01
cinvoke@debugg:~$ sudo lspci
Password:
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:05.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
01:06.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
01:09.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
cinvoke@debugg:~$

---

### Post by oscar44 on 2007-06-01
cinvoke@debugg:~$ dmesg | grep eth1
[  406.895097] eth1: ethernet device 00:14:a5:47:2d:66 using NDIS driver: bcmwl5, version: 0x3644000, NDIS version: 0x501, vendor: '', 14E4:4318.5.conf
[  406.895132] eth1: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  437.747115] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  621.375775] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  865.687976] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  925.007566] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  967.422406] ADDRCONF(NETDEV_UP): eth1: link is not ready
cinvoke@debugg:~$ dmesg | grep eth0
[  385.393500] eth0: Broadcom 4400 10/100BaseT Ethernet 00:03:25:2b:e5:fe
[  437.747113] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  480.007608] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  865.702526] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  893.066093] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  894.073845] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  951.889420] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  967.546933] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  971.544982] b44: eth0: Link is up at 100 Mbps, full duplex.
[  971.544987] b44: eth0: Flow control is off for TX and off for RX.
[  971.545043] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  978.566481] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  981.563493] b44: eth0: Link is up at 100 Mbps, full duplex.
[  981.563498] b44: eth0: Flow control is off for TX and off for RX.
[  981.564009] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  999.116744] eth0: no IPv6 routers present
cinvoke@debugg:~$

---

### Post by vigleik on 2007-06-01
It really shouldn't be this hard. If your wireless card is working you should be able to just choose the wirless network through some network manager (I use knetworkmanager since I prefer kde, I'm not sure what the gnome equivalent is) and you should prompted for the password.

I also have a bcm4318, and I could never get encryption to work before feisty. Now it works out of the box. I use fwcutter, not ndiswrapper. If you use ndiswrapper that might be the problem.

---

### Post by MrObvious on 2007-06-01
I've got WPA running using a BCM4318 and the Gnome Network Manager stuff. I don't even use fwcutter I just modprobe bcm43xx on the commandline (might need sudo). If you need me to post a few pages of settings please remind me to do so via PM and I'll look this thread up and post it. I want other people to be able to benefit from my setup.

---

### Post by oscar44 on 2007-06-01
> **vigleik said:**
> It really shouldn't be this hard. If your wireless card is working you should be able to just choose the wirless network through some network manager (I use knetworkmanager since I prefer kde, I'm not sure what the gnome equivalent is) and you should prompted for the password.

I also have a bcm4318, and I could never get encryption to work before feisty. Now it works out of the box. I use fwcutter, not ndiswrapper. If you use ndiswrapper that might be the problem.

I installed fwcutter, which downloaded bcm43xx driver and extracted the firmware auto :)
then i removed network-manager and installed wicd
with wicd i was able to get onto wifi and wired.

Thanks for the help guys :D

---

