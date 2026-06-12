---
title: "ok need some help with my wireless"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by vdub03 on 2007-05-12
i have a hp dv6140us. all i know is its a broadcom 802.11g. when i hook up to a hardline i can get internet but when i go wireless i get nothing. when i'm using vista no problems. i found a post that kinda helped me. it got my wireless light working but still no connection. after following more of that post i ended up deleting my wireless icon in my connections box. lets keep in mind this is my first go with ubuntu so i really know nothing about it. what i need is a way to get my icon back and my wireless working. please help

---

### Post by skwishybug on 2007-05-12
can you post the results of: 

```
lspci
```

Specifically the result with the entry that has Broadcomm in it.

Chances are there is a how-to already created, but knowing the type of card will help.

---

### Post by vdub03 on 2007-05-12
how do i do that. as i said i'm very new to all this

---

### Post by skwishybug on 2007-05-13
Sorry, in the Terminal:

Applications --> Accessories -->Terminal

at the prompt type in **lspci**

You should get a result similar to: 
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
**06:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)**
06:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:09.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller

You are looking for a line similar to the line in Bold.  That will tell us what type of Broadcomm card you are using. From there we should be able to get it working.

---

### Post by vdub03 on 2007-05-13
ok let me log into ubuntu and out of windows plug my lan cable in and i'll post

---

### Post by vdub03 on 2007-05-13
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
randy@Ubuntu-X64:~$ 

thats all i got nothing in bold like you said

---

### Post by bobplano on 2007-05-13
they just bolded it so you could see which line it was. btw the line is this:
Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)

---

### Post by skwishybug on 2007-05-13
I would try working through this How To. It appears by the poll that it has been fairly successful in getting that particular card working.

I can't say from my own experience as you can tell I have a different type of card.

Good luck!

[http://ubuntuforums.org/showthread.php?t=297092&highlight=1390](http://ubuntuforums.org/showthread.php?t=297092&highlight=1390)

---

### Post by vdub03 on 2007-05-13
thank you will try this now and let you know how it works. if i do get it working can i ask you for more help

---

### Post by skwishybug on 2007-05-13
By all means. But I would recommend asking in the open forum. I'm still fairly new to Linux and Ubuntu and there are many who are much more knowledgeable than I.

You will find that most people on here are very friendly and helpful. And in time you will, hopefully, have learned enough where you can give back and help another new user enjoy their Ubuntu experience.

---

### Post by FuturePast on 2007-05-13
Which icon are you talking about?
What happens when you type NetworkManager at the terminal prompt?

---

### Post by vdub03 on 2007-05-13
i went to the page u sent me to have no idea of what i'm doing really, but when i get the the second step i get to the end and nothing installs. really confussed

---

### Post by vdub03 on 2007-05-13
> **FuturePast said:**
> Which icon are you talking about?
What happens when you type NetworkManager at the terminal prompt? this is what happens what does it mean. randy@Ubuntu-X64:~$ NetworkManager
You must be root to run NetworkManager!
randy@Ubuntu-X64:~$ 
can i ask if i have a hp laptop how do i have dell products in it

---

### Post by FuturePast on 2007-05-13
Oops. Try
$ sudo NetworkManager

---

### Post by vdub03 on 2007-05-13
ok got this so now what
randy@Ubuntu-X64:~$ $ sudo NetworkManager
bash: $: command not found
randy@Ubuntu-X64:~$ sudo NetworkManager
Password:
randy@Ubuntu-X64:~$

---

### Post by zxczxc1 on 2007-05-13
What happened: sudo asked for your password, and you pressed enter, so NetworkManager was not started.

What can you do: enter your password when asked for it (when the word "Password:" appears), and press enter.

Explanation: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by zxczxc1 on 2007-05-13
just in case you actually did enter the password:

sudo /etc/dbus-1/event.d/25NetworkManager restart
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher restart
this will (as far as I understand from below link) make the icon appear again.

taken from [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/43379](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/43379) regarding "nm-applet vanished from tray".

---

### Post by vdub03 on 2007-05-13
ok now what can i do to get my wireless working

---

### Post by zxczxc1 on 2007-05-13
> **vdub03 said:**
> ok now what can i do to get my wireless working

does ok mean that you managed to get the NetworkManager icon back as per #17?

---

### Post by vdub03 on 2007-05-13
yes but i still cannot get my wireless working, and my beryl goes white when i launch it any ideas whats up with that. better yet anywhere i can go to read all about codeing and stuff i'm very new to this at the age of 33 and uhmmm i'm below beginner. but i still need help getting my wireless to connect. my wireless light comes on but no connection, and when i try and run beryl it goes to a white screen and i have to restart to get out of it

---

### Post by skwishybug on 2007-05-13
Since you are new, and we are still having some problems getting the wireless working, I would suggest holding off on Beryl for a little while. I waited almost 5 months to install it on my computer and really, I don't find it all that great anyway.

you said you got to the end of step 2 and nothing installed. What part didn't install? Just a note, the code blocks are to be copied and pasted line by line, not as a chunk.

---

