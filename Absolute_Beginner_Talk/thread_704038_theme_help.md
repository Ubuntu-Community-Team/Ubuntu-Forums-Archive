---
title: "theme help"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by zerobinary on 2008-02-21
After i updated the top frame get smaller. How do i restored to default 
[IMG]http://i183.photobucket.com/albums/x196/zerobinary/Screenshot-22.png[/IMG]

---

### Post by spiderbatdad on 2008-02-21
in your picture click the font tab, and change the size of the window title font.

---

### Post by zerobinary on 2008-02-21
do u can me what is the default setting

---

### Post by spiderbatdad on 2008-02-21
10

---

### Post by zerobinary on 2008-02-21
what font 
and do u know how to i configure my compiz 
to this.
[IMG]http://i183.photobucket.com/albums/x196/zerobinary/Screenshot-23.png[/IMG]
[http://www.desktoplinux.com/files/misc/compiz-cube.jpg](http://www.desktoplinux.com/files/misc/compiz-cube.jpg)

---

### Post by zerobinary on 2008-02-21
anyone

---

### Post by spiderbatdad on 2008-02-21
sans is the font i have. And have you configured compiz to work at all?```
sudo apt-get install compizconfig-settings-manager
```Then try to enable desktop effects under System>>Preferences>>Appearance>>Visual Effects. If you cannot...post back the result of: ```
lspci
```

---

### Post by zerobinary on 2008-02-21
anyone plz help
i just can't rotate like them 
i like rotate 3d between 4 workspace
but how can i project the cube thing

```

zerobinary@zerobinary-desktop:~$ sudo apt-get install compizconfig-settings-manager
[sudo] password for zerobinary:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compizconfig-settings-manager is already the newest version.
The following packages were automatically installed and are no longer required:
  libxine1-gnome
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
zerobinary@zerobinary-desktop:~$ lspci
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0611 (rev a2)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:09.0 Multimedia audio controller: Creative Labs SB X-Fi

```

---

### Post by zerobinary on 2008-02-22
any hand

---

### Post by spiderbatdad on 2008-02-22
go to the advanced desktop effects settings in your system preferences. Find Cube...select rotate cube and Desktop cube. Click on the rotate cube and go to the actions tab...see screenshot...Click on the key or button options to set a key or button. I think by default you'll see Ctrl-Alt-Button1 is set. That is left mouse+Ctrl+Alt

---

### Post by zerobinary on 2008-02-22
thx

---

### Post by incen on 2008-02-22
sans is the default font for Ubuntu. The size is set to 10 for all. The last one is monospace 10, as what you have now! ^^

---

### Post by spiderbatdad on 2008-02-22
see zoom? Move that slider to zoom out during rotate.

---

