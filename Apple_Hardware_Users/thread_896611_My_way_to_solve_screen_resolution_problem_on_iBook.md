---
title: "My way to solve screen resolution problem on iBook G3 600"
date: 2008-08-21
forum: Apple Hardware Users
---

### Post by jeecol on 2008-08-21
Hi everyone, 


A. I had a iBook G3 600 with 256 Mb RAM (produced in 2002). I installed Xubuntu 6.10 in the iBook (the screen resolution was correct) in early 2007. But the hard drive was dead later.


B. From this website, I learned how to replace the HD. Then I put a 15 Gb HD into the iBook in Aug 18, 2008.

[http://www.ifixit.com/Guide/Mac/iBook-G3-14-Inch/51](http://www.ifixit.com/Guide/Mac/iBook-G3-14-Inch/51)


C. I have tried 7.04, 7.10 and 8.04 Ubuntu, but none of them could detect the screen resolution correctly.
 However, I install 8.04 in the iBook with wrong screen resolution setting.


D. I checked the threads in the forum, but I still could not make it work.

1. 8.04 iBook G3 600mhz no video driver problem

2. iBook G3 dualUSB resolution problem


E. On Aug 20, 2008 I downloaded Ubuntu 6.06 

1. Booted from this CD, and the screen resolution was correct.

2. I checked the xorg.conf file: sudo gedit   /etc/X11/xorg.conf (actually, "sudo" is not needed in live-CD)

3. I inserted a USB-disk and save the xorg.conf file (from 6.06) in the USB-disk. 

4. Booted the iBook from hard drive (8.04 installed), copied the three titles: device, monitor and screen (from xorg.conf of 6.06), and replaced the same titles in xorg.conf of 8.04

5. Restarted the computer, and this time it works at 1024*768 (thank God!)

-------------------------------

Section "Device"
	Identifier	"ATI Technologies, Inc. Rage Mobility M3 AGP 2x"
	Driver		"ati"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage Mobility M3 AGP 2x"
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
-------------------------

To my dear friends, if you have the same problem like mine, I highly suggest you to download old versions (such as 6.06 or 6.10) and got the xorg.conf file. 

By the way, only solving the resolution problem, I cannot start the visual effects. 

---------
&#8220;jeecol&#8221; means one dollar, in my first language, Taiwanese.

---

### Post by jtappin on 2008-09-16
With Intrepid, I was able to use this method (6.06 release) to get a 1024x768 login screen. But on logging in, the initial KDE4 splash screen appears, but after the first 3 steps, the screen went white (with a cursor) and then blue, whereas with the 800x600 wrapped display I was able to get a sensible if cramped desktop.

The blue screen had a few fuzzy rectangles of a different shade of blue but nothing that was of any use.

I've not yet had a chance to try installing any alternate desktops or window managers to see what they do (this machine [G3 600MHz iBook-dual USB (late 2001-early 2002), 384Mb] is pretty glacial when it comes to software installations).

NOTE added: 17/9: Turns out that somewhere along the line compiz-wrapper had been installed (nothing else from compiz, just the wrapper), and removing that fixed the white/blue screen.

---

### Post by Tovarich on 2008-09-18
Hi,
My problem is that I can't install 6.06 in an ibook 466 Mhz because of an initial wrong resolution screen, which prevents me to try any solutions posted here.

When I use the live CD I can manage to go with the mouse to the preferences and resolution screen and change it to 800 X 600, which is the best my ibook can support, but when I install 6.06 into the hard drive, there is no way to change the resolution screen because I can only see "Options" --> Shut down, Hibern, and so on, "Ubuntu" where it seems to be the center of the screen, and that's pretty much it.

So I wonder if there is some way to get to the terminal with the keyboard, and a command to change the resolution screen.

Thanks a lot

---

