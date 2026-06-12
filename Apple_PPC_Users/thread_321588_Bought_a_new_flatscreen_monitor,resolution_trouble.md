---
title: "Bought a new flatscreen monitor,resolution troubles"
date: 2006-12-19
forum: Apple PPC Users
---

### Post by macminiuser on 2006-12-19
I just purchased a new LG LCD "19 flatscreen monitor for my macmini,I am dual booting Mac os 10.4 and ubuntu edgy eft.
What I am having trouble with is the resolution on the ubuntu side.
Once I hooked up the new monitor and turned on my mac, Macos 10.4 had my monitor already setup,I can get 1440x900@60hz.
But nothing changed on ubuntu I can only get 1024x768 what gives?
my video card is a ati 9700
I am also using the digital port on my mac.

---

### Post by eXisor on 2006-12-19
I've just been through this exercise, so maybe I can help. You need to specify your monitor's modelines in your /etc/X11/xorg.conf file.

1) To do this open two terminal windows:

In the first open the xorg file for editing, and find the monitor section: 
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
sudo gedit /etc/X11/xorg.conf
```

In the second, for a resolution/refesh rate of 1600x1200@85mhz type: 
```
gtf 1600 1200 85
```

(There are other online modeline generators out there, but I find they don't keep within my monitors clock range, which makes them largely useless for me. So that's why I use 'gtf').

This will give you something like: ```
 
  # 1600x1200 @ 85.00 Hz (GTF) hsync: 107.10 kHz; pclk: 234.76 MHz
  Modeline "1600x1200_85.00"  234.76  1600 1720 1896 2192  1200 1201 1204 1260  -HSync +Vsync
```

This gives you the modeline you need so cut all that and paste it into the monitor section of the xorg file.

Rince and repeat for all the resolutions and refresh rates you want/need/know work on the monitor.

2) Then in the 'screen' section of the xorg file add the new modes you created to the modes of the various colour bit sections. The first  mode within the defaultdepth is what is used when you start X. (Since my defaultdepth is 24, you can see I start with "1600x1200_75"). I suggest you start with something you definitely know the monitor/graphics card supports.

For example, here is my monitor section:

```
Section "Monitor"
	Identifier	"C996F"
	Option		"DPMS"
	HorizSync	30-96
	VertRefresh	50-160
	
	# 1024x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 64.11 MHz
  	Modeline "1024x768_60"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync
  	# 1024x768 @ 70.00 Hz (GTF) hsync: 56.00 kHz; pclk: 76.16 MHz
  	Modeline "1024x768_70"  76.16  1024 1080 1192 1360  768 769 772 800  -HSync +Vsync
	# 1024x768 @ 75.00 Hz (GTF) hsync: 60.15 kHz; pclk: 81.80 MHz
  	Modeline "1024x768_75"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync
  	# 1024x768 @ 85.00 Hz (GTF) hsync: 68.60 kHz; pclk: 94.39 MHz
  	Modeline "1024x768_85"  94.39  1024 1088 1200 1376  768 769 772 807  -HSync +Vsync

  	# 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
	Modeline "1280x1024_60"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
  	# 1280x1024 @ 70.00 Hz (GTF) hsync: 74.62 kHz; pclk: 128.94 MHz
  	Modeline "1280x1024_70"  128.94  1280 1368 1504 1728  1024 1025 1028 1066  -HSync +Vsync
	# 1280x1024 @ 75.00 Hz (GTF) hsync: 80.17 kHz; pclk: 138.54 MHz
	Modeline "1280x1024_75"  138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync
 	# 1280x1024 @ 85.00 Hz (GTF) hsync: 91.38 kHz; pclk: 159.36 MHz
  	Modeline "1280x1024_85"  159.36  1280 1376 1512 1744  1024 1025 1028 1075  -HSync +Vsync

	# 1600x1200 @ 60.00 Hz (GTF) hsync: 74.52 kHz; pclk: 160.96 MHz
  	Modeline "1600x1200_60"  160.96  1600 1704 1880 2160  1200 1201 1204 1242  -HSync +Vsync
	# 1600x1200 @ 70.00 Hz (GTF) hsync: 87.43 kHz; pclk: 190.25 MHz
  	Modeline "1600x1200_70"  190.25  1600 1712 1888 2176  1200 1201 1204 1249  -HSync +Vsync
   	# 1600x1200 @ 75.00 Hz (GTF) hsync: 93.97 kHz; pclk: 205.99 MHz
  	Modeline "1600x1200_75"  205.99  1600 1720 1896 2192  1200 1201 1204 1253  -HSync +Vsync

