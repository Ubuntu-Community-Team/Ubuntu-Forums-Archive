---
title: "1440x900 resolution adn Hanns-G monitor"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by rgraves on 2006-11-10
I'm a noob to Ubuntu & linux.

I have that Hanns-G HW-191DPB monitor and eVga GeForce 6200 TurboCharge video card.


I'm having trouble getting optimum 1440x900 resolution. I only have three choices 1024x768, 800x600, 640x480. Below is the section from my xorg.cong file.

I've read other posts that say to just add the line "1440x900" on each mode line and also to change "nv" to "nvidia" When I do that and reboot all is screwed up and I have to reinstall.

Any other suggestions.

Thanx,
Bob

Section "Device"
	Identifier	"NVIDIA Corporation NV44 [GeForce 6200 TurboCache]"
	Driver		"nv"
	BusID		"PCI:3:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV44 [GeForce 6200 TurboCache]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

---

### Post by firenurse4 on 2006-11-10
I have the Hanns-G JW199D.  To get the 1400 x 900 resolution, run the following command from the terminal.

sudo dpkg-reconfigure xserver-xorg

It will first go through the video card setup and then ask you about setting up your monitor. You can accept all the defaluts along the way.  It will come up with a screen about your monitors resolution and you need to check the 1400 x 900 setting.

After it writes the new xorg file resart and you should hve that resolution available.

Make sure you back up the xorg.conf file first. ;)

---

### Post by firenurse4 on 2006-11-10
> Section "Device"
Identifier "NVIDIA Corporation NV44 [GeForce 6200 TurboCache]"
Driver "nv"
BusID "PCI:3:0:0"
EndSection

I see that your video card driver is the free one that ships with ubuntu. You can get the nVidia binary driver that will enable video acceleration by using [Automatix]("http://www.getautomatix.com").

---

### Post by tommy1987 on 2006-11-10
I have the same monitor and similar graphics card and I had no end of trouble trying to install it manually, however using Automatix it seems to work a treat!

---

### Post by JayTee on 2006-11-10
You might also need to add a modeline to the Monitor section.
You can get the modeline info by running the following command.
sudo gtf "h-resolution" "v-resolution" "refresh rate" , where you add the horizontal, vertical and refresh rate for your monitor where the items in quotes are. Then you can copy and paste the output into your xorg.conf file. I'm pasting the sections I've had to modify here but your values may differ!!! I have a MAG Innovision 19" widescreen and an eVGA GeForce 6200 LE with 128MB of RAM.
> 
Section "Monitor"
	Identifier	"MAG LT926Wb"
	HorizSync	30-82
	VertRefresh	50-85
	Option		"DPMS"
	Modeline "1440x900_75.00" 136.49  1440 1536 1688 1936  900 901 904 940 -HSync +Vsync
	Modeline "1440x900_60.00" 106.47  1440 1520 1672 1904  900 901 904 932 -HSync +Vsync
	DisplaySize 	1440 900
EndSection

Here is the sreen section of my xorg.conf:
> Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40 [GeForce 6200]"
	Monitor		"MAG LT926Wb"
	Option 		"AddARGBGLXVisuals" "True"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900_75.00" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900_75.00" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900_75.00" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900_75.00" "1440x900_60.00" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900_75.00" "1440x900_60.00" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900_75.00" "1440x900_60.00" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
I had to do a complete restart for this to finally work. Running Ctrl-Alt-Backspace to restart X-server did not update the changes right away as it normally would.

---

### Post by rgraves on 2006-11-10
Thanks to all,

DL'd automatix, installed nvidia driver, then edited xorg.conf file adding modeline and new resolution in all modes. Didn't have to reboot. just ctl-alt-backspace, then startx and all was well.

Below is new section in xorg.conf

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
    Modeline	   "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV44 [GeForce 6200 TurboCache]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV44 [GeForce 6200 TurboCache]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1440x900_60.00" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1440x900_60.00" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1440x900_60.00" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1440x900_60.00" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1440x900_60.00" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1440x900_60.00" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by JayTee on 2006-11-10
Enjoy it!!! Congrats on getting it working.

---

### Post by rgraves on 2006-11-10
Thought all was well. Now when I reboot I get a kernel panic not syncing message and cannot boot into system. 

Not sure what I'm supposed to do at this point. Is the following message a result of my editing the xorg.conf file.  As I said earlier, all was fine when I did the ctl-alt backspace, then startx. But now rebooting seems to fail.

Again help.
Bob

Uncompressing Linux.. Ok, booting the kernel
{17179572.896000] ..MP-BIOS bug: 8245 timer not connected to IO-APIC
[1717952.972000] Kernel panic - not syncing: IO-APIC + timer doesn't work!  Boot with apic=debug and send a report. Then try booting with the 'noapic' option
[17179572.972000]

---

