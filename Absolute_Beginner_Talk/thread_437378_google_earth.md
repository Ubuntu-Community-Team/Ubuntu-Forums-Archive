---
title: "google earth"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by heatrag on 2007-05-08
hi
I have just downloaded GoogleEarthLinux.bin and have followed instructions on their help page but only get -> desktop:~$ sh GoogleEarthLinux.bin
sh: Can't open GoogleEarthLinux.bin

not the end of the world but it would be nice to get it working, thanks.

---

### Post by taurus on 2007-05-08
```
cd ~/Desktop
chmod 755 GoogleEarthLinux.bin
./GoogleEarthLinux.bin
```

---

### Post by earobinson on 2007-05-08
> **taurus said:**
> ```
cd ~/Desktop
chmod 755 GoogleEarthLinux.bin
./GoogleEarthLinux.bin
```
That should do it.

---

### Post by t3roriz3r on 2007-05-08
[http://ubuntuforums.org/showthread.php?t=195382&highlight=google+earth]("http://ubuntuforums.org/showthread.php?t=195382&highlight=google+earth")

I installed it this way very easy.

---

### Post by heatrag on 2007-05-15
Thanks for the feedback, all of the above was helpful, however google earth doesn't appear to run on my machine after the instal, although the spec seems within the prescribed it restarts after the Google Earth start up window. I  get screen of text for a moment one line of which I seem to remember referring to the cpu frequency then the restart.

---

### Post by taurus on 2007-05-15
Google Earth is a 3D app so have you installed a driver for your graphic card?  And what kind of graphic card do you have on your machine anyway?

```
lspci
```

---

### Post by heatrag on 2007-05-15
here's the lot:
> 00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:09.0 Communication controller: Ambient Technologies Inc HaM controllerless modem (rev 02)
00:0b.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233 PCI to ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.4 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
what about the built in capibilites, does that count?

---

### Post by xthund3rh3adx on 2007-05-15
here is mine....im pretty sure i installed the driver too
```

00:00.0 Host bridge: Intel Corporation 82810 GMCH [Graphics Memory Controller Hub] (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810 CGC [Chipset Graphics Controller] (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
01:09.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)
01:0a.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)
01:0b.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)

```

---

### Post by heatrag on 2007-05-15
Back to mine, am I missing something or are there more devices than slots?

---

### Post by xthund3rh3adx on 2007-05-15
try to find your graphics card's driver. It doesnt look like its installed.

---

### Post by heatrag on 2007-05-15
I havent a clue how to do that, sureley there must be some sort of graphics driver, I run the monitor at 1280x1024.

---

### Post by xthund3rh3adx on 2007-05-15
probably just because its built in basic graphics drivers....before i installed my driver i had higher resolutions too. But even after installing my driver google didnt work, so yeah i understand.

---

### Post by heatrag on 2007-05-15
Is it working now?
 If I were to go out and get a basic graphics card (3d?) would it come with a linux driver, would I be duplacting hardware I already have and will google earth work?
Atcuall it's purley accedmic now because I can't think of any other application I need a card for, google earth is a frill I can possibly live without if it ment spending money.

---

### Post by ikman on 2007-05-16
I have a Compaq Presario R3000 (R3306US to be exact) with Ubuntu 7.04 installed with all updates.
My lspci output showed this as one of the lines:
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)

Whether I click on the desktop GoogleEarth icon, run it from the Applications menu where it installed,  or use the terminal cmds: sh Googl.. or ./Goo.. I get a terminal window that says everything is ok, then a splash screen that installs the instance of GoogleEarth and, usually, the splash screen says "installed fine" with a Start button that, when pressed, proceeds to make me either login to Linux again or login just before it shuts down.

I also tried installing GoogleEarth using the forum-provided wget command to install GoogleEarth, after uninstalling the original files, but I get the same results as most others with this problem.

Still no joy.

---

### Post by byenary on 2007-05-16
install automatix and its just a few clicks away...:guitar:

---

### Post by heatrag on 2007-05-17
Yes. yes, but its not the install thats the problem now (unless installing it in the home folder is) its the fact that it restarts the computer when I try to open it.

---

### Post by Kangaroo on 2007-05-17
But it probably does that, because the 3D-Driver for your Graphics Card is missing. 

Try to install die Nvidia-Drivers in Automatix and try again to start Google Earth.

---

### Post by heatrag on 2007-05-18
Nvidia-drivers have solved the problem,
Fantastic, I can go and impress the neighbours with Google earth now.
Thanks all,

---

