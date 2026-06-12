---
title: "Refreshrate problems"
date: 2005-10-10
forum: Absolute Beginner Talk
---

### Post by Quincy2you on 2005-10-10
Hi, im new to this forum and to Ubuntu and to Linux and to Gnome......

I'm having some problems with my refreshrate.

It won't go higher then 85 hz. This is the section in my /etc/X11/xorg.conf file:
> 
Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	        30-96
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600 GT]"
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

As you can see my monitor can support up to 160 hz refresh rate but I can't select higher then 85 hz in resolution manager in gnome.

Here is a section from my my /var/log/xorg.0.log file.

> (II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) NVIDIA(0): Linear framebuffer at 0xC0000000
(--) NVIDIA(0): MMIO registers at 0xC8000000
(II) NVIDIA(0): NVIDIA GPU detected as: GeForce 6600 GT
(--) NVIDIA(0): VideoBIOS: 05.43.02.27.00
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(II) NVIDIA(0): Connected display device(s): CRT-0
(--) NVIDIA(0): CRT-0: maximum pixel clock: 400 MHz
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) NVIDIA(0): Generic Monitor: Using hsync range of 30.00-96.00 kHz
(II) NVIDIA(0): Generic Monitor: Using vrefresh range of 50.00-160.00 Hz
(II) NVIDIA(0): Clock range:  12.00 to 400.00 MHz
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(WW) (2048x1536,Generic Monitor) mode clock 266.95MHz exceeds DDC maximum 250MHz
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1440x900" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x960" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x960" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x800" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1152x864" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1152x864" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x768" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1152x768" (width too large for virtual size)
(WW) NVIDIA(0): Not using mode "576x384":
(WW) NVIDIA(0):   horizontal sync start (589) not a multiple of 8
(WW) NVIDIA(0): Not using mode "360x200":
(WW) NVIDIA(0):   horizontal sync start (378) not a multiple of 8
(**) NVIDIA(0): Validated modes for display device CRT-0:
(**) NVIDIA(0):      Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "640x480": 74.2 MHz, 85.9 kHz, 85.1 Hz (D)
(**) NVIDIA(0):      Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(**) NVIDIA(0):      Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(**) NVIDIA(0):      Default mode "1024x768": 133.5 MHz, 95.3 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 44.9 MHz, 35.5 kHz, 87.0 Hz (I)
(**) NVIDIA(0):      Default mode "960x720": 117.0 MHz, 90.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "928x696": 109.2 MHz, 86.4 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "896x672": 102.4 MHz, 83.7 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "960x600": 115.0 MHz, 91.0 kHz, 72.8 Hz (D)
(**) NVIDIA(0):      Default mode "960x600": 96.6 MHz, 74.5 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(**) NVIDIA(0):      Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "800x600": 101.2 MHz, 93.8 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(**) NVIDIA(0):      Default mode "800x600": 94.5 MHz, 87.5 kHz, 70.0 Hz (D)
(**) NVIDIA(0):      Default mode "800x600": 87.8 MHz, 81.2 kHz, 65.0 Hz (D)
(**) NVIDIA(0):      Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(**) NVIDIA(0):      Default mode "800x600": 81.0 MHz, 75.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(**) NVIDIA(0):      Default mode "840x525": 73.6 MHz, 65.2 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "700x525": 92.0 MHz, 93.9 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "700x525": 77.9 MHz, 81.5 kHz, 74.8 Hz (D)
(**) NVIDIA(0):      Default mode "700x525": 75.5 MHz, 77.0 kHz, 70.0 Hz (D)
(**) NVIDIA(0):      Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x512": 78.8 MHz, 91.1 kHz, 85.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x512": 67.5 MHz, 80.0 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(**) NVIDIA(0):      Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(**) NVIDIA(0):      Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "576x432": 60.8 MHz, 77.5 kHz, 85.2 Hz (D)
(**) NVIDIA(0):      Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 39.4 MHz, 60.1 kHz, 75.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.9 Hz (D)
(**) NVIDIA(0):      Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(--) NVIDIA(0): Display dimensions: (350, 260) mm
(--) NVIDIA(0): DPI set to (74, 75)

Please, anybody an idea how to get higher refreshrate?

---

### Post by Perfect Storm on 2005-10-10
Do you have your monitor specs manual?

---

### Post by Quincy2you on 2005-10-10
[QUOTE=Artificial Intelligence]Do you have your monitor specs manual?[/QUOTE]

No, but I used the specs from the internet: [http://product.samsung.com/cgi-bin/nabc/product/b2c_product_detail.jsp?eUser=&prod_id=LE19ISBB&selTab=Specifications](http://product.samsung.com/cgi-bin/nabc/product/b2c_product_detail.jsp?eUser=&prod_id=LE19ISBB&selTab=Specifications)

---

### Post by Perfect Storm on 2005-10-10
As I can see out of theis monitor specs, ubuntu are showing the right refresh rate. 

> 
RESOLUTION  	   	 Maximum  	  	 1920x1440 / 64 Hz
  	  	                Recommended 	  	1600x1200 / 76 Hz


You destroy your monitor if you're breaching the maximum.

---

