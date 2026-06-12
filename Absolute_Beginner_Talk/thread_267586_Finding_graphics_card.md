---
title: "Finding graphics card"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by IusedTObeSOMEONEelse on 2006-09-28
I do not know which graphics card I have, Trying to use google earth. How do I find which card I have and upgrade it

---

### Post by meng on 2006-09-28
Try this from terminal:
lspci
and look among the PCI devices listed for your graphics card.

Or else look under System > Admin > Device Manager.

---

### Post by IusedTObeSOMEONEelse on 2006-09-28
Not sure what I'm looking for  meng           ~$ lspci
00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 05)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 05)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 05)
01:00.0 Modem: ALi Corporation SmartLink SmartPCI561 56K Modem
01:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)

---

### Post by meng on 2006-09-28
> **MustangSallydd said:**
> 
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03)
This is it. Must be one of them on-board thingies.
EDIT: It's an Intel 810 video controller.

---

### Post by IusedTObeSOMEONEelse on 2006-09-28
Will it work for google earth and can driver be updated? Please forgive my ignorance on computer "guts".

---

### Post by emarkay on 2006-10-19
"Intel® 82810 Graphics Controller
End of Interactive Support Announcement
These products are no longer being manufactured by Intel."
[http://support.intel.com/support/graphics/intel810/](http://support.intel.com/support/graphics/intel810/)

Drivers:
[http://downloadfinder.intel.com/scri...?ProductID=798](http://downloadfinder.intel.com/scri...?ProductID=798)

Most recent drivers are from 2002, however.

---

### Post by IusedTObeSOMEONEelse on 2006-10-19
What you are telling me is, that I now have to take my machine in and have the card changed. I may be wrong but is that not part of the mother board? And that is some thing I can not change my self as I am not the 'Brightest Bulb" on the tree!  haha :confused:

---

### Post by gn2 on 2006-10-19
> **MustangSallydd said:**
> What you are telling me is, that I now have to take my machine in and have the card changed. I may be wrong but is that not part of the mother board? And that is some thing I can not change my self as I am not the 'Brightest Bulb" on the tree!  haha :confused:

You can add a graphics card to your PC to use instead of the the on-board one.

Even if you don't have an AGP or PCI-e slot you can use a PCI one.

Installing it is simple enough, one screw to remove after you get the case open.

[http://en.wikipedia.org/wiki/Accelerated_Graphics_Port](http://en.wikipedia.org/wiki/Accelerated_Graphics_Port)

[http://en.wikipedia.org/wiki/PCI_Express](http://en.wikipedia.org/wiki/PCI_Express)

[http://en.wikipedia.org/wiki/Peripheral_Component_Interconnect](http://en.wikipedia.org/wiki/Peripheral_Component_Interconnect)

---

