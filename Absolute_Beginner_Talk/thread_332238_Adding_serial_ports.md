---
title: "Adding serial ports"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-01-05
How do I tell Ubuntu Dapper that there are more than 4 serial ports?

---

### Post by ingo on 2007-01-07
try

sudo lspci

to see whether they are there

---

### Post by Mark_in_Hollywood on 2007-01-07
mark@Lexington:~$ sudo lspci
Password:
0000:00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 02)0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 01)
0000:00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 01)
0000:00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 01)0000:00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 01)
0000:01:0c.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 06)
0000:01:0d.0 Communication controller: Agere Systems Venus Modem (V90, 56KFlex)
0000:02:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS

BUT, what is happening is that sudo wvdialconf sets the modem on ttyS4 and then wvdial and GnomePPP's logs both say "cannot set serial port"

I need to make ubuntu/dapper "aware" or "see" a modem as ttyS4 on IRQ 3 each and every time I boot. I can't find which files to modify or what to put in them to make the modification.

---

