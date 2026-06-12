---
title: "i got serious problems wit gusty i need help!!!"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by nnamdi on 2007-11-09
pls can anyone help in resolvin this problem of audio on my laptop

hp pavilion dv6536en series
got alot of problems on it

1.Audio
2.webcam
3.Desktop effect (i.e cannot use Normal or Extra visiual effect)

i will be glad if anyone replies me thanks

---

### Post by Sef on 2007-11-09
What are system specs?

---

### Post by nnamdi on 2007-11-09
it is dv6500 series

160gd hdd
1gb ram
wifi/bluetooth
webcam
intel centrino 
formerly had vista but revomed it and put win xp
and dual bootin gustybon it

---

### Post by anaconda on 2007-11-09
I think what "sef" meant was what hardware do you have?

eg. the output if you write these commands (in terminal)
lsusb
lspci
(you can get even more info with "sudo lsusb -v" and "sudo lspci -v" but they may be a bit long to post here..)  

also 
lshw and dmesg
can give (too much) more info... But the relevant parts can be worth posting here.

---

### Post by nnamdi on 2007-11-09
ok thanks
pradeep@pradeep:/$ lsusb
Bus 006 Device 001: ID 0000:0000  
Bus 007 Device 002: ID 04f2:b015 Chicony Electronics Co., Ltd 
Bus 007 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


pradeep@pradeep:/$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

---

### Post by anaconda on 2007-11-09
Here is how someone got the same soudcard working..
[http://ubuntuforums.org/showthread.php?t=605990&highlight=82801H](http://ubuntuforums.org/showthread.php?t=605990&highlight=82801H)

---

### Post by nnamdi on 2007-11-09
anaconda thanks alot i tried it out and it worked i i followed the procedure from this link
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
and it. but i download the 1.5 version

am still yet to install my webcam and desktop effects

---

### Post by sailor2001 on 2007-11-09
In synaptics. (system/admin./synaptic) check your compiz-fussion.  You can launch through alt/f2....eg. for menu alt/f2/ccsm  and for start compiz alt/f2/compiz --replace   to get back to metacity alt/f2/metacity --replace....... other ways of course

---

### Post by bcrom on 2007-11-09
Try running the webcam wizard in Ekiga Softphone.  That worked for me in Gutsy.

---

### Post by nnamdi on 2007-11-09
i installed kopete and it saw my webcam but i couldn't invite a viewer to see it. it said jasper is required to render the yahoo webcam images i do i fix that 



and as for the compiz that did not work

---

### Post by AndrewGene on 2007-11-15
> **nnamdi said:**
> 
and as for the compiz that did not work


Are your windows moving slowly without compiz (while in metacity)???? I have an intel integrated graphics card as well.  Gusty, unlike Feisty, installed xgl-server.  Xgl-server slowed my system way down and on the integrated graphics i didn't need it.  You might try opening synaptic and search for xgl-server and removing it.  Worst comes to worst, and that didn't solve your problem, you can always reinstall it by typing sudo apt-get install xgl-server into the terminal and all is back to normal.

---

### Post by Ekeluo on 2007-11-16
Post the output of this command:

fpreg | glxinfo  

Also what VGA driver are you using? [System>Administration>Screens and Graphics]

---

### Post by Martje_001 on 2007-11-16
> **nnamdi said:**
> i installed kopete and it saw my webcam but i couldn't invite a viewer to see it. it said jasper is required to render the yahoo webcam images i do i fix that 



and as for the compiz that did not work
Go to System --> Administration --> Synaptic and search for 'Jasper'. Select everything and install it.

---

