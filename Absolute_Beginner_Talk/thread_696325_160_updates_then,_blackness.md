---
title: "160 updates then, blackness"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by ecs_pf5 on 2008-02-13
I have:

1 x SATA HDD with 5 partitions which I think run like this:

1. Windows XP NTFS
2. Vista 64-bit NTFS
3. Vista 32-bit NTFS
4. Ubuntu feisty ext3 (comes up as sda5) (active partition)
5. Ubuntu swap ext3(?)

I have an ATI Radeon video card, boo hiss.

Normally when it boots, it first loads grub, then gives me a menu to boot into various ubuntus, or else move on to a windows loader which presents a second menu for booting the windows stuff.

I recently fired up into Ubuntu after a few months break.

I noticed the screen was wrong, because I threw out my old monitor and bought another. Old monitor was FPD1960 lcd with a max res of 1024x768, new one is HPw2207 which is 1680x1050.

Couldn't change the res that high through the GUI, so I edited etc/X11/xorg.conf, and added 1680x1050 at the 'top' of all the mode lines.

Rebooted & the GUI let me go that high then. Screen came up crisp & proper at the right resolution.

Then noticed, it wanted to install 160 updates. So, I let it. Rebooted again after downloading, when prompted, and now it won't boot.

It only shows the very first part of the booting text, then the monitor just goes black.

I can get into sda5 and edit stuff okay using an old knoppix disk I have, but otherwise pretty foxed right now, any pointers gratefully received. Thanks.

I'll post back with the exact point at which the boot fails..

----

okay it says 'Starting up' at the top of the screen, then something like '...Kernel...  ...Mapping tables...  ...(strings of numbers)...' flashes by really quick at the bottom of the screen, and then that's it, you see no more. Monitor goes pitch 'switched off at the plug' black, and doesn't come back again. 

Tried waiting a bit then trying to login 'blind' whilst listening for disk activity, not a sausage.





IF it's likey to be easier to reinstall (I have a md5-checked & verified copy of the alternate gutsy CD here), that's fine, but I'm worried about losing my grub boot setup - need to be able to reinstall without losing ability to boot into the windows loaders.

---

### Post by glennric on 2008-02-13
Have you added any vga=??? options to your kernel boot parameters?

---

### Post by emarkd on 2008-02-13
Can you get to a terminal, maybe <ctrl><alt>F1?  Then reconfigure your xserver

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then restart X:

```
sudo /etc/init.d/gdm restart
```

Maybe?

---

### Post by asmoore82 on 2008-02-13
**IF** the linux system is booted properly, you could simply **Ctrl+Alt+F1**
to get to a console login and fix your setup from there.

This type of thing is to be expected if you manually installed Graphics drivers outside of the
Ubuntu package management system, either manually or by 3rd party "helper" Apps.

---

### Post by ecs_pf5 on 2008-02-13
Thanks folks

> 
        Have you added any vga=??? options to your kernel boot parameters?
No, not intentionally myself.

Will go try the ctrl-alt-f1..

I'm posting my /boot/grub/menu.lst and /etc/X11/xorg.conf for ref:

menu.lst (commented defaults removed for brevity)
```


default        0

timeout        10

title        Ubuntu, kernel 2.6.20-16-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=6b9802a0-b3e3-460e-96b1-32a3eb95de1f ro quiet splash
initrd        /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=6b9802a0-b3e3-460e-96b1-32a3eb95de1f ro single
initrd        /boot/initrd.img-2.6.20-16-generic

title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=6b9802a0-b3e3-460e-96b1-32a3eb95de1f ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=6b9802a0-b3e3-460e-96b1-32a3eb95de1f ro single
initrd        /boot/initrd.img-2.6.20-15-generic

title        Ubuntu, memtest86+
root        (hd0,4)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1

```xorg.conf
```

Section "Files"
    FontPath    "/usr/share/fonts/X11/misc"
    FontPath    "/usr/share/fonts/X11/cyrillic"
    FontPath    "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/Type1"
    FontPath    "/usr/share/fonts/X11/100dpi"
    FontPath    "/usr/share/fonts/X11/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load    "bitmap"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "vbe"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "gb"
    Option        "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "Device"
    Identifier    "ATI Technologies Inc RV410 [Radeon X700]"
        Driver                "ATI"
        BusID                "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
        Option "AGPMode" "4"
        Option "AGPFastWrite" "true"
        Option "DisableGLXRootClipping" "true"
        Option "AddARGBGLXVisuals" "true"
        Option "AllowGLXWithComposite" "true"
        Option "EnablePageFlip" "true"
EndSection

Section "Monitor"
    Identifier    "FPD1960"
    Option        "DPMS"
    HorizSync    30-70
    VertRefresh    50-160
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies Inc RV410 [Radeon X700]"
    Monitor        "FPD1960"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
        Option          "AIGLX" "true"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

```

(I removed the extra resolutions that I'd previously added to the mode lines, it made no difference either way)

---

### Post by ecs_pf5 on 2008-02-13
No joy with ctrl-alt-f1 :(

---

### Post by asmoore82 on 2008-02-13
try choosing this option from your boot menu, I'm guessing it would be the 3rd one:
```
Ubuntu, kernel 2.6.20-15-generic
```
if that one doesn't boot up fully either,
highlight the first one and press 'e'
then highlight the "kernel" line and press 'e'
then, delete "quiet splash" from the end of the line and press 'enter'
then, press 'b' to boot with the modified options;
that way, you can at least read exactly what's going on.

---

### Post by ecs_pf5 on 2008-02-14
First suggestion failed, it went to blackness as usual.

Second suggestion

> 
highlight the first one and press 'e'
 then highlight the "kernel" line and press 'e'
 then, delete "quiet splash" from the end of the line and press 'enter'
 then, press 'b' to boot with the modified options;
Did work. 

It led me to a corrupted-looking blue text screen (similar to the installer screens) that said, 'Failed to start the X server'.

It then led on to give a screen of version info before saying 'X server now disabled' 'restart GDM when configured correctly'.

Then dumped me at a working command prompt.

So now I can try and reconfigure the X server. I am going to try 'Envy'.

[edit] Envy did not work. But then again I could never get my ATI Radeon 700 working properly using the 'normal' instructions. I then looked in /etc/X11/xorg.conf & noticed it had given itself the driver "ATI",,,,,, changed that to "fglrx"    and all working again.

---

