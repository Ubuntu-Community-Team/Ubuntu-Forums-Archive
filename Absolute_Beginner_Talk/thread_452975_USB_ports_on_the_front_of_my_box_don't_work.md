---
title: "USB ports on the front of my box don't work"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by hanzj on 2007-05-23
Hello,
I've just installed Ubuntu 7.04 on my computer. My computer has 9 USB ports: 6 at the back, and 3 in front.  When I plugged in my iPod into a USB port in front,  the iPod wasn't getting charged. But when I plugged in my Ipod onto a USB port at the back, the connection worked.

How can I figure out what's wrong?

Thanks!

I think that all of my USB ports are 2.0 compliant, (though I'm not sure).
I also think that my iPod is able to use a 1.0 port.


Here is the reading of** lsusb**: > 
Bus 002 Device 002: ID 05ac:1209 Apple Computer, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 


The following is the reading of **lspci:**

> 00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
05:00.0 VGA compatible controller: ATI Technologies Inc R480 [Radeon X850XT Platinum (PCIE)]
05:00.1 Display controller: ATI Technologies Inc R480 [Radeon X850XT Platinum (PCIE)] (Secondary)



---

### Post by drowner on 2007-05-23
When you plugged it in the front, did it mount your iPod?

USB drives 'at the front' are notorious for being not as powerful as the back ones, even (especially!) in windows.

Try plugging something less powerful, like a USB flash drive in the front, and see how that goes. I am going to guess charging the iPod is a bit too heavy for the front.

---

### Post by hanzj on 2007-05-23
No. When I plugged in the iPod at the front, my iPod was not mounted.

---

### Post by drowner on 2007-05-23
Does the front USB port mount a flash drive, or let anything else work?

---

### Post by hanzj on 2007-05-24
I checked the BIOS of my computer for USB information.
The BIOS is Phoenix Award WorkStationBIOS CMOS Setup UTility / Integrated Peripherals

OnChip USB: V1.1+2.0
USB Memory Type: Shadow

---

### Post by easy_target on 2007-05-25
I have the same peculiar behavior. Intersting enough if I plug it to the back ports it works like it should. Go figure...

---

### Post by hanzj on 2007-05-25
I haven't tried other devices yet, but I guess I could.

---

