---
title: "Probably impossible in Ubuntu ?"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by Basics102 on 2007-08-16
I really need to know if im wasting my time. Its about the freakin screen resolution. Ive tried everything. Here are some infos: Amd64, Ati x600 using fglrx driver, compiz fusion works and is stable. I use a tv as a monitor (Samsung LE26R72B) it has a pc mode and its maximum resolution for the computer mode is 1360x768. I tried some reconfiguring dont remember the code. I even stopped the gdm for autodetection for the reconfigure thing, when it comes to the point to select resolutions 1360x768 is not available.
 
Xorg.conf: Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    30.0 - 100.0
	VertRefresh  30.0 - 93.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "Generic Video Card"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Generic Video Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1360x768" "1024x768" "800x600" "768x576" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1360x768" "1024x768" "768x576" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1360x768" "1024x768" "800x600" "768x576" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1360x768" "1024x768" "800x600" "768x576" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1360x768" "1024x768" "800x600" "768x576" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1360x768" "1024x768" "800x600" "768x576" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection

I posted this before but its a dead thread because nobody seems to know an answer. So I thought ill give it another shot. Please help me, I had to delete windows to install Ubuntu, and It was an headache to get everything running as for example restricted drivers. 

Best Regards from Iceland

---

### Post by heimo on 2007-08-16
Not sure if this will help you at all, but I think the correct resolution for Samsung LE26R72B is [SIZE=-1]136**6** x 768.[/SIZE]

---

### Post by Basics102 on 2007-08-16
No thats for TV mode, but anyway thanks for the try. :)

---

### Post by heimo on 2007-08-16
> **Basics102 said:**
> No thats for TV mode, but anyway thanks for the try. :)

Ok. Then you could check if you get any ideas from this post - it's a kind of collection of resolution/refresh rate related tips'n'tricks:
[Fixing Resolution/refresh rate problems]("http://ubuntuforums.org/showpost.php?p=454217&postcount=1")

---

### Post by PandaGoat on 2007-08-16
It does with the horizontal refresh rate and vertical sync.  They are probably not set correctly.  You would have to look at the TV's manual or something to figure it out exactly, or you could play with it until you get it right.

---

### Post by heimo on 2007-08-16
Here's link to a LARGE (>60MB) pdf, which I think is manual for that television.
[http://org.downloadcenter.samsung.com/downloadfile/ContentsFile.aspx?CDSite=NL&CttFileID=914344&CDCttType=UM&ModelType=N&ModelName=LE26R72B&VPath=UM/200603/20060313133239875_BN68-00983A-01L7-0301.pdf](http://org.downloadcenter.samsung.com/downloadfile/ContentsFile.aspx?CDSite=NL&CttFileID=914344&CDCttType=UM&ModelType=N&ModelName=LE26R72B&VPath=UM/200603/20060313133239875_BN68-00983A-01L7-0301.pdf)

---

### Post by Basics102 on 2007-08-16
Yes and here is additional info: mode resolution    horizontal      Vertical       Pixel Clock  Sync Polarity
                  Resolution:      1360 x 768         Frequency (khz): 47.72    Frequency (hz): 60.05      Frequency (mhz): 85.800    (h/V)

---

### Post by Basics102 on 2007-08-16
adding this to the xorg(in to the right place):
 # 1360x768 @ 60.01 Hz (GTF) hsync: 47.71 kHz; pclk: 85.8 MHz
  Modeline "1360x768_60.01"  85.8  1360 1424 1568 1776  768 769 772 795  -HSync +Vsync

ill be right back with results

---

### Post by Basics102 on 2007-08-17
Didnt work

---

### Post by macogw on 2007-08-17
try running "sudo X -configure" it'll make a crazy big sample xorg.conf with ALL the possibilities for your stuff, so it should show everything your monitor can take, and you can use it as reference in editing your real xorg.conf

---

### Post by jjbean on 2007-08-17
> **Basics102 said:**
> adding this to the xorg(in to the right place):
 # 1360x768 @ 60.01 Hz (GTF) hsync: 47.71 kHz; pclk: 85.8 MHz
  Modeline "1360x768_60.01"  85.8  1360 1424 1568 1776  768 769 772 795  -HSync +Vsync

ill be right back with results

I have an an ATI card as well, using the fglrx driver. I don't know if it will work for you, but to get Modelines to work I have to leave off the -HSync +Vsync. Might depend on the device. That I don't know.

If you want to see my xorg.conf. Let me know and I will post it ASAP.

---

### Post by Basics102 on 2007-08-20
I tried the command to see all the possiblities that should work with my stuff, I stopped the genome display manager to run the command but there was an error and the core dumped.
Ill try removing the -Hsync... thing.

Thanks for the support

---

