---
title: "Changing Screen Resolution"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by Stochastic on 2006-11-23
Hi, I'm running 6.06 and I'd like to increase my screen resolution.  I've run ```
sudo dpkg-reconfigure xserver-xorg
``` and it had larger resolutions than my current 1280x768 and I selected them and wrote the changes to file but upon reboot I still only have 1280x768 or lower choices in the settings menu.  I checked the contents of /etc/X11/xorg.conf and they had changed to:

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection


but the menu still has only 1280x768 or smaller.  Any ideas?

---

### Post by JayTee on 2006-11-23
What does the Monitor section of your xorg.conf file say? Here is a sample of how mine looks. 

> Section "Monitor"
	Identifier	"MAG LT926Wb"
	HorizSync	30-82
	VertRefresh	50-85
	Option		"DPMS"
	Modeline "1440x900_75.00" 136.49  1440 1536 1688 1936  900 901 904 940 -HSync +Vsync
	Modeline "1440x900_60.00" 106.47  1440 1520 1672 1904  900 901 904 932 -HSync +Vsync
	DisplaySize 	1440 900
EndSection
You probably need to edit the HorizSync and VertRefresh rates according to the values for your particular monitor. If that doesn't work, try adding a modeline to the monitor section by running the command gtf from a terminal. 
The default syntax is gtf "horiz" "vert" "refreshrate" 
You may also need to edit your modes in the Screen section to include refresh rate. Many others haven't needed to do this last step but I had to for some reason with this funky MAG 19" widescreen.
Here's what one of my modes sections looks like:
> SubSection "Display"
		Depth		24
		Modes		"1440x900_75.00" "1440x900_60.00" "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection

Hope this helps

---

### Post by CatKiller on 2006-11-24
Also, you might need to change your driver. You might be using a newer video card than the **ati** driver supports.

---

### Post by JayTee on 2006-11-24
One other thing I forgot to mention and should have was that you check the specifications on your monitor not just for the horizontal and vertical refresh rates but also for what the maximum screen resolution is AND also check what the max supported resolution is for your graphics card. If the max res on your ATI card does not match exactly the max res on your monitor then pick the lower of those two values as you won't be able to get anything working at the higher of the two. I had an older MAG lcd flat panel that would only go as high as 1024x768. Didn't matter that the video card supported higher resolutions. And I'd also follow CatKiller's recommendation to check out your driver version and see if there are newer ones.

---

