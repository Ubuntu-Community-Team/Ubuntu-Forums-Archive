---
title: "Headaches setting up a wireless connection :("
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by Jordan9786 on 2007-08-15
hey guys, ive recently been having troubles seting up a wireless internet connection for ubuntu.

right now i am dual booting xp and ubuntu.

the problems im having is, i dont know how to use ubuntu, ive read tutorials on how to set up a connection but i just dont understand them, can anyone please help me out, i just started using ubuntu this morning:(:confused:

---

### Post by splintercellguy on 2007-08-15
What exactly is your issue with wireless networking? Could you please open Terminal (Applications -> Accessories -> Terminal) and post the output of the command lspci?

---

### Post by Jordan9786 on 2007-08-15
well right now im not on ubuntu, im using xp right now, but i do open terminal and im not sure how to use that

---

### Post by splintercellguy on 2007-08-15
Okay, in Ubuntu, go to Applications -> Accessories -> Terminal. Type lspci at the prompt and press Enter. Highlight the output and copy and paste into a new post. Then we can begin to give you the information you need :).

---

### Post by Jordan9786 on 2007-08-15
alright, sounds good, i guess i will log onto this forum using my psp, and tell you everything from there :P

---

### Post by Jordan9786 on 2007-08-15
ok i just came back from booting up ubuntu and i got this:

00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 12)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 12)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
02:0c.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

---

### Post by splintercellguy on 2007-08-15
Do you have the Windows driver for your wireless card? Follow this Ubuntu Wiki guide: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Jordan9786 on 2007-08-15
yes i do have the driver

---

### Post by splintercellguy on 2007-08-15
Follow the Ubuntu Wiki link I gave earlier then follow directions, and you should be good to go. Please ask if you have any questions.

---

### Post by Jordan9786 on 2007-08-15
how do i run/use ndiswrapper

---

