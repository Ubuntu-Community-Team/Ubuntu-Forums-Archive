---
title: "UK Tiscali Internet With Sagem F@st 800 ModemUK Tiscali Internet With Sagem F@st 800"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by Bueno on 2005-11-20
I've been following Davie's instructions below to try to get my modem to connect

1. System>Administration>Synaptic Packet Manager
2. Scroll down left hand menu. Click on Networking.
3. In right hand box, mark 'eagle-usb-data' and 'eagle-usb-utils' for installation.
4. Stick the Ubuntu installation CD in the drive.
5. Click Apply
6. The system should then install these two packages from the CD.
6.5 Plug in your modem.
7. Go to Applications>System Tools>Root Terminal. (Don't do what I did the first four times I tried this and go to Applications>System Tools>Terminal. You need to be in root to make it work.)
8. At the prompt type in 'eagleconfig'. This will give you a list of options for different ISPs. You'll see Tiscali at the bottom as 'UK01'
9. Type in 'UK01'
10. At the prompt, type in your ISP username
11. At the prompt, type in your ISP password
12. At the prompt about encryption, say 'no'
13. At the prompt about startup on boot, say 'no'
14. You should then get a message saying that configuration was successful.
15. Type 'startadsl'
16. Go to System>Administration>Networking
17. Double click on 'Ethernet connection eth01'
18. Tick the 'This device is configured' box'
19. Change the Connection Settings Configuration drop down from 'Static IP Address' to 'DHCP'
20. Click 'OK'
21. This takes you back to the first dialogue box. 
22. Make sure that 'Ethernet connection eth01' is highlighted and then click on 'Activate' 


I get to point 14 and get the "config successful" 

At point 15 startadsl I get the following

root@ubuntu:/home/rob# startadsl


Modem is not operational!
Check eaglestat result to know its state!

root@ubuntu:/home/rob# eaglestat
eagle-usb status display
-------------------------------------------------------------
Driver version 2.3.2 Chipset: Eagle0
Vendor ID : 0x1110 Product ID : 0x9031 Rev: 0x200b
USB Bus : 001 USB Device : 005 Dbg mask: 0x0
Ethernet Interface : none
MAC: 00:60:4c:71:47:59
Tx Rate 0 Rx Rate 0
FEC 0 Margin 0 Atten 0 dB
VID-CPE 0 VID-CO 0 HEC 0
VPI 0 VCI 0 Delin GOOD
Cells Tx 0 Cells Rx 0
Pkts Tx 0 Pkts Rx 0
OAM 0 Bad VPI 0 Bad CRC 0
Oversiz. 0

Modem waiting for driver response.
Please send DSP (eaglectrl -d)

root@ubuntu:/home/rob#

Can anyone help?

:KS 
Cheers
Bueno

---

### Post by Brunellus on 2005-11-20
that modem is a known headache to get working in Linux.  Advice:  spend twenty quid and get an ADSL modem with a real ethernet connection, rather than a USB one.  Trust me, you'll be far far happier.

---

### Post by avantgardaclue on 2005-11-21
>>>Advice: spend twenty quid and get an ADSL modem with a real ethernet connection, rather than a USB one. Trust me, you'll be far far happier.<<<

OK my PC doesn't have any ethernet ports in the back. However you can buy on ebay usb -> ethernet adaptors for next to nothing. Knowing linux's problems with usb will ubuntu be able to comunicate with the modem using one of these adaptors?

---

### Post by {anthrax} on 2005-11-21
Go to point 16 first. Enable the modem in the network settings, then try the command again.

---

