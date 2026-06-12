---
title: "DirectX 8/9"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by OptimusPrime on 2006-11-13
Is there any way to install DirectX on linux?  I tried though Wine, and it looked good, but when I go to play Guild Wars, it says I need direct X 8, or an updated video card. I just did the video card, so I need DirectX.

---

### Post by CatKiller on 2006-11-13
[http://appdb.winehq.org/appview.php?iAppId=2243](http://appdb.winehq.org/appview.php?iAppId=2243)

---

### Post by OptimusPrime on 2006-11-13
That didn't really say much.  It doesn't really talk about Wine or anything.

---

### Post by CatKiller on 2006-11-13
> **OptimusPrime said:**
> That didn't really say much.  It doesn't really talk about Wine or anything.

You mean, apart from it being Wine's application database entry for Guild Wars, telling you what works and what doesn't, and how to get the bits that do work to work? Apart from that, you mean?

---

### Post by BLTicklemonster on 2006-11-14
Okay, so how do I get directx installed in wine, just click a link and have at it?

---

### Post by pay on 2006-11-14
Wine has it's own version of DirectX built in. I don't think that you can install the Windows version of directX in wine.

---

### Post by pay on 2006-11-14
@OptimusPrime
Did  you miss this?

Simple How To:
by RD on Monday October 2nd 2006, 21:48
Here is what I did to get Guild Wars to work...

1. Install wine v0.9.22

2. Install Guild Wars by either CD or Downloaded Client

3. Setup winecfg as follows:

Application Compatability
==========================
Windows98(Selected)

Graphics
===========
Allow DX App to stop the mouse leaving their window(Checked)
Enable Desktop Double Buffering(Checked)
Allow the window manager to control the windows(Checked)
Emulate a virtual Desktop(Up to you, but I find it better not to use this and just let GW run in Full Screen)
Vertex shader support(None)
Allow pixel shader(Unchecked)

Audio
======
ALSA Sound Driver Hardware Acceleration(Full)
Default Sample Rate(I've used 22050 and 4100)
Default Bits per sample (8 or 16)
Driver Emulation(Checked)

4. To run Guild Wars I type: wine C:\\Program\ Files\\Guild\ Wars\\Gw.exe

I am running GW with:
=======================
Suse 10.1
nvidia x86 drivers v1.0-8776
wine 0.9.22
AMD AthlonXP Barton 2600+
GeForce 4 MX440

---

### Post by JafaarNhh on 2008-04-05
Do you know how i have to do for playing talesofpirates:confused:

i downloaded it and played but the graphic isnt good it lagss al the time:(

---

