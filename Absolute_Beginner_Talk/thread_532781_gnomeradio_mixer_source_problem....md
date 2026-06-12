---
title: "gnomeradio mixer source problem..."
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by armanforum on 2007-08-23
OS: Ubuntu 7.04
Kernel: 2.6
Tv Card: AverTv Studio 203

i installed gnome radio,
i checked /dev folder and found my radio device is radio0
i write radio0 as my input device

inside mixer source only choice is "dig1" i think it has to be line0 or line1 so i can get sound...

so there is no sound but when i go to a frequency i can see the green lines and stereo

Thanks for the help

---

### Post by Offoffoff on 2007-12-04
I have the same problem... Gnomeradio even can get radiostations in right freq. places. But from tv-tuner sound output (03:02.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)) output I can here only strange noise sounds like modem. I know that real sound can be get from hw1,0 - this is virtual channel in PCI bus. But how to do it? I can make it for videosound in mplayer (it is really good monster line - mplayer tv:// -tv driver=v4l2:normid=5:fps=25:width=720:height=576:alsa:adevice=hw.1,0:amode=1:audiorate=32000:forceaudio:immediatemode=0), but how to learn gnomeradio to work in that way (through PCI)?

---

