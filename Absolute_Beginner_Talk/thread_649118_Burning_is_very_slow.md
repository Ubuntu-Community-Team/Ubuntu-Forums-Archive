---
title: "Burning is very slow"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by Bandicoot on 2007-12-24
I've read alot of articles here on the froum about slow dvd burning , one of the newest threads ended on sept 29 without any working solution. Is my conclusion correct that it is simply not possible to get highspeed dvd burning ?? An iso of 4 GB takes about 14 minutes , which absolutely ridiculous !! I have an 18 speed burner, media certified for 18 speed, tried brasero, gnome isoburner and nerolinux all have slowburning.

---

### Post by LaRoza on 2007-12-24
You can burn at high speeds, but for ISO's, low speeds are recommended.

Try k3b for the most feature rich burning tool.

If you consider that the drive has to get the data right the first time, it is amazing there are no errors. The drive is constantly spinning and the drive has to have a steady stream of data, this means if it misses one byte, it can't go back. The slow speeds ensure that there are no errors, in ISO's of operating systems this is critical. It may not bother you to miss a single byte of a movie, but for system programs that is essential.

---

### Post by Bandicoot on 2007-12-24
For the main part I burn movies .. When I was still using windows I always burned at 12X without any problems. The movies I burn are mostly in iso format .. As far as I can see all my settings are right , but the burning jsut almost grinds to a halt and burns at approx 2 / 3 speed.

These are my current settings

/dev/hda:

 Model=TSSTcorpCD/DVDW SH-S182M, FwRev=SB05, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:227,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 
 AdvancedPM=no


/dev/hda:
 IO_support    =  1 (32-bit)
 unmaskirq     =  1 (on)
 using_dma     =  1 (on)
 keepsettings  =  0 (off)
 readonly      =  0 (off)
 readahead     = 256 (on)

---

