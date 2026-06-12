---
title: "trying to to make my geforce 6600 mac ppc g5 works with ubuntu 12.04"
date: 2013-03-21
forum: Apple Hardware Users
---

### Post by gusduenas on 2013-03-21
I know that there is a problem with the nvidia driver, able only to work with the ubuntu 2d, altough my bual boot uses 3d acceleration on my leopard...is a 256mb!
Well I've made this experiment yesterday and it went wrong , went awry to be honest.
I did this:
sudo stop lightdm
then the terminal ctrl alt f1
sudo su
sudo Xorg -configure
it results in an error that says that the numbers of screens created doesn not match the number of detected devices.
-turns out I ahve only one monitor- and my nvidia card has double monitor capabilities I guess it has two dvi outputs

sudo start lightdm and back to normal

I took the /root/xorg.conf.new file and I copied to /etc/X11/xorg.conf

but before I erase the extra screen, I guess it was screen one or something.

Problem when I reboot it....it won't pass of the icon loading (ubuntu with the dots)

so after trying to get my way back three times, I end up doing an alternate cd fresh install.

here is my new xorg.con.new that was produced by Xorg

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "extmod"
    Load  "record"
    Load  "dri"
    Load  "dbe"
    Load  "dri2"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "WrappedFB"              # [<bool>]
        #Option     "GLXVBlank"              # [<bool>]
        #Option     "ZaphodHeads"            # <str>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "nouveau"
    BusID       "PCI:10:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # <str>
        #Option     "fbdev"                  # <str>
        #Option     "debug"                  # [<bool>]
    Identifier  "Card1"
    Driver      "fbdev"
    BusID       "PCI:10:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


So what do you think mates? is this ok to put as a xorg.conf or do I need a new one tailored for an nvidia geforce 6600...thanks.

Gus

---

### Post by BenTin2 on 2013-04-05
Hi Gus - so, any luck? I'm in the same boat... late 2005 G5 with Geforce 6600 256mb. I tried both the bleeding-new 13.04 (beta-ish) and 12.10, but 12.04 seems to be the only one that works currently without some major digging - but all of them seem to be plagued by the nouveau driver and lack of proprietary nv drivers for PPC linux. 

If you got a working xorg.conf, I'd love to see it! From what I've been reading, we may have to tackle this from the open-firmware end of things too. Whatever driver we install and intend to use has to be called by the open firmware, no? I think. Well, lemme know if you solved the riddle, and I'll look for a good setup on my own and report back if I find anything.

Do you have an airport card, too? The b43 driver install process seems to work, but no wifi yet.

~Ben

---

### Post by BenTin2 on 2013-04-06
Ok, wifi (airport) is alive, and I think I have my system backed-up, proceeding to monkey with video drivers :guitar:

---

### Post by gusduenas on 2013-05-28
Any success using the xorg.conf or configuring one, let me know.

> **BenTin2 said:**
> Ok, wifi (airport) is alive, and I think I have my system backed-up, proceeding to monkey with video drivers :guitar:

---

### Post by liquidfalcon on 2013-05-29
> **gusduenas said:**
> Any success using the xorg.conf or configuring one, let me know.

This card is an absolute pain even under an x86 based system. Unfortunately due to the age of the NV30 chipset used in this card, it's unlikely we'll see much love from the Nouveau developers in regards to sorting this problem out. Your best bet is to replace this with an off the shelf ATI card as they have fantastic FOSS driver support, or at least an NVIDIA card known to work nicely with Nouveau. Since the 6600 was only found in PCI-E PowerMacs, you should be able to use most all modern video cards. I'm currently using an ATI 6450 which seems to be alright thus far on my G5 Quad.

---

