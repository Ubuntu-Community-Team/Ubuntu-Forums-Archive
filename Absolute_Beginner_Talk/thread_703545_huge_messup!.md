---
title: "huge messup!"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by SRG8 on 2008-02-21
complete linux newbie here so i apologyze in advance. grub loads fine, whenever i boot up now it doesnt boot up to my login screen, instead it asks me for my login in terminal. i punch in my user name and password as i would in the login page but it tells me login incorrect!

what i was doing before was trying to reconfigure my graphics card because i was having troubles with it and thus was running in low graphics mode. i managed to reset it to the appropriate driver but it still wouldnt let me enable desktop efffects. i tried it again with and restarted my computer and now this happens!

how do i get back to my desktop, im really not too comfortable in terminal and i have no idea why its telling me i have the wrong login when i write it as the exact same as i would in my login screen?

---

### Post by skymera on 2008-02-21
sudo dpkg-reconfigure -phigh xserver-xorg

put that in and that should help you get back to GUI.

what is your current graphics card?

---

### Post by SRG8 on 2008-02-21
k it gave me back this: xserver-xorg postinst warning: overwriting possibly-customized configuration file; backup in /etc/X11/xorg.conf.20080221133612

according to my manufacturer my video adapter is the nvidia geforce go 7200, but in screen and graphics manager it said i had the intel 945, i dont know much about this so i dont know if their the same thing or if one is the actual card and the other is just something else. i do have the drivers though, the i810 and the glx-nvidia-new, something like that it was

---

### Post by SRG8 on 2008-02-21
k i managed to get back into my desktop, phew. thanks for your help. i ran the driver configuration again in terminal and rebooted and i got through!

but if you could still help me with my original problem concerning not being able to enable desktop effects i would appreciate it a bunch. i know my card can support it because it ran fine up until a few days ago where i tried setting up a second screen. at first i got a pop up telling me my graphics card could not be detected correctly every time i booted, and i got some help so now im able to select the appropriate drivers for the card and that message is gone, however when i go to the appearance menu and try nd select desktop effects it tells me they cant be enabled :S

---

### Post by jan quark on 2008-02-21
please run in terminal

```
lspci
```

to get to know the exact model of your card
according to that we can help you to enable the effects

---

### Post by SRG8 on 2008-02-21
i get this when i ran it:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
08:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

---

### Post by SRG8 on 2008-02-22
i guess from that, that means i have the intel 945. currently the driver i have selected is the i810 which is the driver iv been told by the system and the internet i should be using, so why am i not able to enable desktop effects? i know its supports them cause i had them running since i installed ubuntu until a few days ago

---

