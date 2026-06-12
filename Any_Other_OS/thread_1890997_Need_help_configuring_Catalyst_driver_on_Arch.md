---
title: "Need help configuring Catalyst driver on Arch"
date: 2011-12-04
forum: Any Other OS
---

### Post by ratcheer on 2011-12-04
I am trying to install and configure the Catalyst fglrx driver on Arch Linux. With a little help from the people in the Arch forums, I followed the instructions on the Arch wiki to the letter and everything ran, successfully.

However, when I reboot Arch, I get a mostly black screen with a few colored bands at the top and a large, blue square mouse pointer. I have asked for more help in the Arch forums, but they have declined to respond. Yes, I am aware that it is a pretty tough crowd. So I am asking, here.

At first, I thought I might have messed up my xorg.conf. But, comparing it to the corresponding file on my Ubuntu system, which is working perfectly, the only difference is the line 'Load "glx"' in the Module section. This line is in my Ubuntu configuration, but not in Arch. I tried adding the line for Arch, but it made no difference.

So, I am stuck. I think there may be some bugs to work around in Arch, but I'm not sure. There are a few extra lines in the example xorg.conf on the Arch Wiki, but I'm not sure about them.

Does anyone here know how to fix such a situation?

Thanks,
Tim

---

### Post by ratcheer on 2011-12-04
If it will help, here is my xorg.conf file:

```
Section "ServerLayout"
         Identifier     "aticonfig Layout"
         Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
         Identifier   "aticonfig-Monitor[0]-0"
         Option        "VendorName" "ATI Proprietary Driver"
         Option        "ModelName" "Generic Autodetecting Monitor"
         Option        "DPMS" "true"
EndSection

Section "Device"
         Identifier  "aticonfig-Device[0]-0"
         Driver      "fglrx"
         BusID       "PCI:1:0:0"
EndSection

Section "Screen"
         Identifier "aticonfig-Screen[0]-0"
     Device     "aticonfig-Device[0]-0"
         Monitor    "aticonfig-Monitor[0]-0"
         DefaultDepth     24
         SubSection "Display"
                 Viewport   0 0
                 Depth     24
         EndSubSection
EndSection
```

---

### Post by ratcheer on 2011-12-04
Ok the problem is somewhat SOLVED.

I did a bunch of stuff and I'm not sure what fixed it (maybe it was all of it).

I  had to manually edit grub.cfg (a no-no for grub2) to add nomodeset to  the boot command for Arch. Adding it to /etc/default/grub and running  update-grub only set the parameter for Ubuntu. This will probably cause  me trouble down the road.

That got me running Arch, again. There,  I added fglrx to the MODULES parameter in rc.conf, blacklisted radeon,  and rebooted. I seem to now be running fglrx and everything looks great,  but none of the tests the Wiki says to run confirm that it is actually  working. However, Xorg.0.log shows the fglrx driver loaded and displays  many messages from the module, so it seems like it is working.

Since 8:30 this morning, no one in the Arch forum has responded to my requests. What a great bunch of guys (not!).

Tim

---

### Post by mips on 2011-12-05
Post removed.

---

