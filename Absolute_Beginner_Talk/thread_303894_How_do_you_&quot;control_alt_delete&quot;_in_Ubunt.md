---
title: "How do you &quot;control alt delete&quot; in Ubuntu, when it freezes?"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by snik on 2006-11-21
My Ubuntu is Edgy Eft 6.10

While browsing through screensaver options I chose to preview "molecule" which caused my system to freeze. I could not close the screensaver preferences window and also could not open or close any other application.

I rebooted the first time the problem occurred. Then tried to undo the "molecule" choice, but now every time I open System-->Preferences-->Screensaver my computer hangs.

Attempted to change screensaver five times, system froze all five times.

I just keep hitting the power button on my computer to restart. What is the Ubuntu version of cntrl-alt-del? 

What is the best way to figure out what is causing the problem. I typed the "cd /var/crash" and then typed in "ls" but no files are listed. 

I got "cd /var/crash" thing from googling. Still learning the linux syntax. Am I doing it wrong?

---

### Post by ctrlcctrlv on 2006-11-21
Well, it sounds like you dont have the appropriate graphics drivers installed..at least that was my problem when my Dapper install locked. After i installed the orrect graphics drivers for my video card the problem went away...

for some reason "ctrl alt backspace" ends a session on my Dapper install. it is possible that this is not always the case.

---

### Post by rlozano on 2006-11-21
> **snik said:**
> My Ubuntu is Edgy Eft 6.10

While browsing through screensaver options I chose to preview "molecule" which caused my system to freeze. I could not close the screensaver preferences window and also could not open or close any other application.

I rebooted the first time the problem occurred. Then tried to undo the "molecule" choice, but now every time I open System-->Preferences-->Screensaver my computer hangs.

Attempted to change screensaver five times, system froze all five times.

I just keep hitting the power button on my computer to restart. What is the Ubuntu version of cntrl-alt-del? 

What is the best way to figure out what is causing the problem. I typed the "cd /var/crash" and then typed in "ls" but no files are listed. 

I got "cd /var/crash" thing from googling. Still learning the linux syntax. Am I doing it wrong?


what do you have with lspci -v? and maybe worthwhile posting your xorg.conf also..

---

### Post by TheTux on 2006-11-21
There is no Alt+Ctrl+Delete in Ubuntu but you can create the shortcut. If you use metacity you can run gconf-editor and go to apps>metacity>keybinding_commands. Then add gnome-system-monitor to one of the blank key. Let say you put that on command_9. Then go to apps>metacity>global_keybindings and put <Control><Alt>Delete into run_command_9. Hope this help.

---

### Post by David Corrales on 2006-11-21
As ctrlcctrlv pointed out, the combination **ctrl+alt+backspace** kills the X server process (which gets automatically restarted by gdm) so you're able to boot back in case of a hard lock.

---

### Post by doclivingston on 2006-11-21
> **ctrlcctrlv said:**
> for some reason "ctrl alt backspace" ends a session on my Dapper install. it is possible that this is not always the case.

Control-Alt-Backspace is X's "magiczap" key combo, which basically tells X to abort (and then it will be reloaded).

---

### Post by snik on 2006-11-21
> what do you have with lspci -v? and maybe worthwhile posting your xorg.conf also..

