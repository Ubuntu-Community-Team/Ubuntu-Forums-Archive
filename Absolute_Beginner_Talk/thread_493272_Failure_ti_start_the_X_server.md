---
title: "Failure ti start the X server?"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by snwbord2456 on 2007-07-05
After installing Ubuntu on my Dell Inspiron E1505 using the text installer because I have an ATI X1400 the Unbuntu Screen came up after saying the computer needed to reboot. After going to the Unbuntu screen with the load bar it goes to a command line interface and then quickly to an error screen saying: 

Failed to start the X server (your graphical interface). It is likely that is it not set up correctly. Would you like to view the X server output to diagnose the problem? 

I checked all the resolutions below 1680 and the output says:

X Window System Version 1.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.1
Build Operating System: Linux Ubuntu
Current Operating System: Linux Mark 2.6.20-15-generic #2 SMP Sun Apr
15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
          Before reportingf problems, check [http://wiki.x.org](http://wiki.x.org)
          to make sure that you have the latest version.
Module Loader Present.
Markers: ( -- ) probed, ( ** ) from config file, (==) default setting,
              (++) from command line, (!!) notice, (II) informational,
              (WW) warning, (EE) error, (NI_ not implemented, (??) ubnknown.
(==) Log File: "/var/log/Xorg.0.log". Time: Thu Jul 5 11:29:57 2007
(==) Using config file: "/etc/X11/xorg.conf"
                                                                        .2
acktrace:                                           tu
0: /usr/X11R6/bin/X(xf86SigHandler+0x81) [0X80c5d91]                           pr
e: [0xffffe420]                   86
2: /usr/X11R6/bin/X(InitOutput+0x9aa) [0x80a5b9a]
3: /usr/X11R6/bin/X[main+0x27b) [0x807456b]            rg
4: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7db3ebc]
5: /usr/X11R6/bin/X(FontFileCompleteXFLD+0x1e1) [0x8073ab1]
                                                                                                           g,
Fatal server error:                                                                         l,
Caught signal 11. Server Aborting                                                          n.
                                                                                                                07
Y                                                            f"


Then the advanced config file is:


X Window System Version 1.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.1
Build Operating System: Linux Ubuntu
Current Operating System: Linux Mark 2.6.20-15-generic #2 SMP Sun Apr
15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
          Before reportingf problems, check [http://wiki.x.org](http://wiki.x.org)
          to make sure that you have the latest version.
Module Loader Present.
Markers: ( -- ) probed, ( ** ) from config file, (==) default setting,
              (++) from command line, (!!) notice, (II) informational,
              (WW) warning, (EE) error, (NI_ not implemented, (??) ubnknown.
(==) Log File: "/var/log/Xorg.0.log". Time: Thu Jul 5 11:29:57 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen"  (0)
(**) |    |-->Monitor "Generic Monitor"
(**) |    |-->Device "Generic Video Card"         .2
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"                                               pr
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"                                             rg
(**) |-->Input Device "Synaptics Touchpad"                 n.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
               Entry deleted from path.                                                 g,
(**) FontPath set to:                                                                   l,
             /usr/share/fonts/X11/misc                                                        n.
             /usr/share/fonts/X11/100dpi/ :unscaled                                 07
             /usr/share/fonts/X11/75dpi/ :unscaled,"
             /usr/share/fonts/X11/Type1,
             /usr/share/fonts/X11/100dpi,
             /usr/share/fonts/X11/75dpi,
             /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
             /usr/share/fonts/X11/misc,                                                     pr
             /usr/share/fonts/X11/cyrillic,
             /usr/share/fonts/X11/100dpi/ :unscaled,
             /usr/share/fonts/X11/75dpi/ :unscaled.                     rg
             /usr/share/fonts/X11/Type1,
             /usr/X11R6/lib/X11/fonts/Type1
             /usr/share/fonts/X11/100dpi                                            g,
             /usr/share/fonts/X11/75dpi                                           l,
             /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType                  n.
(==) RgbPath Set to "/etc/X11?rgb"                                                  07
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI Successful (/var/run/acpid.socket)
(II) Loader magic: 0881c92e0
(II) Module ABI Versions:
             X.Org ANSI C Emulation: 0.3
             X.Org Video Driver: 1.1
             X.Org Xinput driver : 0.7                                                        pr
             X.Org Server Extension : 0.3
             X. Org Font Renderer : 0.5
(II) Loader running on lnux                           rg
(II) LoadModule: "pcidata"                        n.
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: verndor= "X.Org Foundation"                    g,
             compiled for 7.2.0, module version = 1.0.0               l,
             ABI class: X.Org Video Driver, Version 1.1                           n.
(++_ Using VT number 7                                                                  07


theres a ton more...and i dont feel if i can type it right now. Down at the bottom though it does say 

(II) VESA(0) : Not unsin built-in mode "1400X1050: (no mode of this name)


Hopefully some of this helps....eagerly awaiting any help.

---

### Post by Raineer on 2007-07-05
If you could just copy/paste like the last 10 lines that could really help.  You could possibly try to use "[Envy]("http://albertomilone.com/nvidia_scripts1.html")" to install the correct driver for your card.  It isn't supported by Ubuntu official but tons of people use it with lots of luck.

---

### Post by snwbord2456 on 2007-07-05
Yah no problem, I just cant copy and paste though because im on different comps.

(II) VESA(0): Total Memory: 256 64KB banks (16384kB)
(II) VESA(0): Generic Monitor : Using hsync value of 64.80kHz
(II) VESA(0): Generic Monitor : Using vrefresh value of 60.00 Hz
(II) VESA(0): Not Using Mode "1680x1050" (no mode of this name)
(II) VESA(0): Not Using Mode "1600x1200" (no mode of this name)
(II) VESA(0): Not Using Mode "1440x900" (no mode of this name)
(II) VESA(0): Not Using built-in Mode "1400x1050" (no mode of this name)
(II) VESA(0): Not Using Mode "1280x1024" (no mode of this name)
(II) VESA(0): Not Using Mode "1280x960" (no mode of this name)
(II) VESA(0): Not Using Mode "1280x854" (no mode of this name)
(II) VESA(0): Not Using Mode "1280x800" (no mode of this name)
(II) VESA(0): Not Using Mode "1280x768" (no mode of this name)
(II) VESA(0): Not Using Mode "1200x800" (no mode of this name)
(II) VESA(0): Not Using Mode "1152x864" (no mode of this name)
(II) VESA(0): Not Using Mode "1152x864" (no mode of this name)
(II) VESA(0): Not Using Mode "1152x786" (no mode of this name)
(II) VESA(0): Not Using Mode "1024x786" (no mode of this name)
(II) VESA(0): Not Using Mode "800x600" (no mode of this name)
(II) VESA(0): Not Using Mode "640x480" (no mode of this name)
(WW) VESA(0) : No Valid Modes lef. Trying less strict filter...

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x81) [0x80c5d91]
1: [0xffffe420]
2: /usr/X11R6/bin/X(InitOutput+0x9aa) [0x80a5b9a]
3: /usr/X11R6/bin/X(main+0x27b) [0x807456b]
4: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d64ebc]
6: /usr/X11R6/bin/X(FontFileCompleteXFLD=0x1e1) [ 0x8073ab1]

Fatal Server Error:
 Caught signal 11. Server aborting.

Then after pressing okay goes back to the error screen saying:

The X server is now disabled. Restart GDM when it is configured correctly.

Goes back to:


Starting up ...
Loading, please wait...
kinit: name_to_dev_t(/dev/sda5) = sda5(8,5)
kiniti: trying to esume from /dev/sda5
kinit: No resume image, doing normal boot...

Ubuntu 7.04 (user name) ttyl

(username) login:

Thanks

---

### Post by snwbord2456 on 2007-07-05
I figured it out, well in a way. I understand the part now about how Gnome needs to be configured with the ATI card and I'm pretty sure i can figure out how to do this with the howto that is stickied. What I don't have is internet. I'll search the forum pages for wireless configuration, but I hear that is really hard, can anyone give me a nudge in the right direction?

---

