---
title: "Wireless Connection Disabled with Dell Latitude D610"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by KhakiMonky on 2006-09-21
Hello another newbie trying to get wireless to work.

I've been reading through a lot past few days, can't get my wireless connection to work...

I've narrowed it down to the fact that my WiFi is disabled...pressed Fn + F2 to enable, but it doesn't work.  Also checked in bios to ensure Fn + F2 activation feature is enabled

These are the details when I use lshw in terminal...
I have downloaded and installed ndiswrapper, and ndisgtk and from wiki downloaded the windows drivers for my particular card...  I just can't enable the bloody wifi... Help!

> *-network DISABLED
                description: Wireless interface
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 3
                bus info: pci@03:03.0
                logical name: eth1
                version: 02
                serial: 00:14:a4:2a:75:3f
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx multicast=yes wireless=IEEE 802.11b/g
                resources: iomemory:dfcfe000-dfcfffff irq:10


---

### Post by jivebiscuit on 2006-10-13
I installed the ndswrapper, etc... but I have to go to standby and then bring the D610 out of standby to make the wifi functional. I have to do this everytime I go wireless...I may go back to WindowsXP,NAHHHHH!!!!

---

### Post by timmy3 on 2006-12-14
Hey there, Ive got the same issue as KhakiMonky, i'm using ubuntu 6.10. I used the live version before installing and wireless just worked, but now ive installed it, i cant get the wireless to work.

Tim

---

### Post by rlozano on 2006-12-14
wpa_supplicant should be already installed with with edgy. 

for product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller, please see the HOW-TO section as there are several post on how make this wireless device works. you should have no problem making it work since it is being detected by Ubuntu.

can you try in your terminal;

wpa_passphrase "SSID" "password"  (without the quotes) where your SSID is your wireless network ID and the password to use it. see what you get. you can post it back.

---

### Post by timmy3 on 2006-12-14
i'm using works wireless and that doesnt have any security on it. with the live version on the cd it loaded up and i could choose what essid i wanted, but now i dont have a choice.

Ive put on the w29n51 both from intel site and from windows xp that i have installed on the same laptop and the wireless is working on there.


i did the wpa_passphrase "SSID" "password" , it came back with "#reading passphrase from stdin", i waited for a while, and pressed enter, it came back with passphrase must be 8..63 characters.

Ive downloaded the broabcom drivers (airforceone) and ill have a go with that

Thanks for your help with it.

---

### Post by timmy3 on 2006-12-15
just a quick update, 
I have tried the broardcom drivers, no luck there either, i think i am just mucking it up more and more.

i have done a ispci
ubuntu has detected it as a intel pro/wireless 2915ABG Network Connection (rev 05)


timmy@beth:/media/TIMS WORK/home stuff/wireless/intel$  lspci | grep Intel*
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
03:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)
 
Tim

---

### Post by rkillcrazy on 2007-04-23
I'm in the same boat here...  Mine seemed to work in 6.10 but it's not working in 7.04.

```

rob@rob-ubuntu-lap:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
03:01.0 CardBus bridge: Adaptec (formerly DPT) Unknown device 8036 (rev 4c)
03:01.5 Class 8038: Adaptec (formerly DPT) Unknown device 8038 (rev 4c)
03:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)

```

I can't seem to get NDISGTK to work.  Perhaps I'm doing something wrong?

---

