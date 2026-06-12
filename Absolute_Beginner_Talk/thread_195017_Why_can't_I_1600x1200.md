---
title: "Why can't I 1600x1200?"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by MoxJet on 2006-06-12
Since I installed Dapper Drake I cannot anylonger pick 1600x1200 as my screen resolution. What do I need to install to make that possible? My graphic card can handle it, I used it all the time with Badger.

Thanks in advance,
Dan

---

### Post by taurus on 2006-06-12
What video card do you have and did you happen to install a driver for it?

---

### Post by MoxJet on 2006-06-12
In case this is necessary:

```

dan@Mainframe:~$ lspci
0000:00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
0000:00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
0000:00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
0000:00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
0000:00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
0000:00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2)
0000:00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
0000:00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
0000:00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
0000:00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
0000:00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:05:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0162 (rev a1)

```

---

### Post by taurus on 2006-06-12
So you have nVidia card.  Try to install nVidia driver for it and see if you can get to whatever resolution you want to use...
```

sudo apt-get install nvidia-glx

```
Don't forget to replace "nv" with "nvidia" in /etc/X11/xorg.conf after you installed nvidia-glx...  Then, <Ctrl><Atl>Backspace to restart X and at this point, you should see an nVidia logo!

---

### Post by MoxJet on 2006-06-12
My nvidia-glx was already installed and I opened the /etc/X11/xorg.conf, but couldn't find the "nv" you were talking about, it said NVIDIA... everywhere, so I brutally changed the following rows in the end:
```

    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection

```

By simply adding "1600x1200", and it worked.

Thanks a lot, I never knew about that agressive ctrl+alt+backsp restart nor the xorg.conf-file, which seems good to remember!

---

