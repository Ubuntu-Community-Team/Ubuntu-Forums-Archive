---
title: "Quicksilver G4: No Video"
date: 2011-10-29
forum: Apple Hardware Users
---

### Post by Elkaintmoose on 2011-10-29
I feel like I should be able to find the answer to this somewhere, but a few hours of searching have left me still in the dark, so I thought I'd go ahead and ask:

I've got Xubuntu 10.10 installed on my Quicksilver G4 with a GeForce4 MX 440 graphics card. When I boot the computer, I get no video at all -- not even the yaboot text. It's running, though, and I've got SSH access, so I can log in from another computer.

It was running an earlier version of Xubuntu and displaying video fine. I upgraded to see what would happen and, well, this happened. Nothing mission critical; I could wipe and reinstall something, but I'd like to get this running, if I can.

I've changed /etc/X11/xorg.conf to:


```
Section "Device"
Identifier "Configured Video Device"
BusID "PCI:0:10:0"
Driver "nv"
EndSection

Section "Monitor"
Identifier "StudioDisplay17"
Option "DPMS"
HorizSync 30-80
VertRefresh 50-100
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "StudioDisplay17"
Device "Configured Video Device"
DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 16
		Modes "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
Identifier "DefaultLayout"
Screen "Default Screen"
EndSection

Section "DRI"
Mode 0666
EndSection
```

But I get an error in Xorg.0.log that reads:

```
(--) NV: Found NVIDIA GeForce4 MX 440 at 00@00:10:0
(EE) NV: Kernel modesetting driver in use, refusing to load
(EE) No devices detected.
Fatal server error: no screens found
```

This seems to be a problem, but I can't figure out what it means. Can anyone interpret?

Thanks!

---

### Post by rsavage on 2011-10-29
I try to explain video here: [http://ubuntuforums.org/showpost.php?p=11020435&postcount=1](http://ubuntuforums.org/showpost.php?p=11020435&postcount=1)
 
Xorg.conf has no affect on yaboot text.  Do you mean the 'press l for llinux' etc which is the yaboot text?
 
Things you can try: adding nouveau.modeset=0 to turn off kms.  Or change 'nv' to 'nouveau' in your xorg.conf.
 
Let us know if it works or you need more help!

---

### Post by rsavage on 2011-10-29
Also, if you have more than one dvi port..... [http://ubuntuforums.org/showthread.php?t=1867383](http://ubuntuforums.org/showthread.php?t=1867383)

---

### Post by Elkaintmoose on 2011-10-29
Thanks for the replies! I'm just passing through, so I'll read your big post when I've got more time, but I just wanted to clear up that one point—yes, I see NO text EVER on the screen. The yaboot text is missing, and the screen is off, effectively. I figured that xorg.config doesn't load until later, which is why I thought it was odd that I'm not even seeing a "press l for linux" prompt.

I did try changing nv to noveau, and adding noveau.modeset=0 to yaboot earlier, with no luck either. (Sorry, should have mentioned that.)

---

### Post by rsavage on 2011-10-29
You've got me a bit stumped I'm afraid, but that doesn't mean much!

I don't understand why you don't see any yaboot text?  Does the screen flicker at any point between white and black or is it just black all the time?

I'm kinda thinking it's some sort of hardware thing.  The cable has become unplugged or something.  Have you tried swapping to a different dvi slot or using a different sort of connector if you can?

---

### Post by Elkaintmoose on 2011-10-30
Yeah, it's starting to seem like hardware. I've replaced the hard drive with one with a known working OS on it, and still no monitor. Starting from CD, or with option held down, no video. Something else is up, it seems. 

The power light on the Studio Display is on, and the brightness control lights up when I touch it -- might that be indicative of a video card issue? Can video cards catastrophically fail like that? (One minute working, next not?) This is beyond the purview of this forum, surely -- just thought I'd ask in case someone had experience with this.

I'll haul the thing into work this week and hook it to a VGA monitor and see what I get.

---

### Post by rsavage on 2011-10-30
Stab in the dark here (I'm not a mac person really!) - what about trying resetting the pram/pmu....?

---

