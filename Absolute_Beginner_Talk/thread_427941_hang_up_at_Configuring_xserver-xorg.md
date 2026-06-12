---
title: "hang up at Configuring xserver-xorg"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Conanu on 2007-04-29
I am trying to load the correct driver for my Intel 945GM graphics card, so I downloaded and installed xserver-xorg-video-intel_2.0.0-1_i386.deb.

Then I typed xserver-xorg-video-intel_2.0.0-1_i386.deb into terminal, selected "Intel" from the list of drivers, pressed enter twice, and then I get stuck on the screen that says:

 Configuring xserver-xorg 
                                                                           &#9474;  
 &#9474; Users of PowerPC machines, and users of any computer with multiple video  &#8593;  
 &#9474; devices, should specify the BusID of the video card in an accepted        &#9646;  
 &#9474; bus-specific format.                                                      &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; Examples:                                                                 &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474;  ISA:1                                                                    &#9618;  
 &#9474;  PCI:0:16:0                                                               &#9618;  
 &#9474;  SBUS:/iommu@0,10000000/sbus@0,10001000/SUNW,tcx@2,800000                 &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; For users of multi-head setups, this option will configure only one of    &#9618;  
 &#9474; the heads.  Further configuration will have to be done manually in the X  &#9618;  
 &#9474; server configuration file, /etc/X11/xorg.conf.             

When I press enter, nothing happens. Anyone know what to do?

---

### Post by [S|G] on 2007-04-29
What exactly are you trying to do? I have an intel 945GM on my notebook and it was detected automatically and had hardware accel from the start. The only things that were wrong were the resolution that wouldn't go to 1280x800 and I couldn't get it to work on two monitors at the same time. I managed to get the resolution right, though.

---

### Post by Conanu on 2007-04-30
I was having problems with the resolution as well, but I was able to solve that problem. Now I just want to make sure that I am using the correct driver, and that I understand how to configure xserver-xorg.

---

### Post by [S|G] on 2007-04-30
The driver that supports the 945GM is the i810:
```

Section "Device"
        Identifier      "Intel Corporation Mobile Integrated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

```
I believe that the driver is avaliable in the default installation. To check that you have hardware acceleration you can run glxinfo and check that you have "direct rendering: Yes".

You can also run glxgears and check the frame rate. It should be 600+ and the animation should look smooth.

---

### Post by Conanu on 2007-05-05
Thanks for the help SG....all vital signs are good to go!

---

