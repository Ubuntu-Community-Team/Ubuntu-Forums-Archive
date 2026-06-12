---
title: "installing pcmcia firewire card and unibrain fire-i camera"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by pip2 on 2006-08-21
Hello!

first: sorry for my bad english :)
i am new in linux (installed yesterday) so i haven´t a clue how to get the hardware working.
i want to use a firewire camera (unibrain fire-i) on my notebook.
the problem is that i must use a pcmcia card because the notebook has no firewire connections.
i installed all requested ieee1394 drivers but the camera still doesn´t work!

coriander:
found the camera

gscanbus:
found a s400 av/c device

kino:
doesnt find a camera

dvgrab:
Error: no camera exists


with *lspci* i get the following:
0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
0000:00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Radeon Mobility M300]
0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)
0000:0b:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 8d)
0000:0b:02.0 Network controller: Intel Corporation PRO/Wireless 2915ABG MiniPCI Adapter (rev 05)
0000:0c:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)

with *pccardctl* info i get this:
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

which steps are requested to make the camera working?

Thanks, 
pip2

---

### Post by theJagger on 2008-03-11
i would also like to get this camera working

---