```
lspci -v
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
        Flags: bus master, fast devsel, latency 0
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: ff800000-ff8fffff
        Prefetchable memory behind bridge: ee900000-f69fffff

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: ff900000-ff9fffff
        Prefetchable memory behind bridge: f6a00000-f6afffff

00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 02) (prog-if 80 [Master])
        Subsystem: Intel Corporation Unknown device 4541
        Flags: bus master, medium devsel, latency 0
        I/O ports at ffa0 [size=16]

00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 02) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation Unknown device 4541
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at ef80 [size=32]

00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 02)
        Subsystem: Intel Corporation Unknown device 4541
        Flags: medium devsel, IRQ 9
        I/O ports at efa0 [size=16]

01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Unknown device 0404
        Flags: bus master, stepping, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at f0000000 (32-bit, prefetchable) [size=64M]
        I/O ports at c800 [size=256]
        Memory at ff8fc000 (32-bit, non-prefetchable) [size=16K]
        Expansion ROM at ff8c0000 [disabled] [size=128K]
        Capabilities: <access denied>

02:0c.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
        Subsystem: Creative Labs CT4780 SBLive! Value
        Flags: bus master, medium devsel, latency 64, IRQ 9
        I/O ports at df80 [size=32]
        Capabilities: <access denied>

02:0c.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07)
        Subsystem: Creative Labs Gameport Joystick
        Flags: bus master, medium devsel, latency 64
        I/O ports at dff0 [size=8]
        Capabilities: <access denied>

02:0d.0 Communication controller: Conexant HCF 56k Data/Fax/Voice/Spkp Modem (rev 08)
        Subsystem: GVC Corporation Dell Titanium
        Flags: bus master, medium devsel, latency 64, IRQ 3
        Memory at ff9f0000 (32-bit, non-prefetchable) [size=64K]
        I/O ports at dfe0 [size=8]
        Capabilities: <access denied>
```

```


/$ cat /etc/X11/xorg.conf
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
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
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Rage 128 PF/PRO AGP 4x TMDS"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "DELL E770s"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Rage 128 PF/PRO AGP 4x TMDS"
        Monitor         "DELL E770s"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection
```

I hope this is what you requested. But I wonder if it is my computer and or system setting that is the cause of the problem. All the other screensaver previews worked. I was methodically  trying each one (trying to find the right one) and got all the way to "M" for "molecule". And there were some other screensaver options that to a layman's eye looked fairly complicated. And they all worked. 

(Could some kind soul tell me if the "molecule" screensaver preview is working on their computer?)

Thanks rlozano

Thanks also ctrlcctrlv & Tux for the info.

---

### Post by CatKiller on 2006-11-21
> **snik said:**
> I rebooted the first time the problem occurred. Then tried to undo the "molecule" choice, but now every time I open System-->Preferences-->Screensaver my computer hangs.

**gconf-editor**
/apps/gnome-screensaver/themes

if you'd like to stop using molecule for a bit.

---

### Post by snik on 2006-11-21
Thank you Catkiller. Thank you! :D 

I was just about to reinstall Ubuntu. It's a two day old installation. Other than adding the flash plug-in, the system is as fresh out of the box. The install only took me about 35 mins. I figured why not re-install rather than spend 90 mins trying to figure out a solution. This is what happens when Ubuntu makes the install process too easy : )

