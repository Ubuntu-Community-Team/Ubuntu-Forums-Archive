---
title: "New Install need Internet help"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by wulfie69 on 2007-01-03
Just installed Ubuntu 6.06.1 detected everything okay and runs great. Problem is I've always been a die hard windows user so I have little idea of what I am doing, and since I am in windows atm, some of this will sound stupid. My problem is, Well how do I connect to the internet? My modem shows up in the device manager so I know it is there. I found one setup box that had both my enet card and my modem showing in it, with the modem disabled and enet card set as default, I tried getting it to autodetect my modem but it says it couldn't using /dev(something)/modem, so I choose a random one I think I went to /dev/ss0 or something like that and clicked enable, and it said it was enabled, it would not enable using the /dev/modem so I did not know which one to use. My modem is a PCI soft data fax modem with smartCP. My computer is a Emachine model W3118 with 512meg ram. If I do manage to get this working with you guys/gals help what do I use to dial in with? 

 One other question so I dont have to start a new topic again, My video is a NVIDIA Geforce 6100 and I seem to be unable to change screen resolutions and stuck in 800x600.

 Any ideas, preferably something that I dont have to download, as I won't ever figure out how to install it :p 

Thanks & sorry for the confusion.
Kenny

---

### Post by Efwis on 2007-01-03
for the graphics card, you will have to do a download for the drivers at least for proper usage.

for your modem,  can you post the output of the following command .

open terminal and type

```
lspci
```
This will actually help determine the type of modem you are using.
for example here is mine
```
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
[COLOR="Red"]0000:00:09.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)[/COLOR]
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

```

---

### Post by wulfie69 on 2007-01-05
Sorry it took me so long to get back. I did the command you told me, and according to it we have virtually the same modem mine was a Conexant HSF 56k HSF Modem.

---

### Post by tomkae on 2007-01-05
I also have this modem. I found the driver at linuxant.com.

If you know your kernel version, you may find an exact match.

the free download is supposed to have a max. speed of 14.4; a paid version is supposed to be faster.

---

### Post by Efwis on 2007-01-05
thats exactly it, if you want full dialup speeds you need to pay for the linuxant driver, otherwise you are stuck with the 14.4 speed version for free.

conexant used to offer linux support through linuxant, but now they want $$ for complete modem usability. There is no other way around it short of going and buying a Linux compatible modem card for your comp. US Robotics is one that I know of and I know there are others but I don't have them memorized.

here is a link for compatible modems:
[http://start.at/modem](http://start.at/modem)

---

