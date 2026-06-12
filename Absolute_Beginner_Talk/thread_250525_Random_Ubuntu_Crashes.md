---
title: "Random Ubuntu Crashes"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by SearchingBearCub on 2006-09-04
Apologies for the long post.

I am running a dual-boot system with Windows 98SE for gaming (No NIC drivers loaded) and Ubuntu 6.06 for all other tasks.

With this configuration, windows runs fine, but Ubuntu experiences random crashes in various applications. So far, its crashed while downloading updates, in Firefox, and in XChat. The crash is a total lockup, meaning that all hard drive activity ceases, the mouse is frozen, the keyboard indicators do not respond, and a three finger salute has no effect. Nothing appears on-screen; the screen just freezes.

The crashes also occur when running Ubuntu from the LiveCD. I have run MemTest from the Ubuntu LiveCD with the default options for about 4 hours, and in that time, it completed 11 tests with no errors.

A walkthrough of my current system configurations is as follows:

- System booted with a Partition Magic CD, all partitions removed, and a primary partition comprising 50% of my HD space (about 9,538.6 MB) is created and made active.

- System is rebooted with a bootable Windows 98SE CD. Drive is formatted with FAT32 and windows is installed with no optional components.

- All applicable hardware drivers are loaded, with the only optional software being the latest version of DirectX.

- System is rebooted with the Ubuntu 6.06 LTS CD, and Ubuntu is installed to the hard drive using the other 50% of my hard drive that is not yet partitioned.

- System is again rebooted, and proceeds to load Ubuntu from the hard drive. All applicable updates are downloaded and installed.

My system specs are as follows:

- Compaq Evo N160 Notebook
- Intel Pentium III-M 1.13 Ghz
- 256 MB RAM
- 20 GB HD
- ATI Mobility Radeon w/ 8 MB VRAM


What is going on here? Thanks!

---

### Post by petri on 2006-09-04
Random crashes, Yes, been there. The fault was no good videocard drivers. Maybe the same reason for your crashes. I have an ATI Radeon 8500 AIW and the fglrx drivers in repos don't work. Search in these forums a howto for your ATI:

Type, or copy and paste 

```
lspci
```

in terminal and you'll see what the graphics chips is called.

My lspci gave:
```

petri@ubuntu:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
0000:00:05.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
0000:00:06.0 Mass storage controller: Promise Technology, Inc. PDC20265 (FastTrak100 Lite/Ultra100) (rev 02)
0000:00:0c.0 Modem: ALi Corporation SmartLink SmartPCI561 56K Modem
0000:00:0f.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:00:0f.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
0000:00:10.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8233 PCI to ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
0000:00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
0000:00:11.4 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc R200 BB [Radeon All in Wonder 8500DV]
0000:01:00.1 PCI bridge: ATI Technologies Inc R200 BC [Radeon All in Wonder 8500]
0000:02:00.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 04)
petri@ubuntu:~$
```

---

### Post by SearchingBearCub on 2006-09-04
My lspci output is as follows:

0000:00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 04)0000:00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)0000:00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 02)0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
0000:00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
0000:02:04.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
0000:02:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:02:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
0000:02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)

---

### Post by petri on 2006-09-04
Search using some of the **ATI Technologies Inc Radeon Mobility M6 LY** maybe just the M6 LY and you should find.

This seems nice but I'm not sure if it is good for your ATI: [http://ubuntuforums.org/showthread.php?t=204910](http://ubuntuforums.org/showthread.php?t=204910)

---

### Post by SearchingBearCub on 2006-09-04
Thanks for the link to the other post. I checked the ATI site in that thread, and though it listed several Mobility models, mine was not explicitly listed as supported. The software appears to be ATI's "Catalyst" drivers, and I know that neither Windows 98SE, 2K Pro, or XP Pro, all of which have lived on this laptop at one point or another, have had any success using Catalyst drivers. (i.e, the underlying chip in my graphics controller, as identified by ATI's chipset ID utility, was not listed as compatible with those drivers.)

Any other ideas? These crashes are annoying!

---

### Post by petri on 2006-09-04
It ain't the catalyst drivers what I'm linking to. Just follow the howto and you'll see you'll get your crashes away.

What does the ```
lspci
``` show and what happens if you try with ```
fglrxinfo
```

---

### Post by SearchingBearCub on 2006-09-04
My lspci output is a couple posts up this thread.

My fglrxinfo output is as follows:

bash: fglrxinfo: command not found

Edit: The thread you referred to appears to be detailing how to install ATI's Catalyst for Linux drivers, which I am 90% sure are incompatible with my graphics adapter. What part of the thread are you referring to specifically?

Bear in mind that I have very little Linux knowledge. What knowledge I do have comes from a deep understanding of MS-DOS. I can grasp the concept of most commands and files, for example, I know that the /etc/fstab file specifies how the system should mount partitions at boot time, and I know that a tar file is a compressed archive, like a zip or rar file, but I don't know the specific command or file parameter formats.

---

### Post by jiaoziren on 2006-10-29
> **SearchingBearCub said:**
> My lspci output is a couple posts up this thread.

My fglrxinfo output is as follows:

bash: fglrxinfo: command not found

Edit: The thread you referred to appears to be detailing how to install ATI's Catalyst for Linux drivers, which I am 90% sure are incompatible with my graphics adapter. What part of the thread are you referring to specifically?

Bear in mind that I have very little Linux knowledge. What knowledge I do have comes from a deep understanding of MS-DOS. I can grasp the concept of most commands and files, for example, I know that the /etc/fstab file specifies how the system should mount partitions at boot time, and I know that a tar file is a compressed archive, like a zip or rar file, but I don't know the specific command or file parameter formats.

As I've known, the crash has nothing with your ATI driver. It's your battery. unplug your battery when running ubuntu 606 and it should be stable. I have a n160 too, exactly same hardware with yours. You could also try latest 610, I've been running my n160 with battery plugged in 6.10 for days and it's quite stable, though the battery is still not recognized by kernel properly.

---