EndSection
```

And here is my 'screen' section:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
	Monitor		"C996F"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1600x1200_75" "1600x1200_70" "1600x1200_60" "1280x1024_85" "1280x1024_75" "1280x1024_70" "1280x1024_60" "1024x768_85" "1024x768_75" "1024x768_70" "1024x768_60" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200_75" "1600x1200_70" "1600x1200_60" "1280x1024_85" "1280x1024_75" "1280x1024_70" "1280x1024_60" "1024x768_85" "1024x768_75" "1024x768_70" "1024x768_60" "800x600" "640x480"
	EndSubSection
EndSection
```

3) If you know your monitors min & max horizsync and vertrefresh frequencies you can add them to the monitor section like I did (see above).

4) The name of the modeline is the first part after 'modeline', and this must be what you refer to in the modes section of the screen section. (I dropped the .00 that gtf appends after the name, so either do that too, or include the .00 when you reference the name in the screen modes section.

5) Save the changes to the xorg.conf file and hit ALT CTL Backspace to restart X.

6) If X won't start, reboot into single user mode and restore the xorg.conf file from the backup.

```
cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

Then try again.

The above exercise should make all the resolutions appear and be selectable within gnome. 

Holler if you come unstuck.

---

### Post by Citosicarius on 2007-01-15
Thank you SOOOOOO Much, you rock!!   I only wish it was easier to find information like this when you need it.  I have an older monitor and under certain refresh rates, it makes an absolutely ear splitting, headache creating noise.. which it decided to default to after installing NVidia drivers.

  Thanks again for the effort of posting this


 Shaun

---

### Post by jaja23bd on 2007-04-24
not so lucky.

 It does not work... :(

---

### Post by jenslandberg on 2008-02-09
I've recently had quite the same experience with the persistent 1024 768 60Hz monitor setting.
Unfortunately the method presented here for resolving this problem did not work for me.
I am running 6.06 on a quite obsolete 1,25 PPC  macmini with radeon 9200 as graphics card.
(TFT is SyncMaster 913v, 1280 1024 75Hz.)

Any suggestions how to proceed are most welcome. (And yes, I am as green as one can be:)

---

### Post by stream303 on 2008-02-09
> **jenslandberg said:**
> Any suggestions how to proceed are most welcome. (And yes, I am as green as one can be:)

Here's another ubuntu xorg.conf, maybe it will help.  Seems that adding

Options  "UseFBDev" "false"

really helped when placed in the device section of xorg.conf.  Although that thread seems more about graphics than a new screen, but might have pointers for something to look at about half-way into the thread using your 1280x1024 resolution.

[http://ohioloco.ubuntuforums.org/showthread.php?t=637913](http://ohioloco.ubuntuforums.org/showthread.php?t=637913)

Looks like manually editing the resolution for your flatscreen might be in order..

---

### Post by jenslandberg on 2008-02-09
> **stream303 said:**
> Here's another ubuntu xorg.conf, maybe it will help.  ... 

Thank you very much for the suggestion, tip and link!

I'll try to find the time to give this matter some serious testing this upcoming week and will post the result in this thread. (Along with the gazillion questions I will probably have by then and wern't skilled enough to find the answer to.

Again, many thanks! :)

---

### Post by roystonlodge on 2008-02-10
I am having similar difficulties.  I have my Mac Mini hooked up to a 37" RCA widescreen tv (with a VGA input).

When I boot from the live cd, my tv displays an error message "Mode unsupported".  I presume that means it's trying to display at an unsupported resolution.

Is there a command I can type in at the "boot:" prompt to tell it to boot up at a different resolution?

If not, is there a file I can change on the live cd to tell it to boot at the correct resolution?

Thanks in advance!

---

### Post by Cows on 2008-02-18
Thanks, I got my resolution to work but I still have one problem. My refresh rate is mest up. My screen is like blurry and you can see the desktop and stuff sorta wiggle. How can I fix this ?

---

