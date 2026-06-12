---
title: "Radeon 9200 driver help, please."
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by Zilliano on 2007-08-20
Okay, beings that no threads I've found have to same card or problems as me, I'm making my own.
Please, keep it simple. I just changed from windows, and I'm a TOTAL beginner.
I have a Radeon 9200. Not Pro, or Mobility, or SE. JUST 9200.
I read somewhere that the radeon driver in Ubuntu would work, but the problem is,
It's 
Not
On
the
freggin'
list.
Ugh.
No, the ati driver doesn't work. Neither does fglrx. Vesa is the only on I can get to work. Hell, I can't even boot the live disc normally. I have to use safe graphics mode. Can SOMEONE help me get this set up so I can enable 3d support n' all?All I want is desktop effects, and maybe beryl.

---

### Post by Zilliano on 2007-08-20
Also, if it matters, My xorg.conf doesn't list my video card as ATI Radeon etc, it just say 'Generic Video Card' or something to that effect.

---

### Post by zamolxis on 2007-08-20
I have a 9600XT AIW, and couldn't get it to work with either Compiz or Beryl. The following posts should give you an idea of what you are up against, also providing some other links you might find useful:

[http://ubuntuforums.org/showthread.php?t=372316](http://ubuntuforums.org/showthread.php?t=372316)

ATI cards are notoriously unsupported, despite what ATI says. I have another system with less memory and a supposedly less powerful nVidia card and compiz worked like a charm, no problem whatsoever!

---

### Post by Zilliano on 2007-08-20
Stiil, could I get an answer why the radeon driver does show up when I run the command to reconfigure xorg? It was there at one time, but I've had to reinstall since then but now I can't find it. Does it need to be downloaded or something? I think I found the files for it using search, but it's just not on the list of drives to choose from. Any suggestions?

---

### Post by w4ett on 2007-08-20
Please do the following....from the terminal (or command line) type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

select 'vesa' as the video drive then selct your desired resolutions....Save, then type:

```
startx
```

THEN from the terminal type:

```
lspci
```

paste the results here in the forum so we can have a look.

Also is your 9200 an AGP card or PCI???

also what MOBO are you using?

---

### Post by w4ett on 2007-08-20
> **Zilliano said:**
> Stiil, could I get an answer why the radeon driver does show up when I run the command to reconfigure xorg? It was there at one time, but I've had to reinstall since then but now I can't find it. Does it need to be downloaded or something? I think I found the files for it using search, but it's just not on the list of drives to choose from. Any suggestions?

Radeon is the OLD name for the open source xorg-driver-ati.....the 'ati' driver is the one you should be using....flgrx only work in Ubuntu with the 9500 cards and above.

---

### Post by gary0 on 2007-08-20
I have a Radeon 9200 and it worked straight out of the box.Just installed Ubuntu, and it worked - really, beryl and all.

here is the relevant part of xorg.conf:-

Section "Device"
	Identifier	"ATI Technologies Inc RV280 [Radeon 9200 SE]"
	Driver		"ati"
	BusID		"PCI:0:9:0"
EndSection

At the terminal do:

sudo  gedit /etc/X11/xorg.conf

Hope this helps
Gary.

---

### Post by Zilliano on 2007-08-20
Oh, sorry, it's PCI. I'll go and get those result for you now, but I have Ooooone more thing I wanna try before I do that. Anyways, I'll be back with those within the hour.

Oh, and, um........MOBO? I don't really know what that is......eheh ^^;

---

### Post by w4ett on 2007-08-20
MOBO=Motherboard  :)

---

### Post by gary0 on 2007-08-20
-.-. --.- -.. -..-

w4ett de --. --... .-. ...

---

### Post by Zilliano on 2007-08-20
> **gary0 said:**
> I have a Radeon 9200 and it worked straight out of the box.Just installed Ubuntu, and it worked - really, beryl and all.

here is the relevant part of xorg.conf:-

Section "Device"
	Identifier	"ATI Technologies Inc RV280 [Radeon 9200 SE]"
	Driver		"ati"
	BusID		"PCI:0:9:0"
EndSection

At the terminal do:

sudo  gedit /etc/X11/xorg.conf

Hope this helps
Gary.

Well, I tried, but it didn't work for me. Sorry. Maybe b/c I don't have an SE?

---

### Post by Zilliano on 2007-08-20
Well, My MOBO is a Mach Speed MK8-939A.

Also, here are my results from the lspci command.

00:00.0 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. K8T890 I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. [K8T890 North / VT8237 South] PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.1 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.2 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.3 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:05.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200] (rev 01)
00:05.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200] (Secondary) (rev 01)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

---

### Post by w4ett on 2007-08-20
> **Zilliano said:**
> Well, I tried, but it didn't work for me. Sorry. Maybe b/c I don't have an SE?

The SE designations is not going to make any difference.  If you will please type in the terminal:

```
cat /etc/X11/xorg.conf
```

and post the results.

---

### Post by Zilliano on 2007-08-20
Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
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
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:0:5:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

Btw, If I didn't mention it, vesa is the only driver (that I've tried) that will actually work right now. The rest (ati, fglrx) reboot to a black screen.

---

### Post by w4ett on 2007-08-20
Yeah, the xorg-driver-ati is SUPPOSED to be the proper one for your card BUT I been reading about your particular GPU (the RV280 in PCI form) and several people have had problems with the same issues as you see:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/114520](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/114520)

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/128421](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/128421)

Both of these problems/bugs affect the same GPU series chipsets as the one in your card and even though are not the same, they seem to be related to your problem.

I suspect that you motherboard and videocard combo has something to do with it as well.   I also use an ATI 9200 based card, and have had problems with via based motherboards with this card in Ubuntu..

Please file a bug in Launchpad and see if the xorg devs can help out a bit on this one.

---

