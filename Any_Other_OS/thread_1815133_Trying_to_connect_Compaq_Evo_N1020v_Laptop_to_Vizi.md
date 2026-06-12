---
title: "Trying to connect Compaq Evo N1020v Laptop to Vizio E320VL TV"
date: 2011-07-30
forum: Any Other OS
---

### Post by ronnielsen1 on 2011-07-30
Like the title says I'm trying to connect Compaq Evo N1020v Laptop to a Vizio E320VL TV with a VGA to VGA cable (or as the TV puts it RGB) It works until it gets past boot up stage and then the TV displays [COLOR=Red]NOT SUPPORT[/COLOR] 

It sounds like a resolution problem but this goes above my pay grade. I'm just barely smart enough/geek enough to have ditched windows 7 years ago. :popcorn: I'm not sure what steps I need to take here.

The specs for the TV are:
> **Tech Specs**

                    SPECIFICATIONS   Class: 32"
  Viewable: 31.5" diagonal   Tuner: NTSC/ATSC/QAM   Native Panel Resolution: 1366 x 768 pixels   Signal Compatibility: 1080i, 720p, 480p, 480i   Colors: 1.06 Billion   Computer Support: 1920 x 1080, 1024 x 768, 800 x 600, 640 x 480 via RGB/HDMI   Dynamic Contrast Ratio: 100,000&#65306;1   Brightness: 500 cd/m2
  Response Time: 8ms   Viewable Angle: 178/178 degrees (horizontal/vertical)   Pixel/Dot Pitch: 0.510mm(H) x 0.510mm(V)   SRS TruSurround HD™: Yes   SRS TruVolume™: Yes   SRS TruSurround XT™: No     
    INPUTS (REAR)   HDMI with HDCP 2   RF Connector for Internal Tuner 1   Component YPbPr plus Stereo Audio: 1   S-Video: 
  Computer RGB: 1   Composite Video: 1 
  USB Ports: 1
  Photo (JPEG): 
    
    INPUTS (SIDE)   HDMI with HDCP  
  RF Connector for Internal Tuner     Component YPbPr plus Stereo Audio:     Composite Video:     S-Video:     Computer RGB:     USB Ports: 1
  Music (MP3):     Video (MPEG):     Photo (JPEG):       
    OUTPUTS (REAR)   SPDIF Digital Optical: 1   Stereo Audio: 1 
  Headphones: 
    
    ADDITIONAL FEATURES   Refresh Rate: 60Hz   Smooth Motion: No   Panel Type: CCFL, LCD
  Picture-in-Picture (PIP): No
  Picture-outside-Picture (POP): No   Zero Bright Pixel Defect Guarantee: Yes
  V-Chip: Yes   3D Comb Filter: No   3:2 or 2:2 Reverse Pull-down: No   ATSC with 8VSB & QAM demodulation: No   ATSC with MPEG-2 decoding: No   NTSC Video decoding via Video: No   Progressive Scan Video: No   Color Temperature: 5400K, 6300K and 9300K   Color Fine Tuning: Red/Blue/Green 
  Speakers: Built-in 10W x 2 Speakers   Panel Lamp Life (typical): 50,000 Hours   Voltage Range: 120Vac at 50/60Hz   Power Consumption: 49W, <0.37W Standby   VIZIO Remote Control: VR15

I'm running the latest Linux Mint Gnome (I don't know LM forums, I've been around Ubuntu forum) with the latest kernel (had to because of an issue that was corrected with the last one). Let me know what other information you need and I'd be glad to post it. Thanks.

---

### Post by gordintoronto on 2011-07-30
Can you confirm that your laptop has this graphics adapter:
ATI Radeon IGP 340M 
running at 1024 by 768 resolution?

---

### Post by Perfect Storm on 2011-07-31
Moved to Other OS/Distro Talk.

---

### Post by ronnielsen1 on 2011-07-31
> Can you confirm that your laptop has this graphics adapter:
ATI Radeon IGP 340M 
running at 1024 by 768 resolution?

Yes

