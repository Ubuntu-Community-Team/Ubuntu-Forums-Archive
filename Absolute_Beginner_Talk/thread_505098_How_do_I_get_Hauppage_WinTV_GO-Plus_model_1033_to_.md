---
title: "How do I get Hauppage WinTV GO-Plus model 1033 to work with TVtime on Fiesty Fawn"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by EElight on 2007-07-19
Hi everyone I've just switched over to ubuntu Fiesty Fawn about two months ago because i wanted to get away from the evil clutches of windows.  The only prior linux experience I've had was Using Fedora Core back in 2004-2005 for a college computer science course.

Anyway,  Since Yesterday I've been trying unsuccessfully to get the Hauppage WinTV GO-Plus model 1033 to work but I've failed at every attempt so far.  After a bit of trying I restarted my computer into windows XP SP2 and installed the driver the TV tuner card came with to see if it worked and sure enough it began working perfectly without any hitches(I've yet to try the remote to see if it works so I don't have an opinion on it just yet).  Then I decided to shut down my computer disconnected it from the Internet and unpluuged its power cable.  Then when I got home today I hooked it back up and decided to open up TvTime and for some strange reason it started working perfectly and I don't know why, so I the decided to restart  my computer and boot back into Fiesty Fawn and then after I logged to see if it was still working it won't display any video signal.

when I type ```
sudo cat /var/log/syslog | grep bttv
``` I get the following

> 

