---
title: "Game problems"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by natehatewindows on 2007-11-26
I am trying to get some games to work. I have installed 2 of them via apt-get, pong2 and pinball. The pong2 game when i onpen it just flashes a lot and looks really bad, the pinball game is just a black window. on the pinball game i have to use force quit to close the window. I am prety sure my graphics card is ok, i use compiz with no problems. just in case here is my lspci. Any help figuring this problem out would be great....it seems like it is with my 3d or soemthing.

home@home-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0a:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
0a:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

---

### Post by KhaaL on 2007-11-26
try running them without compiz and see if its more successful. i don't know about these games, but compiz has sometimes trouble rendering java apps and it might extend to other type of apps too...

---

### Post by natehatewindows on 2007-11-26
well that worked for the pong game...thanks!

---

### Post by natehatewindows on 2007-11-26
ok it actually worked for both!!
 :)

---

### Post by natehatewindows on 2007-11-27
ok so i amam still having preoblems with games. the pinball game will only launch one out of maybe 10 times. I downloaded scorched 3D, it runs fine until i actually do anything in the game (zoom in, out, anything) it freezes my whole computer and i have to turn the power off. I know my system specs should be well able to rund these games. my lapci is above, i have 2GB of RAM. i also downloaded SMC and i got a straner error when i launched it (it never actually launched) and after a restart it deos not do anything when i try to launch it from the terminal or menu....i have tried to reinstall it a few times.

thanks for your help...are linux games just very buggy?

---

### Post by natehatewindows on 2007-11-27
i have also installed the following:

pingus: does the same as the pinball, just a black window i must force quit.
Ibreakout2:same as pinball and pingus.
pacman: works fine.
scorched3D:still not working right
Secret Maryo Chronicals: wont lauch at all.

i would really like to know whats going on. I have never had any problems with programs before these games. Please help me to figure this problem out.....thanks in advance!

---

