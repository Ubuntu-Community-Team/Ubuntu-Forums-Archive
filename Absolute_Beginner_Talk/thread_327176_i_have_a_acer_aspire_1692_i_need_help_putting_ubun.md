---
title: "i have a acer aspire 1692 i need help putting ubuntu dual boot on it plz"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by gavinvasquez on 2006-12-28
hi i have a acer aspire 1692 i need help putting ubuntu dual boot on it plz will my wireless work with this wirless card aswell
specs 
Intel Pentium M Processor 740 (Processor speed 1.73GHz, 2MB L2 cache, 533MHz FSB) 
Intel 915PM Express Chipset Integrated Intel Pro/Wireless 2200BG   
256MB DDR-RAM (Max 2GB)   
80GB HDD, Weight 2.95kg.   
DVD-Dual Double Layer Drive 
4-in-1 card reader   
56K Fax/Modem, 10/100/1000Mbps LAN   
15.4" WXGA Acer CrystalBrite TFT LCD(1280x800 pixel) 
S-Video Out   
ATI Mobility Radeon X600 64MB   
Li-Ion Battery (3.5 hrs. battery life)   
IEEE 1394 port 
Infrared port 
Integrated Bluetooth 
Acer SignalUp wireless technology support   
Microsoft Windows XP Home

---

### Post by oilchangeguy on 2006-12-28
run ubuntu from the live cd. after the desktop loads select the option to install ubuntu. follow the prompts and when you get to the part about disk partition it will explain how to either erase  the drive and load only ubuntu, or partition the drive for ubuntu and your other operating system. make sure your computer is set to boot from the cd drive.

---

### Post by Sef on 2006-12-28
> will my wireless work with this wirless card aswell

Use the Live CD to check that out.   There may be work arounds that will not work with a Live CD.

Read [Psychocat's installing]("http://www.psychocats.net/ubuntu/installing") to learn how to dual boot from the live cd.

---

### Post by gavinvasquez on 2006-12-28
tnx guys system is running great jus trying to set up the network

---

### Post by meney on 2006-12-29
I have the same laptop and wireless works fine :D
You may have some trouble with the graphics driver on first shot, everything works well after that.

---

### Post by gavinvasquez on 2006-12-29
how do i connect to the internet with the wifi

---

### Post by a36233 on 2007-02-02
To use wifi use this commands
ifconfig eth1 up -> assuming eth1 is your wireless interface
iwconfig essid "default" -> default essid of your Acess point
dhclient eth1

check 
man ifconfig 
or 
man iwconfig

for more information!

---

