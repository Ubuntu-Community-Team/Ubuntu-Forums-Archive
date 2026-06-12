---
title: "no wireless network detected intel"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by dnathe4th on 2007-07-05
Alright, I feel like i've read a million threads, so I truly appologize if this has already been solved.

my newly installed Ubuntu 7.04 does not recognize my wireless network, and gives me no option to connect to a wireless network.  I can connect on windows on the same computer,
[http://ubuntuforums.org/showthread.php?t=428916&highlight=no+wireless+network+detected+intel](http://ubuntuforums.org/showthread.php?t=428916&highlight=no+wireless+network+detected+intel)

that thread I thought I was doing so well because everything came up just like hte guys were talking about, but unfortunately, the thread ended and there was no solution other than to reinstall!!!  I'm 99999% sure the install wasnt the problem and i'm not corrupted or anything, so ppplease help me connect wirelessly, as all I can do now is be hard-wired in, unless I wanna go brave Vista

thanks

---

### Post by Hobo Joe on 2007-07-05
First of all, don't go to Vista! 

Second, do you have proper drivers installed, and it's just not connecting, or you just can't find the proper drivers?

---

### Post by dnathe4th on 2007-07-05
id rather not go to vista but its all ive got working!!!
I don't know about drivers, I was trying to look into that using thsi guide:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check)

I'm not sure about hte output i got from lshw  (i know a bash command now!!!!  learning linux so fast!! lolx)
 I get this:
           *-network UNCLAIMED
                description: Network controller
                product: Intel Corporation
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@03:00.0
                version: 61
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: iomemory:f0700000-f0701fff irq:11
I think thats my wireless, since the other *network was ethernet.
Does that mean I do NOT have drivers?

---

### Post by dnathe4th on 2007-07-05
Just as another thought, why are there soooo many wireless issues?   It seems like every newb in this forums having an issue with wireless.  is that really the case?

---

### Post by stchman on 2007-07-05
> **dnathe4th said:**
> Alright, I feel like i've read a million threads, so I truly appologize if this has already been solved.

my newly installed Ubuntu 7.04 does not recognize my wireless network, and gives me no option to connect to a wireless network.  I can connect on windows on the same computer,
[http://ubuntuforums.org/showthread.php?t=428916&highlight=no+wireless+network+detected+intel](http://ubuntuforums.org/showthread.php?t=428916&highlight=no+wireless+network+detected+intel)

that thread I thought I was doing so well because everything came up just like hte guys were talking about, but unfortunately, the thread ended and there was no solution other than to reinstall!!!  I'm 99999% sure the install wasnt the problem and i'm not corrupted or anything, so ppplease help me connect wirelessly, as all I can do now is be hard-wired in, unless I wanna go brave Vista

thanks

What kind of wireless card does your PC have?  Give us an lspci output here.

---

### Post by dnathe4th on 2007-07-05
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
[B]02:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4353 (rev 14)
03:00.0 Network controller: Intel Corporation Unknown device 4229 (rev 61)[/B]
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller


"Unknown Device" doesn't sound promising

---

### Post by annda on 2007-07-05
it looks like you need [ndiswrapper]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29") for [this card under linux]("http://linux.dobeyracing.net/how_to/toshiba_p200_laptop/Linux_on_Toshiba_Satellite_P200.php")

---

### Post by dnathe4th on 2007-07-05
couple things
firstly, I downloaded the drivers, how do I know which one I'm supposed to use?
I wasn't sure, so I did the same one as in that tutorial (:-/)
so then i go to do modprobe and i get 
dnathe4th@ubuntu:~$ modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko): Operation not permitted

:-( seemed like i was getting close

---

### Post by annda on 2007-07-05
for all system configuration changes you need administrator rights - admin on linux is called root. to get root privileges, use [sudo command]("https://help.ubuntu.com/community/RootSudo") in ubuntu. so it should be:

```
sudo modprobe ndiswrapper
```

the Feisty guide is explicit about that.

p.s. and good luck!

---

### Post by dnathe4th on 2007-07-05
wooooooo
im making with post without being tethered down to an ethernet cable!!!!
THANK YOU SO MUCH
i was kinda losing hope there for a second!!!!


Now seriously, why was that so hard, seems like eveyrthing else is easy in ubuntu.  and how can i give myself root by default so it doesnt always have to double check with me and ask for a password (thats half what i want to escape from vista for!)

---

### Post by annda on 2007-07-05
congratulations!

as to root: search the forums. you can enable the root account but i don't know how - i find it too dangerous because i like to experiment with things and **all changes** root makes are systemwide. if root messes up, all other users get messed with. unless you have regular backups of all your data (personally, i'm too lazy to even set up a cron job), i suggest getting used to typing the password a couple of times a day.

---

### Post by dnathe4th on 2007-07-05
fair enough.
But what about permissions, for some reason I don't have permission to extract a rar to a certain folder.  thats off the original topic of the thread, but maybe you have some more wisdom to shed?

---

### Post by dnathe4th on 2007-07-05
oh nos small problem
i restarted and lost the wireless connection
how can I get it so it sticks every time?

---

### Post by dnathe4th on 2007-07-05
OK to make it worse, sudo modprobe ndiswrapper crashes the system, despire ndiswrapper -l showing the driver's already there.

---

### Post by annda on 2007-07-05
i guess you should post another thread about wireless settings lost after reboot - so that people with no experience with intel can help you.

please describe exactly how you get to set up wifi in the new thread: network manager applet? madwifi? gnome? kde?

---

### Post by dnathe4th on 2007-07-05
alright i posted it in a new thread
so anyone with answers, please give them here:
[http://ubuntuforums.org/showthread.php?t=493412](http://ubuntuforums.org/showthread.php?t=493412)

---

### Post by stchman on 2007-07-06
> **dnathe4th said:**
> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
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
[B]02:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4353 (rev 14)
03:00.0 Network controller: Intel Corporation Unknown device 4229 (rev 61)[/B]
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller


"Unknown Device" doesn't sound promising

Go to ebay, folks are selling the 3945 Intel there for around $25 shipped new.

---

### Post by dnathe4th on 2007-07-06
not having any issues anymore, so i wouldnt recomment doing and buying a new one, this one is definetely managable

---

