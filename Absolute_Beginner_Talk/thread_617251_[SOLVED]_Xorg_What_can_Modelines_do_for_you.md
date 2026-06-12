---
title: "[SOLVED] Xorg: What can Modelines do for you?"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by Master One on 2007-11-19
I am quite confused ATM about the following issue:

I would like to use a D201GLY2 mainboard with onboard SiS662 Mirage* 1 graphics on a 24" - 28" LCD with native resolution of 1920x1200@60.

It is very hard, to obtain detailed info about this SiS662 Mirage*1 chipset, and the only useable info I found, was the following linup at [Winischhofer](http://www.winischhofer.net/):

..
1600x1200
1680x1050
1920x1080
1920x1440
2048x1536

as available built-in modes on the 315, 330 and 340 series (I guess SiS662 is 315 series), but no 1920x1200, which is the native resolution of all recent 24" - 28" LCD screens.

If using the Linux driver with Xorg, can this problem be solved by generating a modeline for 1920x1200?

I am confused, because in the [X.org Wiki - FAQVideoModes](http://www.x.org/wiki/FAQVideoModes) it says:> Some drivers are limited to the set of modes in the video BIOS. The most common examples are vesa, i810, and via. Usually there's nothing you can do in this situation, because it's not possible to modify the BIOS. Sorry. The exception is some Intel chips, where you can use the 855resolution or 915resolution hacks, and it might work. You should tell your hardware vendor that you want non-VBE modesetting support in an open source driver, and that they should at least put the native panel size in the video BIOS. There is work underway to remove this restriction from the i810 and via drivers, but vesa will always have this limitation.

So what's the deal? Is there a way, to find out, if a modeline will allow me, to use the mentioned mainboard on such a LCD screen with 1920x1200, before I purchase the equipment?

---

### Post by Master One on 2007-12-12
Well, in the meantime I did some tests with another machine, that has graphics integrated on the mainboard. It's a cheap ASRock mainboard with S3 Savage chipset. I connected that computer to my newly purchased 24" LCD with the native resolution of 1920x1200@60.

The problem is, that whatever I tried, I could not make it display in the native resolution, it always defaults to 1280x1024.

I really played around a lot, I added a fitting modeline to the monitor section, but no change.

I analyzed the Xorg.log file, which shows the following relevant content concerning the desired resolution:```
:~$ grep 1920 Xorg.6.log 
(II) SAVAGE(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) SAVAGE(0): Modeline "1920x1200"  154.00  1920 1968 2000 2080  1200 1203 1209 1235 -hsync +vsync
(II) SAVAGE(0): Estimated virtual size for aspect ratio 1.5938 is 1920x1200
(II) SAVAGE(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) SAVAGE(0): Not using default mode "1920x1440" (height too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 1920x1200 60Hz.
(II) SAVAGE(0): Not using default mode "1920x1200" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) SAVAGE(0): Not using default mode "1920x1440" (height too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 1920x1200 59Hz.
(II) SAVAGE(0): Not using driver mode "1920x1200" (no mode of this name)
(WW) SAVAGE(0): Shrinking virtual size estimate from 1920x1200 to 1400x1050
(--) SAVAGE(0): Virtual size is 1400x1050 (pitch 1920)
```

I am now wondering, if there is any way at all, to make this one work with 1920x1200.

Is a modeline just supposed to add support for a connected monitor, that does not report back the intended resolution as a supported one?

Because it seems to make no sense, to create a modeline, if the monitor itself reports back the proper modeline for that resolution (as seen above).

Does the above output indicate, that it's the chipset's BIOS fault, and that this issue is unfixable?

---

### Post by BCBill on 2007-12-15
What entries do you have in the ==>"Modes"<<== line of your
 /etc/X11/xorg.conf file for resolutions above "1280x1024"?

If you don't indicate _there_ that you want to work at "1920x1200",
that resolution won't be offered as an option
when you click System ==> Preferences ==>Screen Resolution
after logging on at whatever resolution you somehow end up at.

---

### Post by dcstar on 2007-12-15
> **Master One said:**
> I am quite confused ATM about the following issue:

I would like to use a D201GLY2 mainboard with onboard SiS662 Mirage* 1 graphics on a 24" - 28" LCD with native resolution of 1920x1200@60.
.........
So what's the deal? Is there a way, to find out, if a modeline will allow me, to use the mentioned mainboard on such a LCD screen with 1920x1200, before I purchase the equipment?

Have a look at this thread for indications of exactly where you should have the modeline info in your xorg.conf file:

[http://ubuntuforums.org/showthread.php?t=280683&highlight=modeline](http://ubuntuforums.org/showthread.php?t=280683&highlight=modeline)

BTW, my "gtf 1920 1200 60" generates the following modeline:
```

dc@dc-desktop:~$ gtf 1920 1200 60

  # 1920x1200 @ 60.00 Hz (GTF) hsync: 74.52 kHz; pclk: 193.16 MHz
  Modeline "1920x1200_60.00"  193.16  1920 2048 2256 2592  1200 1201 1204 1242  -HSync +Vsync
```

---

### Post by Master One on 2007-12-16
Thanks guys, the mentioned problem wasn't modeline-related after all, because my monitor offers the desired resolution by itself, and modelines are definitely just useful, if the connected monitor doesn't  report to support the desired resolution.

My problem was, that the graphics card's BIOS always tried to override the data reported by the monitor, so for S3 Savage it was **Option "UseBIOS" "False"**, for my other test with an ATI Radeon 9250 it was **Option "DDCMode" "True"** in the device section, to force the desired result.

---

