---
title: "another hdmi question"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by deadmnky on 2008-01-24
my question is how do i get a display from hdmi card slot on  an asus M2A-VM hdmi motherboard. i think it is recognized when i use the lspci command but i am not sure here is the out put in question 

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)

well i was nly going to post part of it but i figured the whole thing would be better. i also can not get any display when i have a dvi-d cord plugged in.
i have read a bunch of the forums tried google/linux but cant find the info i need.

---

### Post by kplaxmaster on 2008-01-25
Hey.  This is a known bug that came upstream from Debian.  However, there is a known fix for this which is very easy!!

When starting the live-cd, press F6 when it has options.  Delete the section "splash", and simply press enter.  For some reason, when splash is included, DVI wont work and just goes black!

Also, after you successfully install and reboot your machine, you need interrupt grub before it starts with the splash parameter again.  So press any key to interrupt grub within the 3 seconds it gives you by default.  Then press "e" to edit grub parameters you wish to boot.  Then find the line that includes "splash" at the end, i believe it is the second one.  Delete the word "splash" and press enter, then press "b" to boot it up with the selected bootup parameters.

Next.... we need to change the grub file so that this doesn't happen again every time!

So...use your favorite text editor to edit the /boot/grub/menu.lst.  In this case I use nano:
```
sudo nano /boot/grub/menu.lst
```

Go all the way to the bottom, as you can see how the file is setup.  You will find the word splash again, simply delete it but making sure everything else stays the way it is.  Then save the file.

Now everytime you reboot, your grub won't include "splash" into the bootup parameter and you DVI won't have a problem anymore!

Hope this helps.

---

### Post by deadmnky on 2008-01-25
thank you i was just trying to that but unforunatly the dvi slot does not display in the bios either. so i am going to buy a new monitor any way and i will see what happens. if  i have any more ?s i will return to this post.

---

