---
title: "Video Capture on Dell Inspiron Not Working in Mint 16 XFCE"
date: 2014-03-09
forum: Any Other OS
---

### Post by Mrich01 on 2014-03-09
Hello,

I'm using using Cheese 3.8 & VLC 2.8 on a brand new installation of Mint 16 64bit XFCE on an Inspiron with a built-in webcam. When I launch the program & choose video capture, the video is not synchronized with my movements. It is delayed &  jerky. When I select start recording it freezes. If I select stop recording it remains frozen. At that time I can use the mouse to select other options, even thought the video is still. 

These are the hardware specs on the laptop:
Dell Inspiron 15R i15RM-7538sLV
Intel Core i7-4500U Processor 1.8 GHz
16Gigs of RAM
15.6-Inch Screen

I've gotten similar results using a Logitech C920 webcam connected through USB.

According to some, the correct driver for this laptop is not installed by default with this distro.

When I run the lspci command, I get this:
```
VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 09)
Subsystem: Dell Device [1028:05e9]
Kernel driver in use: i915
00:03.0 Audio device [0403]: Intel Corporation Device [8086:0a0c] (rev 09)
```

The graphics card information from Dell website is this: *Haswell - HD Graphics 4400*. Others sources on the internet say this laptop has this card: *Haswell - HD Graphics 4600*. So it looks as though I have a *Haswell - HD Graphics 4400/4600*. 

I've found no information on internet for the exact type of built-in webcam for this laptop.

I downloaded the *Graphics Installer* for Ubuntu 13.10, 64-bit from this site: [https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-1.0.4-linux](https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-1.0.4-linux). The name of the file is: *intel-linux-graphics-installer_1.0.4-0intel1_amd64.deb*.

Before I installed it, I used these commands, both of which generated an "OK" after completion:
```
wget https://download.01.org/gfx/RPM-GPG-KEY-ilg -O - | sudo apt-key add -
wget https://download.01.org/gfx/RPM-GPG-KEY-ilg-2 -O - | sudo apt-key add -
```

Then I installed *intel-linux-graphics-installer_1.0.4-0intel1_amd64.deb*, which was successful.

Currently the display settings in Settings Manager are: LGD 15" 1366x786 60Hz.

I downloaded a HD 720p video that displayed OK. I also did multiple 1080p HD tests on YouTube, that worked fine. So, it seems as though HD is enabled for this display.

It also doesn't work in VLC 2.8. I select Media, Open Capture Device, & see that the Capture mode is Video 2 for Linux, Video Device Name is /dev/video0, & Video Standard is Undefined. It opens a window, at the top of which is /dev/video0, & v4l2. At that time the webcam is viewing, but the picture quality is bad & the video is lagging behind my movements. It is definitely not HD, & is similar to the Cheese program in quality.

I'm also using a new installation of Mint 16 Cinnamon on the same PC. Even though I never installed the graphics driver for this, it has the exact same settings in *Settings Manager*. Also, it displays 1080p videos on YouTube OK. This leads me to wonder if the correct driver for this card is really installed. Of course, it might be something other than the video that is causing this. 

Any suggestions to get this working properly would be much appreciated.

Thank You,

Mark

---

### Post by ajgreeny on 2014-03-09
I can't help with your cheese problem as in the days that I used gnome with cheese as the default I never once managed to get it to work for video capture.
It saved still images fine but never videos, no matter which way I tried.

Guvcview, however, worked fine and still does with my Xubuntu 12.04. I am also using a Logitech webcam, but a really cheap and cheerful version with separate mic, as the webcam does not have mic built in, and that works fine with this machine as it did also with a very old sempron 2400+ with ATI 9200SE graphic card

---

