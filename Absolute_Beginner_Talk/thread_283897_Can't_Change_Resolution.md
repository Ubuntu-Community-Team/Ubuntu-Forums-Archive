---
title: "Can't Change Resolution"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by rictus007 on 2006-10-24
OK, I know this thread is popular around here, but it seems that after fallowing all the instruction on other posts I can't still change my monitor resolution.

I need it to be 1024X768 at 60Hz.  My monitor is a Starlogic 15" model MT5BBK.  The video card as you will see next is Intel 82865G.  I don't know if this works but on Knoppix I'm able to have the correct resolution but at  75Hz and the name of the monitor appear to be XHD0000.

Any help will be higly apreciated

Here is my xorg.conf file as I had edit it.
 

Section "Monitor"
        Identifier      "15''"
        Option          "DPMS"
        # V-freq: 60.00 Hz  // h-freq: 47.80 KHz
        Modeline "1024x768" 60.80  1024 1056 1128 1272   768  768  770  796
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82865G Integrated Graphics                           Monitor        "15''"
        DefaultDepth    16
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600"
        EndSubSection
EndSection

---

### Post by taurus on 2006-10-24
What driver do you use for your graphic card?  You can get that info from /etc/X11/xorg.conf.

---

### Post by rictus007 on 2006-10-24
I guess this is what you ask...As far as I know my card is the one described here, but I don't know excatly what is i810

Section "Device"
	Identifier "Intel Corporation 82865G Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

---

### Post by rictus007 on 2007-01-18
Ok...after few months the problem is finally resolved... This is what I do..I find this on this forum and it works :D 

1. First, try a quick fix. It may not work, but if is does you are done.

Code:

sudo dpkg-reconfigure -phigh xserver-xorg

    * The -phigh option selects the defaults for everything but the screen resolution.
    * To select a resolution, use the arrow keys to move up and down, hit the "Space bar" to select/unselect a resolution.
    * You will recieve a message indication your old file was backed up.
      Note: This often shakes the confidence of "noobs", but it is normal. 


[http://ubuntuforums.org/showthread.php?t=269052]("http://ubuntuforums.org/showthread.php?t=269052")

---

