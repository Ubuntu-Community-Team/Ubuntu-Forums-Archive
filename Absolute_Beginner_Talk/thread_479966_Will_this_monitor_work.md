---
title: "Will this monitor work?"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by EAL on 2007-06-20
I am currently considering the purchase of[ this 24" monitor]("http://accessories.us.dell.com/sna/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=A1162248") or one very similar.

I want to be sure it will work under Ubuntu 7.04 with my graphics card. ATI 9800 (9600?) 

If I need to buy another graphics card, I'd like suggestions on what would be sure to work with said monitor, fit the old style agp slot on my main board, and hopefully support dual monitors, tho I'm willing to work with two separate vid cards, one has to be standard PCI tho.

Here's the video section of my xorg.conf file

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AR [Radeon 9600]"
	Monitor		"SyncMaster"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

---

### Post by p_quarles on 2007-06-20
The ATI 9800 card supports that monitor's resolution at a higher rate (100MHz) than the monitor itself, so you should be fine. 

As far as I know, you should be able to add the 1920x1200 resolution to the xorg.conf file and then get full performance.

---

### Post by EAL on 2007-06-21
> **p_quarles said:**
> The ATI 9800 card supports that monitor's resolution at a higher rate (100MHz) than the monitor itself, so you should be fine. 

As far as I know, you should be able to add the 1920x1200 resolution to the xorg.conf file and then get full performance.

Thanks for the reply P.  I'm a newb, and I am not exactly comfortable editing config files.  Is there a way to make Ubuntu recognize everything like it did when I installed?

Also: I want to go dual monitor after I buy a new vid card.  What is the basic process for that?

Can someone recommend a decent basic video card that will fit a regular PCI slot?

---

### Post by Clay_Banger on 2007-06-21
you will prob be able to find a standard agp one that will do it by itself, i doubt u will be able to by a new pci card anyway.

---

### Post by aquavitae on 2007-06-21
I don't know if you need a new card, but if you get one go for nvidia - the drivers have much better support in linux.

You should be able to set up a new monitor useing the ubuntu system settings.  In theory that'll work, but if there are any quirks with your monitor/video card setup you may need to edit the xorg.conf file.  Its not really a big issue editing conf files, its just another way of changing settings.  In fact I prefer it, you can back up the file before editing it, and you have far more control over exactly what gets changed.  Requires a bit of a shift in thinking though which takes time!

By dual boot do you mean windows/linux or linux/linux?  Are you going to install them on the same drive or separate ones?  What OSs do you have installed at the moment?

---

