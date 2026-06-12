---
title: "Macbook 2,1 Hardy Wifi"
date: 2009-04-27
forum: Apple Hardware Users
---

### Post by deaddylan123 on 2009-04-27
I just installed ubuntu Hardy and am having trouble getting the wifi set up.  I installed WICD and then installed the ath9k drivers.  When I open WICD all it says is 'No wireless networks found', when I can connect to mine in OS X.

Any ideas? thanks

---

### Post by flaggh on 2009-04-28
What's the output of
```
lspci
```
and
```
iwconfig
```

---

### Post by deaddylan123 on 2009-04-28
lspci
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
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
02:00.0 Network controller: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter (rev 01)
03:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

thanks

---

### Post by cyberdork33 on 2009-04-28
did you reboot?

---

### Post by deaddylan123 on 2009-04-28
yup

---

### Post by flaggh on 2009-04-29
I have a Macbook 2,1 running Hardy64 with the same atheros card as you.  The only drivers that have worked well for me are version 20080806 that are posted here:
[http://ubuntuforums.org/showpost.php?p=5535562&postcount=3]("http://ubuntuforums.org/showpost.php?p=5535562&postcount=3")

Hope this helps.

---

### Post by cyberdork33 on 2009-04-29
your iwconfig seems to indicate that the device is initialized and working. I don't know what the issue is.

---

### Post by WA_Garrett on 2009-04-29
I have Hardy installed on a Macbook 2,1, When I was setting up my wireless I had issues with ath9k, but I got wireless working with Madwifi. 

[https://help.ubuntu.com/community/MacBook2-1/Hardy]("https://help.ubuntu.com/community/MacBook2-1/Hardy")
I used the instructions on the page linked above under Wireless > Madwifi

---

