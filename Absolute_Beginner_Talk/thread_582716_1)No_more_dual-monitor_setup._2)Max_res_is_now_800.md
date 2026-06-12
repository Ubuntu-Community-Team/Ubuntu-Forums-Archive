---
title: "1)No more dual-monitor setup. 2)Max res is now 800x600 in Gutsy Gibbon 7.10 install"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by hanzj on 2007-10-20
Hello,
I have just  fresh/clean-installed Ubuntu 7.10 Gutsy Gibbon. I was previously using Ubuntu 7.04 Feisty Fawn, where I was able to get a dual monitor (side-by-side) setup working by tweaking the xorg.conf. (By the way, I no longer have a copy of my older Feisty-era xorg.conf. It was erased with the rest of my hard drive.)


My two CRT monitors are NEC MultiSync FP2141SB and AOC 9KLR. 

According to the Net, my NEC MultiSync FP2141SB supports up to 2,048 x 1,536 resolution at 85 Hz. 

The AOC 9KLR has a display size of 19" (18" Viewable), and aresolution of 1160 x 1200 (Maximum).

 Yet under Gutsy Gibbon, it seems my max for either monitor is 800x600.
And I no longer am able to get side-by-side dual-monitor setup in Gutsy 7.10. Instead, I am just having "duplicate" monitors.

"Screen and Graphics Preferences" has neither model is in the list of monitors. When I do "detect" in "Screen and Graphics Preferences", it goes to "Generic" Manufacturer and "Plug N' Play" Model. I clicked the "Add" button, and "chose the driver file" that I downloaded from NEC's website ([http://www.necdisplay.com/SupportCenter/Monitors/SignedINF/necmsinf.zip](http://www.necdisplay.com/SupportCenter/Monitors/SignedINF/necmsinf.zip)), but the_[ webpage that gives the link to that zip file]("http://www.necdisplay.com/SupportCenter/Monitors/InstallDrivers/")_ says that the driver is for Windows 2000/XP.



Now, I'm going to paste what may be other relevant info about my video card and system:

**$ lspci**
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

Please also see attached files.

Thank you for your help.


P.S. Related Bonus Problem: I no longer have 32-bit color depth.

---

### Post by hanzj on 2007-10-20
Hello,
I was able to increase my displays'  screen resolution to something higher than 800x600. I was able to do this by:
```
 sudo dpkg-reconfigure xserver-xorg
```

Question: Is running that command something that one should not do in Gutsy, as xorg is controlled by Screen and Graphics Preferences? 

Question: How come I can't get dual-monitor setup working on Gutsy? Is it because the computer doesn't know that my video card can do dual-monitor setup?

---

### Post by hanzj on 2007-10-20
help.

---

### Post by hanzj on 2007-10-22
I've received some advice:
> 
You have an ATI Radeon.  The radeon driver is now able to configure
dual monitors dynamically with xrandr, but it lost the support for
old-style xorg.conf configuration.

Here's what Ubuntu 7.10 release notes tell you:

  Dual-head (multi-screen) setups

    * The ati driver has dropped MergedFB / Xinerama support in favour
      of xrandr 1.2 support, and old multi-head xorg.conf setups will
      break. To set up dual-head see the guides at
      [http://www.intellinuxgraphics.org/dualhead.html](http://www.intellinuxgraphics.org/dualhead.html) or
      [http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)I read both links and tried the first link's instructions on setting
up with xrandr.

Print-out of " xrandr -q": 

> $ xrandr -q
Screen 0: minimum 320 x 200, current 1600 x 1200, maximum 1600 x 1200
S-video disconnected (normal left inverted right)
DVI-1 connected 1600x1200+0+0 (normal left inverted right) 396mm x 297mm
   1600x1200      85.0*+   75.0  
   1280x1024      84.8     75.0  
   1152x864       75.0     74.8  
   1024x768       84.9     75.1     70.1     60.0  
   832x624        74.6  
   800x600        84.9     72.2     75.0     60.3     56.2  
   640x480        84.6     75.0     72.8     66.7     60.0  
   720x400        87.8     70.1  
DVI-0 connected 1280x1024+0+0 (normal left inverted right) 360mm x 270mm
   1280x1024      85.0*+   84.8     75.0  
   1600x1200      75.0  
   1280x960       84.9  
   1024x768       84.9     75.1  
   800x600        84.9     75.0  
   640x480        84.6     75.0     60.0  
   720x400        70.1  When I try to setup one monitor to the side of the other:

>  $ xrandr --output DVI-0 --left-of DVI-1
xrandr: screen cannot be larger than 1600x1200 (desired size 2880x1200)I'm not sure what xrandr means by "screen". The sum of the 2 monitors,
or something else?

Also, because my monitors are not of the same physical size (one's a
21 inch and the other is 19 inches), I suppose I need to tell the
Ubuntu computer of the physical locations of the monitors, where one
monitor lies in relation to the other.

---

### Post by hanzj on 2007-10-27
Can anyone help me please?

Is there no way for xrandr to fix things?

The problem is this:

> $ xrandr --output DVI-0 --left-of DVI-1
xrandr: screen cannot be larger than 1600x1200 (desired size 2880x1200)

Thank you.

---