> in7@laptop ~ $ lspci
00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:0a.0 CardBus bridge: Texas Instruments PCI4410 PC card Cardbus Controller (rev 02)
00:0a.1 FireWire (IEEE 1394): Texas Instruments PCI4410 FireWire Controller (rev 02)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 20)
00:0c.0 Communication controller: Conexant Systems, Inc. HSF 56k HSFi Modem (rev 01)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:13.0 USB Controller: NEC Corporation USB (rev 41)
00:13.1 USB Controller: NEC Corporation USB (rev 41)
00:13.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M
02:00.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)



>     ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
    ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
    ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
    ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
    ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
    ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
    ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
    ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
    ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
    ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
    AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
    ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
    ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
    ATI Mobility Radeon HD 4670, ATI FirePro M5750,
    ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
    ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
    ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
    ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI RV670,
    ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
    ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
    ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
    ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
    ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
    ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
    ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
    ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3000 Graphics, ATI Radeon HD 4200, ATI Radeon 4100,
    ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
    ATI Radeon HD 4290, ATI Radeon HD 4290, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5900 Series, ATI Radeon HD 5900 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 5700 Series,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
    ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, CEDAR, CEDAR, CEDAR,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, CEDAR, ATI Radeon HD 5450,
    CEDAR
[    70.343] (II) VESA: driver for VESA chipsets: vesa
[    70.343] (II) FBDEV: driver for framebuffer: fbdev
[    70.343] (++) using VT number 7