Jul 19 18:49:10 Davids-desktop kernel: [ 1511.051445] bttv0: timeout: drop=61 irq=127893/147309, risc=1571101c, bits: HSYNC OFLOW
Jul 19 18:49:10 Davids-desktop kernel: [ 1511.051491] bttv0: reset, reinitialize
Jul 19 18:49:10 Davids-desktop kernel: [ 1511.051520] bttv0: PLL can sleep, using XTAL (28636363).
Jul 19 18:49:45 Davids-desktop kernel: [ 1546.727334] bttv0: SCERR @ 37ec0000,bits: OFLOW FDSR SCERR*
Jul 19 18:49:46 Davids-desktop kernel: [ 1547.376831] bttv0: timeout: drop=61 irq=129971/149979, risc=1562a01c, bits: HSYNC OFLOW
Jul 19 18:49:46 Davids-desktop kernel: [ 1547.376912] bttv0: reset, reinitialize
Jul 19 18:49:46 Davids-desktop kernel: [ 1547.376941] bttv0: PLL can sleep, using XTAL (28636363).
Jul 19 18:53:45 Davids-desktop kernel: [ 1785.502383] bttv0: timeout: drop=61 irq=140451/162662, risc=37ec001c, bits: VSYNC HSYNC OFLOW
Jul 19 18:53:45 Davids-desktop kernel: [ 1785.502462] bttv0: reset, reinitialize
Jul 19 18:53:45 Davids-desktop kernel: [ 1785.502491] bttv0: PLL can sleep, using XTAL (28636363).
Jul 19 20:04:19 Davids-desktop kernel: [   16.398061] bttv: driver version 0.9.16 loaded
Jul 19 20:04:19 Davids-desktop kernel: [   16.398067] bttv: using 8 buffers with 2080k (520 pages) each for capture
Jul 19 20:04:19 Davids-desktop kernel: [   16.398137] bttv: Bt8xx card found (0).
Jul 19 20:04:19 Davids-desktop kernel: [   16.398175] bttv0: Bt878 (rev 17) at 0000:03:02.0, irq: 19, latency: 64, mmio: 0xee001000
Jul 19 20:04:19 Davids-desktop kernel: [   16.398186] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
Jul 19 20:04:19 Davids-desktop kernel: [   16.398189] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
Jul 19 20:04:19 Davids-desktop kernel: [   16.398216] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
Jul 19 20:04:19 Davids-desktop kernel: [   16.400700] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
Jul 19 20:04:19 Davids-desktop kernel: [   16.437313] bttv0: Hauppauge eeprom indicates model#44981
Jul 19 20:04:19 Davids-desktop kernel: [   16.437317] bttv0: using tuner=0
Jul 19 20:04:19 Davids-desktop kernel: [   16.437426] bttv0: i2c: checking for MSP34xx @ 0x80... not found
Jul 19 20:04:19 Davids-desktop kernel: [   16.438306] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
Jul 19 20:04:19 Davids-desktop kernel: [   16.439201] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
Jul 19 20:04:19 Davids-desktop kernel: [   16.494616] bttv0: i2c: checking for TDA9887 @ 0x86... not found
Jul 19 20:04:19 Davids-desktop kernel: [   16.548261] bttv0: registered device video0
Jul 19 20:04:19 Davids-desktop kernel: [   16.548310] bttv0: registered device vbi0
Jul 19 20:04:19 Davids-desktop kernel: [   16.548335] bttv0: PLL: 28636363 => 35468950 .. ok
Jul 19 20:05:17 Davids-desktop kernel: [   81.913937] bttv0: PLL can sleep, using XTAL (28636363).
Jul 19 20:47:59 Davids-desktop kernel: [ 2639.800149] bttv0: PLL: 28636363 => 35468950 .. ok
Jul 19 20:48:30 Davids-desktop kernel: [ 2670.598286] bttv0: PLL can sleep, using XTAL (28636363).
Jul 19 20:48:32 Davids-desktop kernel: [ 2672.756800] bttv0: OCERR @ 379a2000,bits: HSYNC OFLOW OCERR*
Jul 19 20:48:32 Davids-desktop kernel: [ 2672.824891] bttv0: OCERR @ 379a2000,bits: HSYNC OFLOW FDSR OCERR*
Jul 19 20:50:10 Davids-desktop kernel: [ 2770.950388] bttv0: PLL: 28636363 => 35468950 .. ok
Jul 19 20:50:34 Davids-desktop kernel: [ 2794.868637] bttv0: SCERR @ 379a2000,bits: OFLOW SCERR*
Jul 19 20:50:34 Davids-desktop kernel: [ 2794.918546] bttv0: SCERR @ 379a2000,bits: OFLOW SCERR*
Jul 19 20:50:34 Davids-desktop kernel: [ 2794.959283] bttv0: SCERR @ 379a2000,bits: HSYNC OFLOW SCERR*
Jul 19 20:50:34 Davids-desktop kernel: [ 2794.989419] bttv0: SCERR @ 379a2000,bits: HSYNC OFLOW SCERR*
Jul 19 20:50:34 Davids-desktop kernel: [ 2795.018477] bttv0: SCERR @ 379a2000,bits: OFLOW SCERR*
Jul 19 20:50:34 Davids-desktop kernel: [ 2795.059210] bttv0: SCERR @ 379a2000,bits: HSYNC OFLOW SCERR*
Jul 19 20:50:34 Davids-desktop kernel: [ 2795.085096] bttv0: SCERR @ 379a2000,bits: OFLOW SCERR*
Jul 19 20:50:34 Davids-desktop kernel: [ 2795.125828] bttv0: SCERR @ 379a2000,bits: HSYNC OFLOW SCERR*
Jul 19 20:50:34 Davids-desktop kernel: [ 2795.151778] bttv0: SCERR @ 379a2000,bits: OFLOW SCERR*
Jul 19 20:50:34 Davids-desktop kernel: [ 2795.192510] bttv0: SCERR @ 379a2000,bits: HSYNC OFLOW SCERR*
Jul 19 20:50:34 Davids-desktop kernel: [ 2795.222646] bttv0: SCERR @ 379a2000,bits: HSYNC OFLOW SCERR*
Jul 19 20:50:34 Davids-desktop kernel: [ 2795.255891] bttv0: SCERR @ 379a2000,bits: HSYNC OFLOW SCERR*
Jul 19 20:50:34 Davids-desktop kernel: [ 2795.295546] bttv0: SCERR @ 379a2000,bits: HSYNC OFLOW SCERR*
Jul 19 20:50:35 Davids-desktop kernel: [ 2795.336025] bttv0: SCERR @ 379a2000,bits: HSYNC OFLOW SCERR*
Jul 19 20:50:35 Davids-desktop kernel: [ 2795.375678] bttv0: SCERR @ 379a2000,bits: HSYNC OFLOW SCERR*
Jul 19 20:50:35 Davids-desktop kernel: [ 2795.405815] bttv0: SCERR @ 379a2000,bits: HSYNC OFLOW SCERR*
Jul 19 20:50:35 Davids-desktop kernel: [ 2795.434874] bttv0: SCERR @ 379a2000,bits: HSYNC OFLOW SCERR*
Jul 19 20:50:35 Davids-desktop kernel: [ 2795.475605] bttv0: SCERR @ 379a2000,bits: HSYNC OFLOW SCERR*
Jul 19 20:50:35 Davids-desktop kernel: [ 2795.501429] bttv0: SCERR @ 379a2000,bits: HSYNC OFLOW SCERR*
Jul 19 20:50:35 Davids-desktop kernel: [ 2795.542160] bttv0: SCERR @ 379a2000,bits: HSYNC OFLOW SCERR*
Jul 19 20:50:35 Davids-desktop kernel: [ 2795.568110] bttv0: SCERR @ 379a2000,bits: HSYNC OFLOW SCERR*
Jul 19 20:50:35 Davids-desktop kernel: [ 2795.601357] bttv0: SCERR @ 379a2000,bits: HSYNC OFLOW SCERR*
Jul 19 20:50:35 Davids-desktop kernel: [ 2795.642087] bttv0: SCERR @ 379a2000,bits: HSYNC OFLOW SCERR*
Jul 19 20:50:35 Davids-desktop kernel: [ 2795.672224] bttv0: SCERR @ 379a2000,bits: HSYNC OFLOW SCERR*
Jul 19 20:50:35 Davids-desktop kernel: [ 2795.701346] bttv0: SCERR @ 379a2000,bits: HSYNC OFLOW SCERR*
Jul 19 20:50:35 Davids-desktop kernel: [ 2795.734655] bttv0: SCERR @ 379a2000,bits: HSYNC OFLOW SCERR*
Jul 19 20:50:35 Davids-desktop kernel: [ 2795.767901] bttv0: SCERR @ 379a2000,bits: HSYNC OFLOW SCERR*
Jul 19 20:50:35 Davids-desktop kernel: [ 2795.808634] bttv0: SCERR @ 379a2000,bits: HSYNC OFLOW SCERR*
Jul 19 20:50:35 Davids-desktop kernel: [ 2795.838770] bttv0: SCERR @ 379a2000,bits: HSYNC OFLOW SCERR*
Jul 19 20:50:35 Davids-desktop kernel: [ 2795.872143] bttv0: SCERR @ 379a2000,bits: HSYNC OFLOW SCERR*
Jul 19 20:50:35 Davids-desktop kernel: [ 2795.888812] bttv0: timeout: drop=198 irq=23175/78002, risc=379a201c, bits: HSYNC OFLOW
Jul 19 20:50:35 Davids-desktop kernel: [ 2795.888887] bttv0: reset, reinitialize
Jul 19 20:50:35 Davids-desktop kernel: [ 2795.888924] bttv0: PLL: 28636363 => 35468950 . ok
Jul 19 20:50:38 Davids-desktop kernel: [ 2799.142715] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW FBUS FDSR SCERR*
Jul 19 20:50:39 Davids-desktop kernel: [ 2799.433044] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW FBUS FTRGT FDSR SCERR*
Jul 19 20:50:39 Davids-desktop kernel: [ 2799.492494] bttv0: SCERR @ 379a2014,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:39 Davids-desktop kernel: [ 2799.519457] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:39 Davids-desktop kernel: [ 2799.552829] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:39 Davids-desktop kernel: [ 2799.581825] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:39 Davids-desktop kernel: [ 2799.615135] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:39 Davids-desktop kernel: [ 2799.655866] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:39 Davids-desktop kernel: [ 2799.681755] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:39 Davids-desktop kernel: [ 2799.715102] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW FBUS SCERR*
Jul 19 20:50:39 Davids-desktop kernel: [ 2799.755794] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW FBUS SCERR*
Jul 19 20:50:39 Davids-desktop kernel: [ 2799.785993] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:39 Davids-desktop kernel: [ 2799.814989] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:39 Davids-desktop kernel: [ 2799.848303] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:39 Davids-desktop kernel: [ 2799.881609] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:39 Davids-desktop kernel: [ 2799.914915] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:39 Davids-desktop kernel: [ 2799.948223] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:39 Davids-desktop kernel: [ 2799.988957] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:39 Davids-desktop kernel: [ 2800.019095] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:39 Davids-desktop kernel: [ 2800.048155] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:39 Davids-desktop kernel: [ 2800.088886] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:39 Davids-desktop kernel: [ 2800.114776] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:39 Davids-desktop kernel: [ 2800.148079] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:39 Davids-desktop kernel: [ 2800.181401] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:39 Davids-desktop kernel: [ 2800.222121] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:39 Davids-desktop kernel: [ 2800.248011] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:39 Davids-desktop kernel: [ 2800.288740] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:40 Davids-desktop kernel: [ 2800.328394] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:40 Davids-desktop kernel: [ 2800.368872] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:40 Davids-desktop kernel: [ 2800.402118] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:40 Davids-desktop kernel: [ 2800.431175] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:40 Davids-desktop kernel: [ 2800.471909] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:40 Davids-desktop kernel: [ 2800.497795] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:40 Davids-desktop kernel: [ 2800.538526] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:40 Davids-desktop kernel: [ 2800.578180] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:40 Davids-desktop kernel: [ 2800.614348] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:40 Davids-desktop kernel: [ 2800.668592] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:40 Davids-desktop kernel: [ 2800.701963] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:40 Davids-desktop kernel: [ 2800.741617] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:40 Davids-desktop kernel: [ 2800.768517] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:40 Davids-desktop kernel: [ 2800.808172] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:40 Davids-desktop kernel: [ 2800.847826] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:40 Davids-desktop kernel: [ 2800.885131] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:40 Davids-desktop kernel: [ 2800.918504] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:40 Davids-desktop kernel: [ 2800.947499] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:40 Davids-desktop kernel: [ 2800.980807] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:40 Davids-desktop kernel: [ 2801.021540] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:40 Davids-desktop kernel: [ 2801.051678] bttv0: SCERR @ 379a2014,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:40 Davids-desktop kernel: [ 2801.091331] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:40 Davids-desktop kernel: [ 2801.114043] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:40 Davids-desktop kernel: [ 2801.154776] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:40 Davids-desktop kernel: [ 2801.180726] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:40 Davids-desktop kernel: [ 2801.213972] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:40 Davids-desktop kernel: [ 2801.247284] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:40 Davids-desktop kernel: [ 2801.280592] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:41 Davids-desktop kernel: [ 2801.313904] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:41 Davids-desktop kernel: [ 2801.347208] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:41 Davids-desktop kernel: [ 2801.380521] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:41 Davids-desktop kernel: [ 2801.421251] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:41 Davids-desktop kernel: [ 2801.451386] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:41 Davids-desktop kernel: [ 2801.480508] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:41 Davids-desktop kernel: [ 2801.521241] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:41 Davids-desktop kernel: [ 2801.560896] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:41 Davids-desktop kernel: [ 2801.601310] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:41 Davids-desktop kernel: [ 2801.634555] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:41 Davids-desktop kernel: [ 2801.667864] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:41 Davids-desktop kernel: [ 2801.701173] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:41 Davids-desktop kernel: [ 2801.730236] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:41 Davids-desktop kernel: [ 2801.770966] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:41 Davids-desktop kernel: [ 2801.796924] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:41 Davids-desktop kernel: [ 2801.830222] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:41 Davids-desktop kernel: [ 2801.863472] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:41 Davids-desktop kernel: [ 2801.904205] bttv0: SCERR @ 379a2014,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:41 Davids-desktop kernel: [ 2801.943860] bttv0: SCERR @ 379a201c,bits: VSYNC HSYNC OFLOW FBUS SCERR*
Jul 19 20:50:41 Davids-desktop kernel: [ 2801.984339] bttv0: SCERR @ 379a201c,bits: VSYNC HSYNC OFLOW FBUS SCERR*
Jul 19 20:50:41 Davids-desktop kernel: [ 2802.013398] bttv0: SCERR @ 379a201c,bits: VSYNC HSYNC OFLOW FBUS SCERR*
Jul 19 20:50:41 Davids-desktop kernel: [ 2802.046726] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW FBUS SCERR*
Jul 19 20:50:41 Davids-desktop kernel: [ 2802.080011] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:41 Davids-desktop kernel: [ 2802.120742] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:41 Davids-desktop kernel: [ 2802.150942] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:41 Davids-desktop kernel: [ 2802.184189] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:41 Davids-desktop kernel: [ 2802.217496] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:41 Davids-desktop kernel: [ 2802.257151] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:42 Davids-desktop kernel: [ 2802.296806] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:42 Davids-desktop kernel: [ 2802.336464] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:42 Davids-desktop kernel: [ 2802.367419] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:42 Davids-desktop kernel: [ 2802.396479] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:42 Davids-desktop kernel: [ 2802.437211] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:42 Davids-desktop kernel: [ 2802.463096] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:42 Davids-desktop kernel: [ 2802.503828] bttv0: SCERR @ 379a2000,bits: VSYNC HSYNC OFLOW SCERR*
Jul 19 20:50:42 Davids-desktop kernel: [ 2802.505402] bttv0: timeout: drop=204 irq=23280/78445, risc=379a201c, bits: HSYNC OFLOW
Jul 19 20:50:42 Davids-desktop kernel: [ 2802.505492] bttv0: reset, reinitialize
Jul 19 20:50:42 Davids-desktop kernel: [ 2802.505526] bttv0: PLL: 28636363 => 35468950 . ok



I know that the card is being auto detected which from what I've seen online is a good thing.  Can anyone help myself resolve this issue and explain where to start in a step by step guide for Linux noobs like my self?

My Computer:

Manufacturer: DELL Dimension 5100
CPU: Intel Pentium 4 2.80 GHz
Graphics Card: ATI Radeon X300 SE 128MB Hypermemory
HD1: 80GB Maxtor Hard-drive Windows XP PRO SP2
HD2: 320GB Western Digital Hard-drive Ubuntu Fiesty Fawn 7.04
RAM: 1.00GB
Sound Card: Sound Blaster Audigy2 ZX
TV-Tuner: Hauppage WinTV GO-Plus model 1033

---

