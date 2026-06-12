---
title: "help with Beryl and the startup file PLEASE!!!"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by whos2know on 2007-09-24
Hi, I am trying to install Beryl... I'm having a hell of a time doing it.  I have a ATI 200M and I get all the way to a point where all I get is a white screen.  I don't know what I am doing wrong and have been working on this for a few days now.  I am now not able to log in because I tried one way and it had me put some things in sessions for the start up.  Once I log in now, it goes to a white screen no matter what session I try.  Where is the startup file so I can take the line out that starts xgl or beryl which ever one is doing this and how do I fix my white screen so I can use my Beryl... Thank you!!

---

### Post by Fitzy_oz on 2007-09-24
> **whos2know said:**
> Hi, I am trying to install Beryl... I'm having a hell of a time doing it.  I have a ATI 200M and I get all the way to a point where all I get is a white screen.  I don't know what I am doing wrong and have been working on this for a few days now.  I am now not able to log in because I tried one way and it had me put some things in sessions for the start up.  Once I log in now, it goes to a white screen no matter what session I try.  Where is the startup file so I can take the line out that starts xgl or beryl which ever one is doing this and how do I fix my white screen so I can use my Beryl... Thank you!!

Howdy,
The easiest way I found to get around this is to log in and let it goto the white screen, then press ctrl-alt-f1 and login to the terminal (if all went well when you pressed the  keys mentioned you'll be at a terminal logon).

Once at the terminal type top, this will give you a list of running processes which can be navigated with the <> keys.  Simply find the number for beryl, press k and enter the process number and that should kill beryl.  Might be an idea to find the beryl manager process and kill it as well jus for good measure.  Now with those processes now dead, press ctrl-alt-f7 top get back to X windows and you should be able to see your desktop.  If you've added beryl to startup, it will be under the system -> preferences -> sessions link which will bring up a list of startup programs of which beryl-manager should be one, simply remove it and you should be good to go.

---

### Post by whos2know on 2007-09-24
Thank you very much.  I tried that but my screen starts to flash differnt colors.  Then I can't seem to go any where... I figure out a way to take the line out... I typed 

rm ~/.config/autostart/beryl-manager.desktop

well... now I can get back into my desktop... How do I fix this crazy problem and get Beryl working?  What files should I send for you to figure out why this isn't working... Thank you very much!!

---

### Post by overdrank on 2007-09-24
> **whos2know said:**
> Thank you very much.  I tried that but my screen starts to flash differnt colors.  Then I can't seem to go any where... I figure out a way to take the line out... I typed 

rm ~/.config/autostart/beryl-manager.desktop

well... now I can get back into my desktop... How do I fix this crazy problem and get Beryl working?  What files should I send for you to figure out why this isn't working... Thank you very much!!

I could be wrong but I don't think the ATI 200m will support 3d.

---

### Post by Fitzy_oz on 2007-09-24
> **whos2know said:**
> Thank you very much.  I tried that but my screen starts to flash differnt colors.  Then I can't seem to go any where... I figure out a way to take the line out... I typed 

rm ~/.config/autostart/beryl-manager.desktop

well... now I can get back into my desktop... How do I fix this crazy problem and get Beryl working?  What files should I send for you to figure out why this isn't working... Thank you very much!!

Glad to see you fixed it - 

Unfortunately I can confirm that the 200m is not supported. :(

---

### Post by whos2know on 2007-09-24
thanxs for the replys.... I just looked up my board... and it's a 200G not 200M... does that make a difference?  I really hope it does... thanx... :)

---

### Post by overdrank on 2007-09-24
> **whos2know said:**
> thanxs for the replys.... I just looked up my board... and it's a 200G not 200M... does that make a difference?  I really hope it does... thanx... :)

Hi if you check the output of the command 
```
lspci
```
it will identify for you to search the forums for help. You can post the output here and I will try and help.

---

### Post by whos2know on 2007-09-25
here it is... thank you again!!


[PHP]00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
[/PHP]

---

### Post by overdrank on 2007-09-25
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE) 
Sorry :(
Edit if you would like to start the search 
[http://ubuntuforums.org/search.php?searchid=27717125](http://ubuntuforums.org/search.php?searchid=27717125)
Its late and I will continue tomorrow.

---

### Post by whos2know on 2007-09-25
ok... thank you for your help!!!

---

