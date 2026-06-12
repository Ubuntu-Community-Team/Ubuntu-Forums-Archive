---
title: "New user that wants wireless!"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by ironmark on 2007-02-13
Hello Everyone!

I am new to Ubuntu world and the linux world for the most part, but not to computers. My experience with linux in general is mostly installing Red Hat to tinker around with on my home computers, which only lasted a couple of hours till I was bored.

I have installed Ubuntu on my laptop (Gateway MX6124) and I am trying desperately to get my wireless to work. I have searched through the forum and gone through the tutorials several times to get my wireless working, to no avail.

following compwiz18's tutorial and then subsequently The Ravens trouble shooting guide I still cannot get it to work.

any help would be appreciated. I will do my best to provide any needed information.

this is the hardware I am using:

Gateway MX6124 laptop (Broadcom AirForce One 54G 802.11g rev. 02)
Linksys WRT54GSV4 (firmware v1.06.1)

The laptop is currently in a location that my wireless connection worked while using Windows XP, so I expect its not a network issue.

---

### Post by nickoli_02 on 2007-02-13
OK so your wireless internet isn't working. That's a pretty broad problem :)

Is the wireless interface active at all? Where exactly are you having troubles? Do you have a driver working with the card yet? What type of security do you have on the wireless network? (linux can do WPA with some configuration with wpa_supplicant daemon, however only WEP is supported by default).

---

### Post by CCBalla10 on 2007-02-13
> **ironmark said:**
> Hello Everyone!

I am new to Ubuntu world and the linux world for the most part, but not to computers. My experience with linux in general is mostly installing Red Hat to tinker around with on my home computers, which only lasted a couple of hours till I was bored.

I have installed Ubuntu on my laptop (Gateway MX6124) and I am trying desperately to get my wireless to work. I have searched through the forum and gone through the tutorials several times to get my wireless working, to no avail.

following compwiz18's tutorial and then subsequently The Ravens trouble shooting guide I still cannot get it to work.

any help would be appreciated. I will do my best to provide any needed information.

this is the hardware I am using:

Gateway MX6124 laptop (Broadcom AirForce One 54G 802.11g rev. 02)
Linksys WRT54GSV4 (firmware v1.06.1)

The laptop is currently in a location that my wireless connection worked while using Windows XP, so I expect its not a network issue.

Have you tried searching for your card here on the forums?

---

### Post by ironmark on 2007-02-14
> **nickoli_02 said:**
> OK so your wireless internet isn't working. That's a pretty broad problem :)

Is the wireless interface active at all? Where exactly are you having troubles? Do you have a driver working with the card yet? What type of security do you have on the wireless network? (linux can do WPA with some configuration with wpa_supplicant daemon, however only WEP is supported by default).

Im not sure. I can disable / enable the wireless with Fn + F2 and the blue light turns on and off. The Network Settings window lists wlan0 as an Available connection so im assuming the driver is installed correctly. Currently I have security disabled until I resolve the situation.

When I try to activate the connection through the Network Settings panel it acts like it activates it, but when I disconnect my ethernet cable it doesnt work and I cant connect to the internet.

> Have you tried searching for your card here on the forums?

that was one of the first things I looked for. its built in wireless on this particular laptop. following the tutorials lead me to the Broadcom AirForce One 54G.

I originally thought that the card was a Broadcom AirForce One 54G. I got the PCI ID 14e4.4318 and I believe the wiki has it listed for both the Broadcom AirForce One 54G and the Broadcom 40100. Which I tried the bcm40100 drivers and still couldn't connect.

I upgraded from Ubuntu 5.10 to 6.06 and it nows lists the Broadcom AirForce One 54G when I use lspci

> 
0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express P rocessor to DRAM Controller (rev 04)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GM L Express Graphics Controller (rev 04)
0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Expre ss Graphics Controller (rev 04)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) P CI Express Port 1 (rev 04)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FR W (ICH6 Family) AC'97 Audio Controller (rev 04)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge  (rev 04)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family ) IDE Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 Fast Eth ernet Controller (rev 10)
**0000:06:04.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g]  802.11g Wireless LAN Controller (rev 02)**
0000:06:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:06:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Ho st Controller
0000:06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated Flash Media Controller
0000:06:09.4 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411 , PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller


---

### Post by ironmark on 2007-02-14
I installed WIFI RADAR and it shows my wireless connection, so that confirms that the transmitter / reciever in the laptop is working and again im assuming that the drivers are installed correctly (otherwise it wouldn't be able to read that information correct?). 

When I clicked on connect it locked up the laptop........... frozen.

---

### Post by ironmark on 2007-02-14
Not sure what I did, but its working now. Seems the WIFI Radar fixed it, somehow.....

Thanks for everyones help!

---

