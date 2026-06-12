---
title: "Just installed Dapper, having a couple of difficulties"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by hanyoutbone on 2006-10-01
Hello, I just recently installed Dapper (the 64 bit version) on my computer, and after a little bit of trouble getting the gui working correctly, i am finally able to get it running almost fine.  

My first problem is that my computer won't shut down or restart properly.  When I click on the shutdown or restart button it closes out the gui, however I don't get a splash "halting" screen.  The screen just goes black then my monitor's OSD says "No signal input detected".  So then I have to manually power off my computer.  I've tried shutting down and restarting through the terminal, and the same problem occurs.

My other problem is that I recently installed the latest ATI proprietary drivers for my X800XL (8.29.06) and mostly everything is working fine, except that none of the 3D screensaers packaged with dapper work anymore.  Before I installed them, they were working fine.  And when I open the ATI control panel under OpenGL it says "Vendor: Unavailable" and "Version: Unavailable".  So I think that may be part of the problem.  As of right now I don't have any linux compatible 3D programs installed, so I'm not sure if it's just the screensaver or 3D graphics in general.

Please give me some advice as to how I should solve this, and also tell me if you need any extra information, and how to get it (I don't know hardly any linux commands).

---

### Post by uk_sphinx on 2006-10-01
i had problems with my ati drivers and all.
useless gits.
try googling if no-one knows anything on here m8.
i got my answers from ati FAQ

---

### Post by hanyoutbone on 2006-10-01
Here's some more info that may or may not be relevant, I'm not too sure.

Kernel version:  2.6.15-27-amd64-generic
X Server: Xorg 7.0.0

Should I uninstall the proprietary drivers and replace them with something else?  I think i was using flglx before installing the proprietary drivers (set it during install because for some reason vesa wasn't working at all).

Oh and I should note that even before I installed the ATI drivers that ubuntu would not shut down/restart.

Thanks

---

### Post by hanyoutbone on 2006-10-02
Does anybody have any idea on what I should do?  I tried googling but didn't get helpful results.  I also tried running OpenGL games I dl'ed through Synaptic, but they don't work.  Here's what lspci returned if anyone needs it, any help would be greatly appreciated:

> 0000:00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
0000:00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
0000:00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
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
0000:05:00.0 VGA compatible controller: ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)
0000:05:00.1 Display controller: ATI Technologies Inc R430 [Radeon X800 XL] (PCIe) Secondary

---

### Post by nudnik on 2006-10-02
> **hanyoutbone said:**
> Here's some more info that may or may not be relevant, I'm not too sure.

Kernel version:  2.6.15-27-amd64-generic
X Server: Xorg 7.0.0

Should I uninstall the proprietary drivers and replace them with something else?  I think i was using flglx before installing the proprietary drivers (set it during install because for some reason vesa wasn't working at all).

Oh and I should note that even before I installed the ATI drivers that ubuntu would not shut down/restart.

Thanks

Go back to the flglx. That will allow for the best performance you are going to get.

Second, the 64 bit versions of Dapper are a bit flaky, so you can expect unusual things, just as with Kubuntu, which is also somewhat goofy. For the most stable results, go with a Gnome desktop in a 32 bit version. 

Remember...this ](*,)  aint the mascot for nothin'!

---

### Post by petri on 2006-10-02
Running 64-bits Ubuntu as a beginner? 64-bits Ubuntu is not for a beginners in gnu/linux.

If you are a gnu/linux user there is a forum for you here [http://ubuntuforums.org/forumdisplay.php?f=134](http://ubuntuforums.org/forumdisplay.php?f=134)

If you are a beginner in gnu/linux but demand a 64-bit, browse yourself to forum above. There is everyone a beginner ;) 

Otherwise install 32-bits Ubuntu. That should work :D

---

### Post by hanyoutbone on 2006-10-02
Ok, thanks, I had no idea when installing the 64 bit version that it would be somewhat buggy lol.  I'll just install the 32 bit version then.

---

