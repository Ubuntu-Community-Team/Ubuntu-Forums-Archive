---
title: "Microphone Problems"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by Cre-ve on 2007-03-01
Hey guys. I was trying to use my microphone just through sound recorder. However, I can't seem to get it to work. When I hit record it doesn't record anything. Its just static. Can anyone tell me whats wrong and how i can fix it up? Thanks in advance for your reply.

The microphone does work because I used it in windows and it seems to work just fine.

---

### Post by timjayko on 2007-03-01
did you install a jack server?  to do anything with sounds you need to set up a jack server

---

### Post by The Dragon Master on 2007-03-11
Hey, this is absolute beginner talk right. What the smut is a jack server?

---

### Post by xyz on 2007-03-11
> **Cre-ve said:**
> Hey guys. I was trying to use my microphone just through sound recorder. However, I can't seem to get it to work. When I hit record it doesn't record anything. Its just static. Can anyone tell me whats wrong and how i can fix it up? Thanks in advance for your reply.

The microphone does work because I used it in windows and it seems to work just fine.
Hi,
If you care to read up on it, go here:
[JACK FAQ]("http://jackaudio.org/faq")
Also, in a terminal, type:
```
alsamixer
```
and make sure everything's on + at a sufficient level.
Use your arrows to modify. Good luck.

---

### Post by Patrick K on 2007-03-11
Actually, you don't need jack for everything. Audacity runs fine without it.

---

### Post by The Dragon Master on 2007-03-11
Well thanks for the info on JACK. Reading the JACK pages I was kind of feeling it was a red herring. :lolflag: 

Actually I got the same trouble as Cre-ve and have been searching forums for the last three hours and there are a heep of microphone threads but nothing I've read has fixed the problem.

I can hear microphone input through my speakers and have tried turning on everything in alsamixer.  But 

vumeter -r &

gives me no indication that anything is being detected at a software level.

Maybe this is useful

$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
00:13.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
01:00.0 VGA compatible controller: nVidia Corporation NV20 [GeForce3 Ti 200] (rev a3)

gnome-sound-recorder will only start if I set "sound capture' in gnome-sound-properties as silent. Obviously this kind of defeats  the point.

As I said, in alsamixer the mic volumes are on full and I've got LR CAPTUR enabled on the mic under the Capture menu (f4)

any hints greatly welcomed
TDM :o)

---

### Post by The Dragon Master on 2007-03-11
What other information might be useful here?

---

### Post by The Dragon Master on 2007-03-12
Well, somehow after a reboot the microphone seems fully functional. I'm not sure at what stage of the proceedings I hit the jackpot to get things in the good state, things only seemed to work after a reboot. I also messed with installing some webcam software prior to that reboot, but hopefully none of that influenced the good outcome. Perhaps the reboot was all that was required.

Despite not actually understanding how things got sorted out (I tried and retried the same stuff for hours) here is a list of the terminal command I have been using in the process, I hope this might be of some help to some one else out there who is struggling and feeling frustrated.

vumeter -r &                   ## Very simple visual microphone check
gnome-sound-recorder    ## A very slightly less simple sound check
gnome-sound-properties ## Saves relentless mousing through menus
                                      ## Both "playback" and "Capture" are now set to alsa
gstreamer-properties      ##  "output" and "input" now set to alsa
alsamixer                        ## arrows to navigate and set levels, 
                                      ## "m" and "space" to toggle switches
                                      ## f3, f4, f5 to toggle View
                                      ## "LR CAPTUR" switch set for "mic" under the "Capture" 
                                      ## view only (f4 and spacebar to toggle)
qjackctl                          ## Jack server. This was not required and I have removed it.

Good luck to anyone still in the maze.
TDG :confused:

---

