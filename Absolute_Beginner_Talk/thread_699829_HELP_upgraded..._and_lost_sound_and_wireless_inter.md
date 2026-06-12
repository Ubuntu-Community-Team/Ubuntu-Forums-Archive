---
title: "*HELP* upgraded... and lost sound and wireless internet... from 7.04 to 7.10"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Jerad on 2008-02-17
upgraded.... now have no sound or wireless internet... someone please help me out

---

### Post by Presto123 on 2008-02-17
If wireless doesn't show up in System/Administration/Restricted Drivers Manager, post the output of:
```
lspci
```

With sound, double click your audio icon in the panel and try the different drivers. If those don't work, try in System/Preferences/Sound doing the same thing.

---

### Post by JoshuaRL on 2008-02-17
If you upgraded then you probably overwrote those settings.  Do you remember what you had to do to get them running correctly in Feisty?

---

### Post by mobio on 2008-02-17
I had similar problem, and there were two solutions. First is to check the following :
if you have this Linux kernel 2.6.22-14-386 with the emphasis on 386 and you also have kernel 2.6.22-14-generic, than choose generic because wifi didn't work for me in 386 mode at all (I don't know how I got it at the first place since usually I use only generic)
Secondly you might need to enable restricted driver. So find restricted drivers option somewhere in settings and than just click on the driver from your wireless card to activate it.

Best

---

### Post by laihafloyd on 2008-03-29
i am having similar problems.  everything worked in gutsy, now i lost my wifi (it shows that the hardware is present, but it does not show up in the list in network settings), my sound says that there is no hardware or driver present (No volume control GStreamer plugins and/or devices found), and when gnome starts up, the resolution is all screwed up.  it seems as though the screen resolution is fine, but my fonts are so small i can't make out any of the characters.  to get around this, i start gnome in fail safe and the fonts are normal.  but every time i log in or out or switch users, it goes back to miniature fonts!  the weird thing is my 3d desktop works fail safe mode, but not in the normal gnome session.  i don't even know where to start.  

here are my lspci and lsusb (i use a usb wireless network adapter).  any help would be GREATLY appreciated.  Thanks!


Marc

marc@marc-desktop:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:07.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
01:08.0 Communication controller: Conexant HCF 56k Data/Fax/Voice/Spkp Modem (rev 08)
01:09.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
marc@marc-desktop:~$ lsusb
Bus 003 Device 007: ID 13b1:000a Linksys 
Bus 003 Device 006: ID 090c:1000 Feiya Technology Corp. Memory Bar
Bus 003 Device 003: ID 059b:007e Iomega Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 03f0:2f11 Hewlett-Packard 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000  
marc@marc-desktop:~$

---

### Post by laihafloyd on 2008-03-29
oops, i just realized that the original post was upgrading to gutsy gibbon,   i went from gibbon to hardy haron beta.  just wanted to clarify that...

thanks again for any input.


marc

---

### Post by laihafloyd on 2008-03-29
another oops....
when i first read the post, i overlooked the post about switching the kernel to generic.  i tried it and it worked for my wifi and for my sound card.  but my resolution problem is still there.  what does switching kernels like that actually do?  is it going to affect anything in the long term as far as kernel updates and such?

---

