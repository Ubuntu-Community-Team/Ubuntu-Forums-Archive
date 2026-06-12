---
title: "Asus Zenbook UX302L"
date: 2013-12-04
forum: Asus Ubuntu Support (CLOSED)
---

### Post by soft0 on 2013-12-04
Dear community

I've been using Ubuntu on daily basis since 10.04 and during the last week I think that the time has come to make my first contribution. Because I'm willing to do basically anything to get my new laptop working.

```
dmidecode -s system-product-name
UX302LA
```

By reading on the [help pages]("https://help.ubuntu.com/community/AsusZenbook") I have realized that my problems seems to fit quiet well. But not exactly. 

With 
**12.04** i have no network drivers, i tried installing them manually but without luck... so i moved on to
**13.04** and **13.10** where almost everything works out of the box, except that I experience the issue described in the help pages where "X dies" (did i understand it correctly?). If i start with the parameter "nomodeset" i do get a none-black screen running. But graphics aren't really satisfying... brightness doesn't work and playing any video =< 720p gets really sluggish =(
I tried installing the 3.12 kernel manually because the help pages said that the issue exists in 3.11, but it made no difference.

I'm grateful for help in any direction

 ```
lspci
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
00:03.0 Audio device: Intel Corporation Device 0a0c (rev 09)
00:04.0 Signal processing controller: Intel Corporation Device 0a03 (rev 09)
00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 1 (rev e4)
00:1c.1 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 2 (rev e4)
00:1c.3 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 4 (rev e4)
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
00:1f.6 Signal processing controller: Intel Corporation Lynx Point-LP Thermal (rev 04)
02:00.0 Unassigned class [ff00]: Device 1aea:6601
03:00.0 Network controller: Intel Corporation Wireless 7260 (rev 6b)

```

---

### Post by varunendra on 2013-12-06
If 12.04 (actually 12.04.3 I guess) is working fine for you, you can choose to install just the driver and firmware from a newer version. Here's how -

[indent]
**1)** Make sure the necessary packages to compile a package are installed beforehand -
```
sudo apt-get install --reinstall linux-headers-generic build-essential
```

**2)** Download the latest backports package from here : [http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/](http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/)

**3)** Copy the downloaded tar.bz2 package to your Ubuntu desktop > Right-click it > Extract here

**4)** Open a terminal (Ctrl-Alt-T), and run the following commands to compile and install the latest driver (replace the name "backports-3.13-rc2-1" if your extracted directory has a different name) -
```
cd Desktop/backports-3.13-rc2-1
make defconfig-iwlwifi
make
sudo make install
```

**5)** Now you need the latest firmware pack that contains the firmware that supports your wifi card. Download the latest "linux-firmware" pack from here : [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/) (the current latest pack is "**linux-firmware_[COLOR="#FF0000"]1.117[/COLOR]_all.deb**" (26 MB download))

**6)** Install the downloaded "linux-firmware....deb" pack by double-clicking it, or by "dpkg -i <package name>" command.

**7)** Reboot and enjoy a working wifi.[/indent]

---

### Post by csipuka on 2013-12-20
Hi,

I just got the same laptop, and when I try to install 13.10, I just got a blank screen.
I have edited the kernel parameter to see more (remove quiet and replace splash to nosplash), but no success.
In the BIOS the secure boot is switched off and Launch CSM enabled.
I am stuck.
Any idea is welcome.
Thx,
Csipuka

---

### Post by varunendra on 2013-12-20
> **csipuka said:**
> I just got the same laptop, and when I try to install 13.10, I just got a blank screen.
I have edited the kernel parameter to see more (remove quiet and replace splash to nosplash), but no success.

Have you also tried "nomodeset" option yet? Try that as suggested here : [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Some other boot options to try, if "nomodeset" doesn't allow you to boot with normal GUI : [https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options](https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options)

---

### Post by csipuka on 2013-12-20
Yes, I have tried it as well.
I google a bit more, and it seems there was a kernel issue. Fixed in 3.12 as I remember.
The 13.04 loading normally.
I can see 2 options:
1. install 13.04 and the new kernel and upgrade to 13.10.
2. Add somehow the newer kernel to the 13.10 live usb
The #1 is more simple, but the #2 is more elegant, but I cannot find a good how to add a new kernel.

---

### Post by csipuka on 2013-12-26
Well, I tried again the 13.10, and the nomodeset works!
May be I misspelled last time.
There is a disadvantage, the screen goes on max brightness, and I cannot change it.
Everything works, but 2 things:
1. the video does not work after 10-30sec usage. rmmod +modprobe uvcvideo did not fix it but restrart. It works with cheese and other program but not with skype.
2. SD card reader does not work.
I tried 13.04 or newer kernels (3.11, 3.12) w/o success.
I had another strange issue. charging did not charged the battery but kept the battery level on charger.
I left on charger over night, the laptop was switched off. Same battery level on next morning.
I put back the win8, and suddenly it was charging. Tried the linux again, and charging works. Confused. 
The #1 is a deal breaker for me, so I returned.

---

### Post by bonventre on 2014-01-13
It is possible to get ubuntu 13.10 working without nomodeset - check out [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1265544](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1265544)

The key step is to install kernel 3.12 or later with the patch [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1265544/+attachment/3946655/+files/0001-i915-Ignore-eDP-clamping-to-BIOS-provided-VBT-value.patch](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1265544/+attachment/3946655/+files/0001-i915-Ignore-eDP-clamping-to-BIOS-provided-VBT-value.patch)
I am currently running with 3.13.rc8 using only the "acpi_vender=" boot option (no nomodeset) and I have no blank screen issues, the video drivers are fully functional, brightness keys works, wireless works, etc.

---

### Post by bonventre on 2014-01-19
sorry i meant "acpi_osi=", not acpi_vendor

---

### Post by bug-track on 2014-02-15
Hello UX302 users. I started new [thread]("http://ubuntuforums.org/showthread.php?t=2205704") and created [help page]("https://help.ubuntu.com/community/AsusZenbookUX302") to gather all UX302 related information in one place. Your help and contribution are welcome.

---

### Post by varunendra on 2014-02-15
Very nice and wise initiative bug-track, and I like the help page - clean, compact and informative.

Good work ! Hope it continues the way it is intended. :)

---

