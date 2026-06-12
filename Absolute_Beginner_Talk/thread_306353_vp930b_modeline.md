---
title: "vp930b modeline"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by sebiskaa on 2006-11-24
hi,
i'm having a problem with my monitor, i can't change the display resolution from 640*480. i followed all the steps described in [URL="http://ubuntuforums.org/showthread.php?t=83973"], but nothing works. linux doesn't recognize my monitor so there's no use in reconfiguring Xorg. the only thing left to do is, i think, entering a modeline in my xorg.conf file. i'm planing on using my monitor at the preferred resolution of 1280x1024 @60Hz, the problem is i don't know which modeline to use. i've tried a few online modeline generators but they all displayed different results. i don't know which one is correct and i wouldn't like to fry my monitor.
one program i used (under windows xp) called Monitor Asset Manager showed the following:

Monitor
  Windows description......... ViewSonic VP930 Series
  Manufacturer description.... VP930 Series
  Manufacturer................ ViewSonic
  ————————————————————————————
  Plug and Play ID............ VSCE41B
  Serial number............... 
  EDID data source............ I2C bus (real-time)
  ————————————————————————————
  Manufacture date............ 2006, ISO week 20
  EDID revision............... 1.3
  Display type and signal..... Digital
  Sync input support.......... n/a
  Screen size................. 380 x 310 mm (~21")
  Power management............ Active off/sleep

Color characteristics
  Display gamma............... 2.20
  Red chromaticity............ Rx 0.641 - Ry 0.353
  Green chromaticity.......... Gx 0.289 - Gy 0.626
  Blue chromaticity........... Bx 0.142 - By 0.078
  White point (default)....... Wx 0.313 - Wy 0.329

Timing characteristics
  VESA GTF support............ Not supported
  Horizontal scan range....... 30-82kHz
  Vertical scan range......... 50-75Hz
  Video bandwidth............. 140MHz
  Extension blocks............ n/a
  Timing recommendation #1.... 1280x1024 at 60Hz
      Modeline................ "1280x1024" 108.000 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync

Standard timings supported
   640 x  480 at  60Hz - IBM VGA
   640 x  480 at  67Hz - Mac II
   640 x  480 at  72Hz - VESA
   640 x  480 at  75Hz - VESA
   640 x  640 at  70Hz - VESA
   720 x  400 at  70Hz - IBM VGA
   800 x  600 at  56Hz - VESA
   800 x  600 at  60Hz - VESA
   800 x  600 at  72Hz - VESA
   800 x  600 at  75Hz - VESA
   832 x  624 at  75Hz - Mac II
  1024 x  768 at  60Hz - VESA
  1024 x  768 at  70Hz - VESA
  1024 x  768 at  75Hz - VESA
  1152 x  864 at  75Hz - VESA
  1152 x  870 at  75Hz - Mac II
  1280 x  960 at  60Hz - VESA
  1280 x 1024 at  60Hz - VESA
  1280 x 1024 at  60Hz - ViewSonic
  1280 x 1024 at  75Hz - VESA

Raw EDID base
  00: 00 FF FF FF FF FF FF 00  5A 63 1B E4 01 01 01 01 
  10: 14 10 01 03 80 26 1F 78  2E 11 45 A4 5A 4A A0 24 
  20: 14 50 54 BF EF 80 81 80  81 40 71 4F 31 0A 01 01 
  30: 01 01 01 01 01 01 30 2A  00 98 51 00 2A 40 30 70 
  40: 13 00 78 36 11 00 00 1E  00 00 00 FF 00 51 38 48 
  50: 30 36 32 30 30 31 39 31  35 0A 00 00 00 FD 00 32 
  60: 4B 1E 52 0E 00 0A 20 20  20 20 20 20 00 00 00 FC 
  70: 00 56 50 39 33 30 20 53  65 72 69 65 73 0A 00 32 

Display adapter
  Adapter description......... NVIDIA GeForce 6600
  Adapter device ID........... 0x00F210DE
  Display settings............ 1280x1024, 32bpp


Unfortunately, it didn't recognize my monitor very well, the horizontal scan range is 24-82 Khz and the vertical scan range is 50-85 Hz. also the display size is incorrect, i have a 19''. so i don't know if the suggested modeline is correct.
viewsonic sent me the VESA_TIMINGS but i'm not sure how to generate the complete modeline using it. this is what they sent me (1280x1024 only):
				
CLOCK FREQ.		MHz	108	135	157,5

HORIZONTAL					
Data Pixel		(dots)	1280	1280	1280
Frequency		(kHz)	63,981	79,98	91,146
Period		(us)	15,63	12,504	10,971
Display Time		(us)	11,852	9,481	8,127
Blank Time		(us)	3,778	3,022	2,844
Front Porch		(us)	0,444	0,119	0,305
Sync Width		(us)	1,037	1,067	1,016
Back Porch		(us)	2,296	1,837	1,524

VERTICAL					
Data Line		(lines)	1024	1024	1024
Frequency		(Hz)	60,02	75,03	85,024
Period		(ms)	16,661	13,329	11,761
Display Time		(ms)	16,006	12,804	11,235
Blank Time		(ms)	0,656	0,525	0,527
Front Porch		(ms)	0,016	0,013	0,011
Sync Width		(ms)	0,047	0,038	0,033
Back Porch		(ms)	0,594	0,475	0,483
Sync Pol. H/V			pos/pos	pos/pos	pos/pos

i would really  apreciate knowing which modeline should i use, please help if you know. thanks.

---

