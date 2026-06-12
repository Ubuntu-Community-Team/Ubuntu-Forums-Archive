---
title: "trouble installing dapper on powermac G3 pismo"
date: 2006-09-08
forum: Apple PPC Users
---

### Post by ubergrafik on 2006-09-08
Hi, 

I have had trouble installing Dapper onto a G3 powerbook circa 2000. I have scoured the forums and tried several things, but with no luck. The cd-rom I have is new, and works fine in another machine, so I think it’s ok. I ckecd that i the cd i burnt was not just the iso as one big file too. Currently, there is no other OS on it, so I can't boot from one into the dapper install...

Booted, holding down the control key, and once the blue screen loads, after a time, a cd icon with a penguin on it. It is selected, then I press the arrow icon, to indicate that I want to load from that. Then, I am presented with a white screen with black text which says the following:
> 
Apple PowerBook3, 1, 2.4f1 BootROM built on 02/18/00 at 19:45:15
Copyright 1994-2000 Apple Computer, Inc.
All Rights Reserved

Welcome to Open Firmware.
To continue booting, type “mac-boot” and press enter.
To shut down, type “shut-down” and press enter.

 ok
0 > 

So, I typed mac-boot and pressed enter.
The following came on screen.

> DEFAULT CATCH!, code=300 at   %SRR0: ff80aee0   %SRR1: 0000b030
 ok
0 > 

I tried to type help, ? and many other things, but the only response is that those are unknown words etc.

I burned the alternate iso too, and tried ubuntu 5.x as well, with the same results.

Stumped...

---

### Post by ubergrafik on 2006-09-08
I have tried resetting the PRAM and NVRAM as well and it still comes up with the same issue...

I tried out a few commands in the firmware and it keeps telling me:

> unknown word

I had a look at a list of commands tat you could use and i tried those, and am still told "unknown word"

---

### Post by nkbj on 2006-09-08
Have you tried the Ubuntu 6.06.1 cdrom? A kernel bug was fixed after the initial dapper release which gave boot problems on some G3 models.

Regards,
Niels Kristian

---

### Post by gruepig on 2006-09-08
When you say the CD works fine in another machine, do you mean you can boot off of it on another machine, or just that you can read the data from it?  (If the latter, verify that you can boot to it from another computer.  Alternately, try booting the non-booting computer from another bootable disk, like one for OS X (or earlier MacOS).

Try resetting the PRAM (hold down command-option-P-R at boot and wait for chimes).  Then try rebooting from the CD.

Try holding down the C key at boot to boot from the CD.
 
From in open firmware (hold down command-option-O-F at boot), run:
```
boot cd:,\install\yaboot
```
to boot directly from the CD.  (I'm guessing that's the path to the yaboot bootloader on the CD; you can verify by mounting the CD on a working computer.)

---

### Post by h00k00 on 2006-09-08
I used Xubuntu alternate install CD, held down the C key at boot and had no problems with my Pismo. Installation went very well.

I did have some difficulties afterwards like 
[LIST]
[*]finding out where special characters are e.g. fn+alt+2=@
[*]I tried two different USB-WLAN adapters and couldn't get them working, although both work fine in my x86 laptop with Xubuntu. Cardbus adapters worked out-of-the-box, so I didn't try to solve this.
[*]To get 3D acceleration working I had to change DefaultDepth to 16 in xorg configuration
[/LIST]

---

