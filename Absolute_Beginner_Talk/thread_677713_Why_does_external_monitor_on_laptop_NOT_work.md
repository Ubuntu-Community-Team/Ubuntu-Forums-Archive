---
title: "Why does external monitor on laptop NOT work??"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by johann_p on 2008-01-25
I am using Ubuntu Gutsy on a IBM ThinkPad T60 and I have used the Administration->Screen and Graphics dialog to  enable a second monitor. The dialog shows Screen 1 as LCD Panel 1024x768 and "default screen" and Screen  2 as LCD Panel 1280x1024 and secondary screen, mirror default screen.

The problem is this: when I start Ubuntu without the external monitor being connected, I cannot enable the external monitor. If i press the test button, the external monitor shows the test pattern together with the laptop screen.

But if I press OK to keep that configuration the external monitor goes black again.

Only if I boot the laptop with the external monitor connected, I get the desired picture there.

This is very bad, because I would need to use the laptop for a presentation with a beamer and I do not have the time to boot after connecting the laptop to the beamer ... 

I need to enable the external monitor before I connect it or at least at the time when I connect it.

Why doesnt that work as expected? And why do I just see the test pattern but nothing else?????

---

### Post by Thanoulis on 2008-01-25
You do not have to restart the compurer only the X server....press Ctrl+Alt+Backspace and log in again...i think it will work...

---

### Post by johann_p on 2008-01-25
> **Thanoulis said:**
> You do not have to restart the compurer only the X server....press Ctrl+Alt+Backspace and log in again...i think it will work...
Yes, you are right -- that is an improvement!

But is it also possible to avoid restarting X? Connecting the cable, restarting X, logging in, and starting up the programs needed for the presentation still takes a lot of time and wouldn't look that interesting for the audience.

---

### Post by insane_alien on 2008-01-25
wait for hardy, with the new Xserver it should be able to handle that. The feature will come.

---

### Post by johann_p on 2008-01-25
> **insane_alien said:**
> wait for hardy, with the new Xserver it should be able to handle that. The feature will come.
I'd love to wait, but my presentation was 2 hours ago :grin:

Anyways, this is obviously even more broken than it originally looked like: I tested this by connecting my home computer's LCD monitor and I was able to actually mirror what I had on my laptop's LCD on the LCD monitor, both with resolution 1024x768 (or even 1280x1024 on the external monitor) after restarting the X server. 

However when I did exactly the same with the beamer, Ubuntu showed a warning about operating in low resolution mode and switched both the LCD and the external device (beamer) to 640x480. That got me some laughs from the audience and other presenters who had no problem doing 1280x1024 on the beamer with their Windows machines. 
I actually gave up and did the presentation in 640x480 but that was not really fun.

I think it is little things like this which make it hard for Linux to really become successful as a mainstream OS -- not everyone is as much as a masochist as I obviously am.

---

### Post by robmacg on 2008-02-06
I have a very similar problem on my Thinkpad T60 (ATI graphics card, using the fglrx driver). 

Firstly - I have to restart X to get the projector (beamer) to be active at all. It seems that the Function-F7 key to activate an external monitor is not implemented (I've looked at KeyTouch, but that does not list it as a possible combination).

Then - I get the message saying that X has hit an error and will operate in low resolution mode. This dialog allows you to set the resolution, but the only option available is 1400x1050 at 61Hz (this is the resolution of my laptop screen).

The system then comes up at 1400x1050, with the projector active. However, most projectors are very unhappy at such a high resolution, so I go to change it to 1024x768. BUT, the Screen Resolution option under Preferences gives me only 1400x1050!

On investigating a bit more, it seems the fglrx driver is crashing during startup and that is what drives the system into the weird "low resolution mode" thing. The Xorg.9.log file shows this failure and a backtrace. I've copied the end of the log below. This looks like an fglrx bug - can anyone suggest how to pursue it further?

Here is the tail of Xorg.9.log:

[FONT="Courier New"]
(II) fglrx(0): EDID (in hex):
(II) fglrx(0):  00ffffffffffff0030ae224000000000
(II) fglrx(0):  15110103801d1578ea6f959c544c8726
(II) fglrx(0):  21505400000001010101010101010101
(II) fglrx(0):  010101010101302a7820511a10403070
(II) fglrx(0):  13001fd71000001825237820511a1040
(II) fglrx(0):  307013001fd7100000180000000f0090
(II) fglrx(0):  43329043280f010030640055000000fe
(II) fglrx(0):  004c5444313431454e39420a20200004
(II) fglrx(0): End of Display2 EDID data --------------------
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Secondary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000008
(II) fglrx(0): POWERplay version 3.  5 power states available:
(II) fglrx(0):   1. 446/351MHz @ 60Hz [enable load balancing]
(II) fglrx(0):   2. 128/135MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):   3. 209/135MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):   4. 324/135MHz @ 60Hz [enable sleep]
(II) fglrx(0):   5. 398/351MHz @ 60Hz [enable sleep, thermal diode mode]
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 2
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(**) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 6 modes found for primary display.
(--) fglrx(0): Virtual size is 640x480 (pitch 0)
(**) fglrx(0): *Mode "640x480@60": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480@60"  108.00  640 1448 1560 1688  480 1051 1054 1066 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"  108.00  640 1448 1560 1688  400 1051 1054 1066 +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"  108.00  512 1448 1560 1688  384 1051 1054 1066 +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"  108.00  400 1448 1560 1688  300 1051 1054 1066 +hsync +vsync
(**) fglrx(0):  Default mode "320x240": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"  108.00  320 1448 1560 1688  240 1051 1054 1066 +hsync +vsync
(**) fglrx(0):  Default mode "320x200": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"  108.00  320 1448 1560 1688  200 1051 1054 1066 +hsync +vsync

Backtrace:
0: /usr/X11R6/bin/Xorg(xf86SigHandler+0x81) [0x80c95d1]
1: [0xffffe420]
2: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0xb7a1e064]
3: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxPreInit+0x988) [0xb7a18a48]
4: /usr/X11R6/bin/Xorg(InitOutput+0x9a4) [0x80a8ea4]
5: /usr/X11R6/bin/Xorg(main+0x27b) [0x8076ceb]
6: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7dfe050]
7: /usr/X11R6/bin/Xorg(FontFileCompleteXLFD+0x1e1) [0x8076241]

Fatal server error:
Caught signal 11.  Server aborting

[/FONT]

---

