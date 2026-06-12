---
title: "Setting up a TV card, and viewer"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by Foudre on 2007-03-23
Ok so here's the issue, I have a old school wintv card, I fixed a freinds computer, i'm returning back to college over the week end after spring break so  I don't have much time to fix this up. Ok any one know of a good tv viewing programme, I have kdetv installed but it freezes every time i try to use it (back when this computer used to be mine i had suse on it and this programme worked well, but suse had a section under hardware for tv cards, kubuntu doesn't) I must say though yast was slow and a back package manager it was good for hard ware. 

So has any one gotten a tv card working on their ubuntu,, and what soft ware are you  using/ how do i even check to see if its installed on this blasted dumbed down operating system (ubuntu has its up sides, but some of the simplifications are cumbersome),

---

### Post by fenian on 2007-03-23
TVTime is the best tv viewing app.Type lspci in a terminal to see if the card is recognized.

---

### Post by Foudre on 2007-03-23
hmm i can see the devices in the list of stuff, but it doesn't know what it is, how would i go about setting this up, you know?

0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 735 Host (rev 01)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
0000:00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
0000:00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
0000:00:0b.0 USB Controller: NEC Corporation USB (rev 43)
0000:00:0b.1 USB Controller: NEC Corporation USB (rev 43)
0000:00:0b.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0000:00:0d.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
0000:00:0f.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:00:0f.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
0000:00:13.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
0000:00:13.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
0000:00:13.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 5940 (rev 01)
 thats what outputs, and tvtime doesn't get the signal, i know the tv card is the brook tree thingy cause i reconize Bt878 from the windows drivers, plus it comes in a sound and audio one seperatly like i know it is, so based on this how do i tell ubuntu thats what it is

---

### Post by Foudre on 2007-03-23
hmm also i'm getting a problem, with dvd play back, when ever i try to play one kafeine / xine / vlc all like just close, these might be realated, well the issue with kdetv freezing i mean, not the fact that the card isn't being used right

---

