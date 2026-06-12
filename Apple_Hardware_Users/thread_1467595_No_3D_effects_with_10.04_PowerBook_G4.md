---
title: "No 3D effects with 10.04 PowerBook G4"
date: 2010-04-30
forum: Apple Hardware Users
---

### Post by Dukenukemx on 2010-04-30
Just did a fresh install of Ubuntu 10.04 and I can't enable the Extra Visual Effects.  I get the error "Desktop effects could not be enabled".  

I'm a noob at this, could someone help?

---

### Post by Dukenukemx on 2010-05-01
Here's what info I can get about my 3D.

  *-display               
       description: VGA compatible controller
       product: RV350 [Mobility Radeon 9600 M10]
       vendor: ATI Technologies Inc
       physical id: 10
       bus info: pci@0000:00:10.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm bus_master cap_list rom
       configuration: driver=radeonfb latency=255 mingnt=8
       resources: irq:48 memory:b8000000-bfffffff(prefetchable) ioport:400(size=256) memory:b0000000-b000ffff memory:b0020000-b003ffff(prefetchable)

---

### Post by Dukenukemx on 2010-05-01
Again, more information.  Clearly Software Rasterizer is used.

Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use

---

### Post by Ezdine on 2010-05-01
I've a PowerMac G4 "Quicksilver" with an ATI Radeon 9700.  I'm also a victim of software rendering, in 9.10 I had excellent hardware acceleration with the radeon driver.

From the moment I should see plymouth at boot, I can tell something is amiss.  I'm going to start by rolling a newer kernel to see if the issue is in the driver.  The X logs don't reveal anything out of the ordinary. 

I'll post if I find a solution.

---

### Post by Dukenukemx on 2010-05-01
Zeroti found a solution [here](http://www.uluga.ubuntuforums.org/showpost.php?p=9194781&postcount=11), but I have no idea how to reproduce his actions.

---

### Post by linuxnoob420 on 2010-05-01
I did not think compiz was even supported on power pc I feel stupid asking but did you have 3D effects before the upgrade because i could never get them period??

---

### Post by conal on 2010-05-01
> I did not think compiz was even supported on power pc

There is some 3D support for Power PC if you have an ATI Radeon card. See the Ubuntu PowerPC FAQ:

[https://wiki.ubuntu.com/PowerPCFAQ]("https://wiki.ubuntu.com/PowerPCFAQ")

Cheers

Conal

---

### Post by Dukenukemx on 2010-05-01
Compiz worked just fine before in 9.10.  There is a way to fix it but I don't know how to create a /etc/modprobe.d/radeon-kms.conf and a /etc/X11/xorg.conf .

I still don't.

---

### Post by Ezdine on 2010-05-01
> Compiz worked just fine before in 9.10. There is a way to fix it but I don't know how to create a /etc/modprobe.d/radeon-kms.conf and a /etc/X11/xorg.conf .

I still don't.

Duke, just drop to a console and

```
sudo nano /etc/modprobe.d/radeon-kms.conf
```

then paste in the exact same information as Zeroti.  Then do the same for the other file.

```
sudo nano /etc/X11/xorg.conf
```

After pasting the contents in, hit control-X to save the newly created files.  Those don't exist by default, you'll be creating them from the copy -> paste.  You may have to edit Zeroti's xorg.conf settings to match your system though.  You would definitely need to omit the BbusID line in his xorg.conf, unless your card is sitting in the exact same place (you can safely omit the line altogether imo.)

---

### Post by Dukenukemx on 2010-05-01
Thanks, was able to create the Radeon-kms.conf, but not the xorg.conf.  I get [Error writing /etc/x11/xorg.conf: No such file or directory ].  

What I do wrong?

---

### Post by Dukenukemx on 2010-05-01
Jesus, it's case sensitive.  x11 isn't the same as X11.  

Everything works again, thanks.

---

### Post by Ezdine on 2010-05-01
Make sure you're doing it as root and using that exact path.

/etc/X11/xorg.conf doesn't exist -- you're creating a brand new one.  

Remember that upper/lowercase matter, write it exactly as you see it here.


[EDIT] Dang, didn't see you'd figured that out lol.

---

### Post by faheyd on 2010-11-19
> **Ezdine said:**
> Make sure you're doing it as root and using that exact path.

/etc/X11/xorg.conf doesn't exist -- you're creating a brand new one.  

Remember that upper/lowercase matter, write it exactly as you see it here.


[EDIT] Dang, didn't see you'd figured that out lol.

Hi All, 
  This is my config file for ubuntu 10.10 on my PowerBook G4 with an ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] video card in it. Do not use this if you have an nvidia card. Use lspci to see what card you have. I also loaded up 'driconf' to see what's happening (it will work only when you got stuff loaded correctly)

Section "Device"
    Identifier    "Radeon 9600"
    Driver        "ati"
##    BusID        "PCI:0:16:0"
    Option        "DynamicClocks" "true"
    Option        "AGPMode" "4"
    Option        "AGPFastWrite" "true"
    Option        "UseFBDev" "false"
    Option        "DRI" "true"
    Option        "GARTSize" "64"
    Option        "AddARGBGLXVisuals" "true"
    Option        "XAANoOffscreenPixmaps"
    Option        "DisableGLXRootClipping" "true"
    Option        "AllowGLXWithComposite" "true"
    Option        "EnablePageFlip" "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Radeon 9600"
    Monitor        "Configured Monitor"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
EndSection

Section "DRI"
    Mode 0666
EndSection

Section "Extensions"
    Option        "Composite" "Enable"
EndSection


Using sudo vi /etc/X11/xorg.conf and paste this into it, save it :wq! and you are done. reboot, enjoy.

Linux buckaroo-laptop 2.6.35-22-powerpc #35-Ubuntu Sat Oct 16 20:02:52 UTC 2010 ppc GNU/Linux

---

### Post by linuxopjemac on 2010-11-19
People can download it here, much easier than copy and paste:
[http://mac.linux.be/content/xorgconf-ppc-machines-radeon-9600-and-kms-kernel-lucid-lynx](http://mac.linux.be/content/xorgconf-ppc-machines-radeon-9600-and-kms-kernel-lucid-lynx)

---

