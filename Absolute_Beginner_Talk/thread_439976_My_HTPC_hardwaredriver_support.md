---
title: "My HTPC hardware/driver support"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by badbob100 on 2007-05-11
Asus MATX Nvidia 410/6150 motherboard, with PCI-E ATI X300 128MB videocard
A64 3700+
M-AUdio Revolution 5.1, using digital out to av pre-amp. Must send DD & DTS streams.
2.5" boot with 3.5" storage
Microsoft MCE USB IR Receiver
Keysonic 2.4ghz Wireless keyboard/trackpad
Squeezebox V3/Slimserver
APC Smart UPS, USB
URC MX-700 remote control MX Editor, must have windows emulation for this applicaiton.

Is everything above supported in Ubuntu? Can I install Linux MCE on Ubuntu 7.04? Does Ubuntu support dual screen, can I have the HTPC front end on secondary (TV) whilst Desktop is on primary? (PC monitor)

I've played around with Ubuntu in the past, but have had problems with garbled 6.06  boot CD graphics during scrolling (not the CD I think problem with ATI graphics)  6.03 worked ok.

Does Ubuntu use Cool & Quiet? I don't need the CPU to be at 2.2ghz all the time, with CAQ it reduces clock speed to 1ghz.

Also is there a FAQ for each component on exactly what to enter into command line? Is Linux ever going to drop command line, and make it more like Windows? I've been using computers since 4.7mhz XT's and glad when command line was dropped.

Does Linux have own version of ffdshow? How come it hasn't been written for linux, being that it's open source? Is there a linux version of winamp, with library support?

---

### Post by starcraft.man on 2007-05-11
Geez, thats a lot of questions... I'll try to answer what I can.

1) I do see a glaring problem with your hardware right away... the ATI card will likely still give you trouble, but if you use the alternate disk and follow this [guide]("http://ubuntuforums.org/showthread.php?t=414194") you should get  things work with a bit of effort :) If you have any problems getting it working under ATI we can help in a seperate thread that you detail whatever specific problem your having.

2)Ummmm, by linux MCE I suppose your talking about media capabilities like mythTV, and yes you can install myth support into Ubuntu it works well from the few people I know who use it, I'm no expert on it though >.>.

3) Again, I assume your going to install your ATI drivers to get dual screen support, if you can manager to get past any problems during installation and then get your drivers working you should be able to dual screen without too much difficulty. I'm an nvidia guy so can't give you specific advise on how to set it up...

4) Ya, it probably was your drivers... use the alternate cd and guide above like I said :)

5) Uhhhh, I have no experience with cool and quiet, wait for someone else to answer that/search forums/google it >.>

6) There are many FAQs about the terminal/command line, please see my sig for ubuntuguide.org and here is another [guide]("http://www.psychocats.net/ubuntu/index") I like, not specifically about terminal though. 

7) No I don't think linux is ever going to drop the command line. Its a very powerful tool and like I (and others) have answered before Linux is not about being "like" windows its about being an alternative OS like the Mac. If you want to have the windows experience, use windows please. Just a note for you btw, Vista is adopting a power shell to get a better command line, so its the one lacking...

8 ) As to ffdshow, Ubuntu has codec support for every format that exists I think, you just have to install it seperately. Check my sig it will give you the details.

9) I guess because Ubuntu has all the codecs separately available in the repos they didn't feel a need to make a single package for codecs...

10) You want XMMS, its in the repos if you want it. I've never used it though. >.>

Guess thats it, took me a while to type all that out and a bit of googling. One note, please don't expect Ubuntu to act and be exactly like Windows. If so, you will be disappointed because its not Ubuntu's goal to be a free clone of windows. My best advice is that if you have no patience for things that don't work exactly like windows, stay with windows.

Have a nice time with Ubuntu if you give it a shot, and be patient. :)

---

