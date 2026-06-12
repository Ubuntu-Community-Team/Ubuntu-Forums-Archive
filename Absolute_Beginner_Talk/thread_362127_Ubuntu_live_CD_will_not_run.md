---
title: "Ubuntu live CD will not run"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by nailzs on 2007-02-15
My new computer I built last year will not run any Ubuntu live CD or DVD beyond Dapper.  I get these error messages.

[IMG]http://img59.imageshack.us/img59/4809/image001ev3.jpg[/IMG] [IMG]http://img204.imageshack.us/img204/7483/image004vy6.jpg[/IMG]

This is my computer specs..

DFI LanParty UT NF4 Ultra
AMD Athlon 64 X2 Dual Core 4400+ 255X10 1.33V
OCZ PC3200 1024X2 EL Dual CH Platinum 2-3-2-5
Connect3D X800 XL
Sound Blaster Audigy2 ZS
Arctic 64 Freezer Pro Heatpipe CPU Cooler
Zalman VF900-CU Dual-Heatpipe VGA Cooler
Thermalright HR-05-SLI Chipset Heatpipe
Hiitachi 160GB SATA II

Is there any way to resolve to this problem?

I'll add my "old" computer has no problem with any version of Ubuntu from Dapper to Fisty 7.04.
It's specs are..

AMD XP 2500-333 (200x11@1.675v)
Thermaltake Silent Boost CPU Cooler
Abit NF7-S V2.0
Mushkin 1gig PC3500 Level II 2x512MB (11-2-2-2@2.7v)
Sapphire Radeon 9800 Pro 128meg 8X AGP (380X340)
Arctic VGA Silencer Rev.2 GPU Cooler
Maxtor 160MB ATA/133

---

### Post by mikewhatever on 2007-02-15
The problem is well explained at Herman's site [http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)
Try reconfiguring xserver for the Live CD session.
It seems to be a common issue with ATI cards. I'd suggest trying an Alternate CD installer, which is the text mode installer with no fancy graphics of the Live cd. You can download it from Ubuntu download page and use Herman's site for installation instructions.
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
Hopefully, this way you'll be able to install Ubuntu on your new PC and then deal with ATI driver problems. You can't run a live session with that kind of cd though.

---

### Post by fromp on 2007-02-15
I also have a problem with the live cd. every time it starts to boot, i get Grub error message and it freezes. Is there any way to bypass the test drive and just install it once it boots from the cd?

---

### Post by mikewhatever on 2007-02-15
> **fromp said:**
> I also have a problem with the live cd. every time it starts to boot, i get Grub error message and it freezes. Is there any way to bypass the test drive and just install it once it boots from the cd?

As you can see, nailzs does not have any GRUB errors. It may be possible to solve your problem by explaining it in details and thus giving others the chance to help you.

---

### Post by darkcyber on 2007-02-15
nailsz,

This is the exact same problem I ran into trying to install on two older pc's.  Here's the thread I started a while back.

[http://www.ubuntuforums.org/showthread.php?t=353946](http://www.ubuntuforums.org/showthread.php?t=353946)

Sounds like there maybe a solution posted in this thread. Thanks for the help!

---

### Post by fromp on 2007-02-15
good luck.

ill make a new thread about my problem then

---

### Post by volksman on 2007-02-15
easy fix for this:

On boot use F6 option and replace "quiet - splash" with "break=bottom" .  You will get a prompt halfway through the boot at which point you can issue:

chroot /root nano etc/X11/xorg.conf

and replace any instance of 'ati' with 'radeon' (under Device driver heading).

---

### Post by nailzs on 2007-02-15
> **mikewhatever said:**
> The problem is well explained at Herman's site [http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)
Try reconfiguring xserver for the Live CD session.


This is the outcome from what I got at Herman's site.

[[IMG]http://img258.imageshack.us/img258/3996/image001na8.th.jpg[/IMG]](http://img258.imageshack.us/my.php?image=image001na8.jpg)

This was the 6.10 DVD version. Everything was detected correctly but the outcome was the same as before, The GUI would not start

---

### Post by mikewhatever on 2007-02-16
> **nailzs said:**
> This is the outcome from what I got at Herman's site.

[[IMG]http://img258.imageshack.us/img258/3996/image001na8.th.jpg[/IMG]](http://img258.imageshack.us/my.php?image=image001na8.jpg)

This was the 6.10 DVD version. Everything was detected correctly but the outcome was the same as before, The GUI would not start

As you can see, it is not happy with the loaded driver. Because the driver is wrong, it can't see the graphic card and the screen. You can try choosing a different option for the driver and see what you get out of a live session. Search the forums and google for your graphic card specs, you may find something. By the way, I get exactly the same error when trying to reconfigure xserver for my nvidia card, so I just installed the latest driver manually and it worked.

---

### Post by nailzs on 2007-02-16
I had read using Vesa drivers instead of the listed ATI drivers would work, but it got the same result. 
I suppose I could install the command line version and build the GUI from there, and make the driver install easier using Envy.

---

### Post by nailzs on 2007-02-17
Well whoop dee do! I'm writing this from the latest Feisty release live CD, build 4 I believe. I'm impressed. Thanks Ubuntu dudes!

---

