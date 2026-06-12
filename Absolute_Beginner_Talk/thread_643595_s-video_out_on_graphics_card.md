---
title: "s-video out on graphics card"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by Luksion Knight on 2007-12-17
well i just installed my new graphics card, and it has s-video out hooked up to my TV. now if i boot the computer without a monitor plugged in, the TV becomes the monitor, however if the monitor is plugged in, theres no s-video output. how do i make it so output is sent both to the monitor and s-video?

---

### Post by alphaniner on 2007-12-18
I may be mistaken, but I remember reading that if you connect something to S-Video, that's all you get.  As I recall, this is a hardware limitation and has nothing to do with Ubuntu.

Again, I may be mistaken and this may only apply to a certain brand or line of cards, in which case it will be at least some ATI Radeons (the ones with two VGA/DVI or one VGA and one DVI plus the S-Video).

---

### Post by Luksion Knight on 2007-12-18
what about a geforce 8500?

---

### Post by daengbo on 2007-12-18
Have you tried using nvtv or nvidia-settings to control the TV-out?

---

### Post by Luksion Knight on 2007-12-18
how do i do that exactly?

---

### Post by x-to-tha-t on 2007-12-18
I got this working via RCA (composite) by installing nvtv from .deb package and then entering the following lines into my /etc/X11/xorg.conf in Section "Device" below the rest of the current entries:
```
Option "TwinView" "true"
Option "TwinViewOrientation" "Clone"
Option "TVOutFormat" "COMPOSITE"
Option "TVStandard" "PAL-I"
Option "SecondMonitorHorizSync" "30-50"
Option "SecondMonitorVertRefresh" "50"
Option "MetaModes" "1024x768,1024x768;800x600,800x600;640x480,640x480;512x384,512x384
```

You will need to replace COMPOSITE with S-VIDEO and PAL-I with your local pallette. PAL-I is for the UK only, so change it to one of the following:

"PAL-B" : used in Belgium, Denmark, Finland, Germany, Guinea,
Hong Kong, India, Indonesia, Italy, Malaysia, The
Netherlands, Norway, Portugal, Singapore, Spain,
Sweden, and Switzerland
"PAL-D" : used in China and North Korea
"PAL-G" : used in Denmark, Finland, Germany, Italy, Malaysia,
The Netherlands, Norway, Portugal, Spain, Sweden,
and Switzerland
"PAL-H" : used in Belgium
"PAL-I" : used in Hong Kong and The United Kingdom
"PAL-K1" : used in Guinea
"PAL-M" : used in Brazil
"PAL-N" : used in France, Paraguay, and Uruguay
"PAL-NC" : used in Argentina
"NTSC-J" : used in Japan
"NTSC-M" : used in Canada, Chile, Colombia, Costa Rica, Ecuador,
Haiti, Honduras, Mexico, Panama, Puerto Rico, South
Korea, Taiwan, United States of America, and Venezuela

You can install nvtv from Synaptic. I think it's from the standard repositories.

---

### Post by forestpixie on 2007-12-18
open a terminal then make a backup before you do anything else :)

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.181207
```

```
gksudo nvidia-settings
```

if you're tv is recognised - it should be there - you'll need to configure it, go to Display Configuration, click the tv and then configure - make your choice between separate x screen and twinview - not sure about twinview, but separate x screen is exactly that

that works at least for an old GeForce4 MX 440, so I hope it works for you

save exit and restart

if it all goes belly up restart again in recovery mode and replace xorg with the backup and you can think again :)
, code for that is 

```
mv /etc/X11/xorg.conf.181207 /etc/X11/xorg.conf
```

I'm sure that recovery mode starts as root so you won't need sudo

---