[    70.344] (II) [KMS] Kernel modesetting enabled.
[    70.344] (WW) Falling back to old probe method for vesa
[    70.344] (WW) Falling back to old probe method for fbdev
[    70.348] (II) Loading sub module "fbdevhw"
[    70.348] (II) LoadModule: "fbdevhw"
[    70.349] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    70.363] (II) Module fbdevhw: vendor="X.Org Foundation"
[    70.364]     compiled for 1.9.0, module version = 0.0.2
[    70.364]     ABI class: X.Org Video Driver, version 8.0
[    70.364] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    70.364] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    70.364] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    70.365] (==) RADEON(0): Default visual is TrueColor
[    70.365] (==) RADEON(0): RGB weight 888
[    70.365] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    70.365] (--) RADEON(0): Chipset: "ATI Radeon IGP330M/340M/350M (U2) 4337" (ChipID = 0x4337)
[    70.365] (II) RADEON(0): AGP card detected
[    70.365] (II) RADEON(0): KMS Color Tiling: disabled
[    70.365] drmOpenDevice: node name is /dev/dri/card0
[    70.365] drmOpenDevice: open result is 8, (OK)
[    70.365] drmOpenByBusid: Searching for BusID pci:0000:01:05.0
[    70.365] drmOpenDevice: node name is /dev/dri/card0
[    70.366] drmOpenDevice: open result is 8, (OK)
[    70.366] drmOpenByBusid: drmOpenMinor returns 8
[    70.366] drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
[    70.495] (II) RADEON(0): Output VGA-0 has no monitor section
[    70.495] (II) RADEON(0): Output LVDS has no monitor section
[    70.495] (II) RADEON(0): Output S-video has no monitor section
[    70.695] (II) RADEON(0): EDID for output VGA-0
[    70.695] (II) RADEON(0): Manufacturer: VIZ  Model: 67  Serial#: 16843009
[    70.695] (II) RADEON(0): Year: 2010  Week: 26
[    70.695] (II) RADEON(0): EDID Version: 1.3
[    70.695] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    70.695] (II) RADEON(0): Sync:  Separate
[    70.695] (II) RADEON(0): Max Image Size [cm]: horiz.: 70  vert.: 39
[    70.695] (II) RADEON(0): Gamma: 2.20
[    70.695] (II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
[    70.695] (II) RADEON(0): First detailed timing is preferred mode
[    70.696] (II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.290 greenY: 0.600
[    70.696] (II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.280 whiteY: 0.290
[    70.696] (II) RADEON(0): Supported established timings:
[    70.696] (II) RADEON(0): 720x400@70Hz
[    70.696] (II) RADEON(0): 640x480@60Hz
[    70.696] (II) RADEON(0): 640x480@75Hz
[    70.696] (II) RADEON(0): 800x600@60Hz
[    70.696] (II) RADEON(0): 800x600@72Hz
[    70.696] (II) RADEON(0): 800x600@75Hz
[    70.696] (II) RADEON(0): 1024x768@60Hz
[    70.696] (II) RADEON(0): 1024x768@70Hz
[    70.696] (II) RADEON(0): 1024x768@75Hz
[    70.696] (II) RADEON(0): Manufacturer's mask: 0
[    70.696] (II) RADEON(0): Supported standard timings:
[    70.696] (II) RADEON(0): #0: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[    70.696] (II) RADEON(0): Supported detailed timing:
[    70.696] (II) RADEON(0): clock: 85.5 MHz   Image Size:  698 x 392 mm
[    70.696] (II) RADEON(0): h_active: 1366  h_sync: 1494  h_sync_end 1624 h_blank_end 1798 h_border: 0
[    70.696] (II) RADEON(0): v_active: 768  v_sync: 770  v_sync_end 776 v_blanking: 795 v_border: 0
[    70.696] (II) RADEON(0): Ranges: V min: 50 V max: 77 Hz, H min: 31 H max: 70 kHz, PixClock max 155 MHz
[    70.696] (II) RADEON(0): Serial No: SAHLBL2601449
[    70.696] (II) RADEON(0): Monitor name: E320VL
[    70.697] (II) RADEON(0): EDID (in hex):
[    70.697] (II) RADEON(0):     00ffffffffffff00593a670001010101
[    70.697] (II) RADEON(0):     1a140103084627782ae69da3544a9926
[    70.697] (II) RADEON(0):     0f474aa5ce0081c00101010101010101
[    70.697] (II) RADEON(0):     010101010101662156b051001b308082
[    70.697] (II) RADEON(0):     2600ba882100001a000000fd00324d1f
[    70.697] (II) RADEON(0):     460f000a202020202020000000ff0053
[    70.697] (II) RADEON(0):     41484c424c32363031343439000000fc
[    70.697] (II) RADEON(0):     0045333230564c0a20202020202000f1
[    70.697] (II) RADEON(0): EDID vendor "VIZ", prod id 103
[    70.697] (II) RADEON(0): Using EDID range info for horizontal sync
[    70.697] (II) RADEON(0): Using EDID range info for vertical refresh
[    70.697] (II) RADEON(0): Printing DDC gathered Modelines:
[    70.697] (II) RADEON(0): Modeline "1366x768"x0.0   85.50  1366 1494 1624 1798  768 770 776 795 +hsync -vsync (47.6 kHz)
[    70.697] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    70.697] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    70.697] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    70.697] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    70.697] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    70.698] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    70.698] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    70.698] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    70.698] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    70.698] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[    70.698] (II) RADEON(0): Printing probed modes for output VGA-0
[    70.698] (II) RADEON(0): Modeline "1366x768"x59.8   85.50  1366 1494 1624 1798  768 770 776 795 +hsync -vsync (47.6 kHz)
[    70.698] (II) RADEON(0): Modeline "1280x720"x60.0   74.44  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.7 kHz)
[    70.698] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[    70.698] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    70.698] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    70.698] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    70.698] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    70.698] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    70.699] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    70.699] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    70.699] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    70.699] (II) RADEON(0): EDID for output LVDS
[    70.699] (II) RADEON(0): Manufacturer: SEC  Model: 0  Serial#: 0
[    70.699] (II) RADEON(0): Year: 2002  Week: 0
[    70.699] (II) RADEON(0): EDID Version: 1.2
[    70.699] (II) RADEON(0): Digital Display Input
[    70.699] (II) RADEON(0): Max Image Size [cm]: horiz.: 31  vert.: 23
[    70.699] (II) RADEON(0): Gamma: 2.20
[    70.699] (II) RADEON(0): No DPMS capabilities specified
[    70.699] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    70.699] (II) RADEON(0): First detailed timing is preferred mode
[    70.699] (II) RADEON(0): redX: 0.589 redY: 0.337   greenX: 0.322 greenY: 0.524
[    70.699] (II) RADEON(0): blueX: 0.152 blueY: 0.137   whiteX: 0.315 whiteY: 0.330
[    70.699] (II) RADEON(0): Manufacturer's mask: 0
[    70.700] (II) RADEON(0): Supported detailed timing:
[    70.700] (II) RADEON(0): clock: 65.0 MHz   Image Size:  304 x 228 mm
[    70.700] (II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
[    70.700] (II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
[    70.700] (II) RADEON(0): Unknown vendor-specific block f
[    70.700] (II) RADEON(0):  SAMSUNG
[    70.700] (II) RADEON(0):  LTN150XB-L01
[    70.700] (II) RADEON(0): EDID (in hex):
[    70.700] (II) RADEON(0):     00ffffffffffff004ca3000000000000
[    70.700] (II) RADEON(0):     000c0102801f17780ad90e9656528627
[    70.700] (II) RADEON(0):     23505400000001010101010101010101
[    70.701] (II) RADEON(0):     01010101010164190040410026301888
[    70.701] (II) RADEON(0):     360030e4100000190000000f00047e18
[    70.701] (II) RADEON(0):     ff0105026f18ff027401000000fe0053
[    70.701] (II) RADEON(0):     414d53554e470a2020202020000000fe
[    70.701] (II) RADEON(0):     004c544e31353058422d4c30310a004d
[    70.701] (II) RADEON(0): Printing probed modes for output LVDS
[    70.701] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    70.701] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    70.701] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[    70.701] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[    70.701] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    70.701] (II) RADEON(0): EDID for output S-video
[    70.701] (II) RADEON(0): Output VGA-0 connected
[    70.701] (II) RADEON(0): Output LVDS connected
[    70.701] (II) RADEON(0): Output S-video disconnected
[    70.701] (II) RADEON(0): Using exact sizes for initial modes
[    70.701] (II) RADEON(0): Output VGA-0 using initial mode 1024x768
[    70.701] (II) RADEON(0): Output LVDS using initial mode 1024x768
[    70.702] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    70.702] (II) RADEON(0): mem size init: gart size :3dff000 vram size: s:2000000 visible:1eb8000
[    70.702] (II) RADEON(0): EXA: Driver will not allow EXA pixmaps in VRAM
[    70.726] (**) RADEON(0): Display dimensions: (700, 390) mm
[    70.726] (**) RADEON(0): DPI set to (37, 50)
[    70.726] (II) Loading sub module "fb"
[    70.726] (II) LoadModule: "fb"
[    70.727] (II) Loading /usr/lib/xorg/modules/libfb.so
[    70.742] (II) Module fb: vendor="X.Org Foundation"
[    70.742]     compiled for 1.9.0, module version = 1.0.0
[    70.742]     ABI class: X.Org ANSI C Emulation, version 0.4
[    70.742] (II) Loading sub module "ramdac"
[    70.742] (II) LoadModule: "ramdac"
[    70.742] (II) Module "ramdac" already built-in
[    70.742] (II) Loading sub module "exa"
[    70.742] (II) LoadModule: "exa"
[    70.743] (II) Loading /usr/lib/xorg/modules/libexa.so
[    70.746] (II) Module exa: vendor="X.Org Foundation"
[    70.746]     compiled for 1.9.0, module version = 2.5.0
[    70.746]     ABI class: X.Org Video Driver, version 8.0
[    70.746] (II) UnloadModule: "vesa"
[    70.746] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    70.746] (II) UnloadModule: "fbdev"
[    70.746] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    70.746] (II) UnloadModule: "fbdevhw"
[    70.747] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    70.747] (--) Depth 24 pixmap format is 32 bpp
[    70.747] (II) RADEON(0): [DRI2] Setup complete
[    70.747] (II) RADEON(0): [DRI2]   DRI driver: radeon
[    70.748] (II) RADEON(0): Front buffer size: 3072K
[    70.748] (II) RADEON(0): VRAM usage limit set to 25545K
[    70.769] (==) RADEON(0): Backing store disabled
[    70.769] (II) RADEON(0): Direct rendering enabled
[    70.769] (II) RADEON(0): Render acceleration enabled for R100 type cards.
[    70.769] (II) RADEON(0): Setting EXA maxPitchBytes
[    70.769] (II) EXA(0): Driver allocated offscreen pixmaps
[    70.769] (II) EXA(0): Driver registered support for the following operations:
[    70.769] (II)         Solid
[    70.769] (II)         Copy
[    70.769] (II)         Composite (RENDER acceleration)
[    70.769] (II)         UploadToScreen
[    70.769] (II)         DownloadFromScreen
[    70.769] (II) RADEON(0): Acceleration enabled
[    70.769] (==) RADEON(0): DPMS enabled
[    70.769] (==) RADEON(0): Silken mouse enabled
[    70.788] (II) RADEON(0): Set up textured video
[    70.789] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    70.789] (--) RandR disabled
[    70.790] (II) Initializing built-in extension Generic Event Extension
[    70.790] (II) Initializing built-in extension SHAPE
[    70.790] (II) Initializing built-in extension MIT-SHM
[    70.790] (II) Initializing built-in extension XInputExtension
[    70.790] (II) Initializing built-in extension XTEST
[    70.790] (II) Initializing built-in extension BIG-REQUESTS
[    70.790] (II) Initializing built-in extension SYNC
[    70.790] (II) Initializing built-in extension XKEYBOARD
[    70.790] (II) Initializing built-in extension XC-MISC
[    70.790] (II) Initializing built-in extension SECURITY
[    70.790] (II) Initializing built-in extension XINERAMA
[    70.790] (II) Initializing built-in extension XFIXES
[    70.790] (II) Initializing built-in extension RENDER
[    70.790] (II) Initializing built-in extension RANDR
[    70.790] (II) Initializing built-in extension COMPOSITE
[    70.790] (II) Initializing built-in extension DAMAGE
[    70.790] (II) Initializing built-in extension GESTURE
[    71.228] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    71.229] (II) AIGLX: enabled GLX_INTEL_swap_event
[    71.229] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    71.229] (II) AIGLX: enabled GLX_SGI_make_current_read
[    71.229] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    71.229] (II) AIGLX: Loaded and initialized /usr/lib/dri/radeon_dri.so
[    71.230] (II) GLX: Initialized DRI2 GL provider for screen 0
[    71.411] (II) RADEON(0): Setting screen physical size to 270 x 203
[    71.877] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    71.929] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    71.929] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    71.929] (II) LoadModule: "evdev"
[    71.930] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    71.964] (II) Module evdev: vendor="X.Org Foundation"
[    71.964]     compiled for 1.9.0, module version = 2.3.2
[    71.964]     Module class: X.Org XInput Driver
[    71.964]     ABI class: X.Org XInput driver, version 11.0
[    71.965] (**) Power Button: always reports core events
[    71.965] (**) Power Button: Device: "/dev/input/event3"
[    71.965] (II) Power Button: Found keys
[    71.965] (II) Power Button: Configuring as keyboard
[    71.965] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    71.965] (**) Option "xkb_rules" "evdev"
[    71.965] (**) Option "xkb_model" "pc105"
[    71.965] (**) Option "xkb_layout" "us"
[    71.967] (II) config/udev: Adding input device Sleep Button (/dev/input/event4)
[    71.967] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    71.967] (**) Sleep Button: always reports core events
[    71.967] (**) Sleep Button: Device: "/dev/input/event4"
[    71.967] (II) Sleep Button: Found keys
[    71.967] (II) Sleep Button: Configuring as keyboard
[    71.967] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    71.967] (**) Option "xkb_rules" "evdev"
[    71.967] (**) Option "xkb_model" "pc105"
[    71.967] (**) Option "xkb_layout" "us"
[    71.971] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    71.971] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    71.971] (**) Video Bus: always reports core events
[    71.971] (**) Video Bus: Device: "/dev/input/event6"
[    71.971] (II) Video Bus: Found keys
[    71.971] (II) Video Bus: Configuring as keyboard
[    71.972] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    71.972] (**) Option "xkb_rules" "evdev"
[    71.972] (**) Option "xkb_model" "pc105"
[    71.972] (**) Option "xkb_layout" "us"
[    71.974] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    71.974] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    71.974] (**) Power Button: always reports core events
[    71.974] (**) Power Button: Device: "/dev/input/event1"
[    71.975] (II) Power Button: Found keys
[    71.975] (II) Power Button: Configuring as keyboard
[    71.975] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    71.975] (**) Option "xkb_rules" "evdev"
[    71.975] (**) Option "xkb_model" "pc105"
[    71.975] (**) Option "xkb_layout" "us"
[    71.976] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    71.976] (II) No input driver/identifier specified (ignoring)
[    71.977] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    71.977] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    71.977] (**) Sleep Button: always reports core events
[    71.977] (**) Sleep Button: Device: "/dev/input/event0"
[    71.977] (II) Sleep Button: Found keys
[    71.977] (II) Sleep Button: Configuring as keyboard
[    71.977] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    71.977] (**) Option "xkb_rules" "evdev"
[    71.978] (**) Option "xkb_model" "pc105"
[    71.978] (**) Option "xkb_layout" "us"
[    71.996] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event5)
[    71.997] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    71.997] (**) AT Translated Set 2 keyboard: always reports core events
[    71.997] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event5"
[    71.997] (II) AT Translated Set 2 keyboard: Found keys
[    71.997] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    71.997] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    71.997] (**) Option "xkb_rules" "evdev"
[    71.997] (**) Option "xkb_model" "pc105"
[    71.997] (**) Option "xkb_layout" "us"
[    71.998] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[    71.999] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    71.999] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    71.999] (II) LoadModule: "synaptics"
[    71.999] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    72.050] (II) Module synaptics: vendor="X.Org Foundation"
[    72.050]     compiled for 1.9.0, module version = 1.2.2
[    72.050]     Module class: X.Org XInput Driver
[    72.050]     ABI class: X.Org XInput driver, version 11.0
[    72.050] (II) Synaptics touchpad driver version 1.2.2
[    72.050] (**) Option "Device" "/dev/input/event7"
[    72.050] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    72.050] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    72.050] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    72.050] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    72.050] (II) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    72.051] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    72.051] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    72.051] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    72.051] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    72.051] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    72.051] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    72.051] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    72.051] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    72.053] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    72.053] (II) No input driver/identifier specified (ignoring)
[    77.788] (II) RADEON(0): EDID vendor "SEC", prod id 0
[    77.789] (II) RADEON(0): Printing DDC gathered Modelines:
[    77.789] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    78.010] (II) RADEON(0): EDID vendor "SEC", prod id 0
[    78.025] (II) RADEON(0): Printing DDC gathered Modelines:
[    78.025] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    78.313] (II) RADEON(0): EDID vendor "SEC", prod id 0
[    78.313] (II) RADEON(0): Printing DDC gathered Modelines:
[    78.313] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    78.482] (II) RADEON(0): EDID vendor "SEC", prod id 0
[    78.482] (II) RADEON(0): Printing DDC gathered Modelines:
[    78.482] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   101.116] (II) RADEON(0): EDID vendor "SEC", prod id 0
[   101.116] (II) RADEON(0): Printing DDC gathered Modelines:
[   101.116] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   101.206] (II) RADEON(0): EDID vendor "SEC", prod id 0
[   101.206] (II) RADEON(0): Printing DDC gathered Modelines:
[   101.206] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   101.269] (II) RADEON(0): EDID vendor "SEC", prod id 0
[   101.269] (II) RADEON(0): Printing DDC gathered Modelines:
[   101.269] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   101.327] (II) RADEON(0): EDID vendor "SEC", prod id 0
[   101.327] (II) RADEON(0): Printing DDC gathered Modelines:
[   101.327] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   110.697] (II) RADEON(0): EDID vendor "SEC", prod id 0
[   110.697] (II) RADEON(0): Printing DDC gathered Modelines:
[   110.697] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   113.181] (II) RADEON(0): EDID vendor "SEC", prod id 0
[   113.690] (II) RADEON(0): Printing DDC gathered Modelines:
[   113.690] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  3255.600] (II) RADEON(0): EDID vendor "SEC", prod id 0
[  3255.600] (II) RADEON(0): Printing DDC gathered Modelines:
[  3255.600] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  3256.094] (II) RADEON(0): EDID vendor "SEC", prod id 0
[  3256.094] (II) RADEON(0): Printing DDC gathered Modelines:
[  3256.094] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  5542.503] (II) RADEON(0): EDID vendor "SEC", prod id 0
[  5542.503] (II) RADEON(0): Printing DDC gathered Modelines:
[  5542.503] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)


---

### Post by ronnielsen1 on 2011-07-31
> Location: Denmark - Scandinavia

My Grandparents and my Dad came to the U.S. from there.

---

### Post by mips on 2011-07-31
On your laptop adjust the external monitor resolution to "Native Panel Resolution: **1366 x 768**" and see what happens.

---

### Post by ronnielsen1 on 2011-07-31
I'm going to ask a real stupid question. How do I adjust the external video resolution?

---

### Post by mips on 2011-08-01
In the software where you configure the second screen or catalyst control centre. Don't have Mint so cant be more specific.

---

### Post by gordintoronto on 2011-08-01
System/Preferences(???)/Monitors

---

