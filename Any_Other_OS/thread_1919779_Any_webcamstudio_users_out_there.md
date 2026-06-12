---
title: "Any webcamstudio users out there???"
date: 2012-02-02
forum: Any Other OS
---

### Post by coffee412 on 2012-02-02
Im actually running mint right now to check it out but this happens with all variations of Ubuntu. 

I cannot get sound to work with movie clips I try and play on blogtv or anywhere else. I get video but no sound. Now someone else has got to be seeing this problem or running into it before. 

1. Checked mixer settings. Nothing I can see wrong there. I have played with them until Im burned out.

2. Checked webcamstudio forums. Not too much relating to this.

3. Complete reinstalls of webcamstudio and checked codecs. No problem with codecs as I can play the video clips locally. 

Im glaring right now at adobe and thinking they just did something to bork it up. But I really cannot tell. 

If I was getting an error message in logs or elsewhere I would be able to solve this problem right away. However I dont. I also do not hear from anyone else having this problem. So, It just leaves you scratching your head and developing a nasty headache.

Be nice to hear from others running this webcamstudio and get your opinions on what this @*#)@ problem is. 

Thanks,

coffee:confused:

---

### Post by Perfect Storm on 2012-02-03
Moved to Other OS/Distro Talk.

---

### Post by coffee412 on 2012-02-08
I see this thread was moved to Other OS/Distro Talk. The problem I was having was actually also in Ubuntu too. But thats beside the point. No biggy. BUT! I think I have found a possible solution to this and I want to take the time to post what I think is the problem for anyone else having this issue.

> Recap: Webcamstudio does not play sound when streaming a video stream. Everything else works fine also works fine with webcam. Its just during streaming a video source (i.e. *.avi, *.mpg, *.ect).
Possible Solution: I remember that when it did work I was using a seperate pci sound card instead of the one built into the motherboard. Presently I have a Asus M4A88T-M LE motherboard with the following id on the sound chip:

> 00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: ASUSTeK Computer Inc. Device 8445
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at f9ff4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intelI do believe that the sound chip (or the driver) built into the mb is missing some capabilities. Therefore, Using the full pci sound card will correct this problem.

Im sure Im on the right track here as when I did use a pci sound card before my upgrade things worked fine.

Anyways, I hope this helps someone else that might be looking for an answer. Hard to believe that no one else has seen a problem like this - oh well.

If I have time tonite I will install a pci sound card and have a go at it.

coffee

---