Here is what kept happening, since I could not change the screensaver, when I was away from the computer for ten minutes, the system would try to launch "molecule" screensaver, fail, and then hang -- and then I had to restart. (For some reason ctrl-alt-backspace was not working for me. I wonder if pressing "ctrl-alt-backspace" launches a dialog window asking you to confirm,  if you want to restart, which I can't see, because my system & monitor freeze?)

And I didn't know how else to change the theme. I was just about to reinstall when I thought I would check the thread again. I used gconf-editor, problem solved in 5 secs. On top of that I learned what gconf-editor is.

---

### Post by Mimsy on 2006-11-21
> **snik said:**
>  (For some reason ctrl-alt-backspace was not working for me. I wonder if pressing "ctrl-alt-backspace" launches a dialog window asking you to confirm,  if you want to restart, which I can't see, because my system & monitor freeze?)


No, it doesn't. It is an immedate and instant restart. It takes you straight to the log-in screen and lets you start a new session from there. I use it a lot, since for some reason my Ubuntu-install has started to freeze up nearly as often as my WinXP computer does. 

/Mimsy

---

### Post by snik on 2006-11-21
> No, it doesn't. It is an immedate and instant restart.

Yup! I just found out it does work. 

But it works (now) when my system is working ok in the first place. But it didn't when my screensaver caused my computer to hang. I guess the screensaver glitch was a rather severe glitch that even ctrl-alt-backspace wouldn't work.

---

### Post by 900i on 2006-11-21
If your system completely locks-up and CTRL+ALT+BACKSPACE and others have no effect, there is the get out of jail free keycombo of ALT+PRINTSCRN+S to sync your disks, followed by ALT+PRINTSCRN+U to unmount your disks then ALT+PRINTSCRN+B to reboot.  Or as I prefer ALT+PRINTSCRN+SUB.

---

### Post by P_Badger on 2006-11-21
Nobody seems to have mentioned that you can download a 3rd party application through Automatix called "Ctrl-Alt-Del" in the "Utilities" section. Made the move from windoze all the more pleasant.

---

### Post by CatKiller on 2006-11-21
> **Mimsy said:**
> No, it doesn't. It is an immedate and instant restart. It takes you straight to the log-in screen and lets you start a new session from there.

The problem comes with the severity of the problem. You've obviously got some problems if you need to restart X. But X handles the keyboard and mouse, as well as the screen, so if your X is **really** broken, then your keyboard won't work enough to kill X.

Sometimes you can still SSH in from another computer and fix things remotely though, which is kinda cool.

---

### Post by bonzini on 2006-11-22
As for this freezing in Ubuntu, I have the disease now too.  Here is what I notice.

I'll be doing something, maybe gmail.  And all of a sudden, nothing.  No moving mouse pointer, nada.  ctrl-alt-backspace?  No way.  Only the big red button (OK it's chrome on my Toshiba).

This is apparently a new feature of the Breezy installation I did just after it was released.  I never had this problem with Dapper nor Breezy.

I am currently using the ati driver following the "Radeon" configuration instructions on the Ubuntu wiki, but I had the same problem with fglrx (plus fglrx did not want to do direct rendering with my particular ATI chipset).

Nothing obvious in the log files.  Here's my lspci.

> clh@dabuntu:~$ sudo lspci -v
Password:
00:00.0 Host bridge: ATI Technologies Inc RS300 Host Bridge (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 64
        Memory at d2000000 (32-bit, prefetchable) [size=32M]
        Memory at d0000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [a0] AGP version 3.0

00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 99
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: d0100000-d01fffff
        Prefetchable memory behind bridge: e0000000-efffffff

00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 193
        Memory at d0001000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 193
        Memory at d0002000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 193
        Memory at d0003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2

00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 18)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: 66MHz, medium devsel
        I/O ports at 8060 [size=16]
        Memory at d0004000 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc ATI Dual Channel Bus Master PCI IDE Controller (prog-if 8a [Master SecP PriP])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 64, IRQ 177
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at 8070 [size=16]

00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4342 (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=02, subordinate=04, sec-latency=168
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: d0200000-d02fffff
        Prefetchable memory behind bridge: 50000000-51ffffff

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
        Subsystem: Toshiba America Info Systems Unknown device ff01
        Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 185
        Memory at d0004400 (32-bit, non-prefetchable) [size=256]

00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01) (prog-if 00 [Generic])
        Subsystem: Toshiba America Info Systems Unknown device 0001
        Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 185
        Memory at d0004800 (32-bit, non-prefetchable) [size=256]

01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP] (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems Unknown device ff02
        Flags: bus master, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 177
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 9000 [size=256]
        Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at d0120000 [disabled] [size=128K]
        Capabilities: [58] AGP version 3.0
        Capabilities: [50] Power Management version 2

02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 64, IRQ 177
        Memory at d0214000 (32-bit, non-prefetchable) [size=2K]
        Memory at d0210000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2

02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: Askey Computer Corp. Unknown device 7065
        Flags: bus master, medium devsel, latency 168, IRQ 201
        Memory at d0200000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2

02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 128, IRQ 193
        I/O ports at a000 [size=256]
        Memory at d0214800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

02:04.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller
        Subsystem: Toshiba America Info Systems Unknown device ff01
        Flags: bus master, medium devsel, latency 168, IRQ 177
        Memory at d0216000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=03, sec-latency=176
        Memory window 0: 50000000-51fff000 (prefetchable)
        Memory window 1: 52000000-53fff000
        I/O window 0: 0000a400-0000a4ff
        I/O window 1: 0000a800-0000a8ff
        16-bit legacy interface ports at 0001

02:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at d0214c00 (32-bit, non-prefetchable) [size=128]
        Capabilities: [80] Power Management version 2

02:04.2 Class 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (prog-if 01)
        Subsystem: Toshiba America Info Systems Unknown device ff01
        Flags: bus master, medium devsel, latency 64, IRQ 185
        Memory at d0215000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

02:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc:
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at d0215400 (32-bit, non-prefetchable) [size=128]
        Capabilities: [80] Power Management version 2

clh@dabuntu:~$ 

Anyone having a similar problem?

---

### Post by Delkster on 2006-11-22
> **900i said:**
> If your system completely locks-up and CTRL+ALT+BACKSPACE and others have no effect, there is the get out of jail free keycombo of ALT+PRINTSCRN+S to sync your disks, followed by ALT+PRINTSCRN+U to unmount your disks then ALT+PRINTSCRN+B to reboot.  Or as I prefer ALT+PRINTSCRN+SUB.

There's also Alt+PrintScrn+K for killing all processes in the current terminal. That's a more forcible way of killing (and restarting) X than Ctrl+Alt+Backspace but you may get something back without rebooting immediately.

Anyway, like others have said, if you need to do that, something's wrong.

---

### Post by Tzumli_D on 2006-12-10
Following on from this, I have a different problem when I am scrolling through the screensavers trying to work out how to have them change.
Some of the screensavers preview nicely, but others cause the system to reboot.
I only discovered this issue because Edgy, unlike Ubuntu Dapper, does not automatically launch the screen saver, and I was trying to get it going, slowly scrolling through all the screensavers available.
Now I'm unsure whether that is such a good idea if the preveiws are causing my system to reboot.
Denise

---

### Post by Delkster on 2006-12-12
> **Tzumli_D said:**
> Some of the screensavers preview nicely, but others cause the system to reboot.

Do these happen to be the fancy 3D ones? If they are, it may be that something's wrong with 3D acceleration.

---

### Post by Swedtony on 2007-03-03
Hi,
   Exactly the same happened to me as I did my first browse thru Ubuntu. Feels like windows already!
I was trying to learn about the gconfig stuff but not skilled enough yet( bit clueless so far, idea was to browse what I had then learn!!). **I went into screen saver again and just quickly clicked on the next in the list and it continued on ok**. I have an older computer to experiment on. I have a lot to read and learn but I like the feel of Ubuntu so far (barring the molecule screensaver)
Tony

---

### Post by steve101101 on 2007-03-03
control alt backspace

---

### Post by raul_ on 2007-03-03
> **P_Badger said:**
> Nobody seems to have mentioned that you can download a 3rd party application through Automatix called "Ctrl-Alt-Del" in the "Utilities" section. Made the move from windoze all the more pleasant.

It's not an application. It's just a script that adds the binding to metacity. If you use Beryl this script won't work, but it's very easy to add keybindings to Beryl.

Anyway, i don't like to use ctrl+alt+backspace. When possible (sometimes it's a complete lock up) i like to change to a terminal (ctrl+alt+f1) and kill the process that it's locked up and then return to my desktop with ctrl+alt+f7.

That alt+printscreen is actually good, but when i use it, i use the full RSEIUB combination (Raising Skinny Elephants Is Utterly Boring). You can find a thread about it here in the forums

---

### Post by Loner_Tech on 2007-03-03
> **snik said:**
> My Ubuntu is Edgy Eft 6.10

While browsing through screensaver options I chose to preview "molecule" which caused my system to freeze. I could not close the screensaver preferences window and also could not open or close any other application.

I rebooted the first time the problem occurred. Then tried to undo the "molecule" choice, but now every time I open System-->Preferences-->Screensaver my computer hangs.

Attempted to change screensaver five times, system froze all five times.

I just keep hitting the power button on my computer to restart. What is the Ubuntu version of cntrl-alt-del? 

What is the best way to figure out what is causing the problem. I typed the "cd /var/crash" and then typed in "ls" but no files are listed. 

I got "cd /var/crash" thing from googling. Still learning the linux syntax. Am I doing it wrong?


I think u shud try some alternate desktop environment like flxubox or enlightenment which are liter than gnome u may try kde also

---

