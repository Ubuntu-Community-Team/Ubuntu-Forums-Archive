---
title: "Resolution Problems"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by orangeLemon on 2007-11-14
For some reason after I enabled my graphics driver my resolution kind of messed up. For some reason no matter what model monitor I select under Screens and Graphics in System > Administration, it only works at the two resolutions 800x600 and 1600x1200, the first of which is too small, the second of which is too big. However if I disabled my graphics driver it'll let me pick the right resolution (any actually.) Any idea how I could fix this? I once was able to "almost" fix it, getting the resolution to 1024x768, but for some reason it won't fit on the screen, meaning when I moved the mouse to the edge of the screen it scrolls down the screen.
Graphics card - Nvidia Geforce 4 MX Integrated
Driver - nvidia glx
Monitor Driver - Plug'n play (Tried a lot of different ones though)
If any more information is needed let me know.

---

### Post by alienexplorers on 2007-11-14
Enable your graphics driver and run from terminal:
> gksudo nvidia-settings
use this to select your resolution and refresh rate.

---

### Post by orangeLemon on 2007-11-14
> **alienexplorers said:**
> Enable your graphics driver and run from terminal:

use this to select your resolution and refresh rate.
And how exactly do I do that? I tried by myself but it wasn't exactly straight forward, I saw nowhere to just change the resolution. I went to the X Server Display Configuration > Resolution, but the only two options were Auto and Off, and off was grayed out so I couldn't pick it.

---

### Post by Inxsible on 2007-11-14
> **orangeLemon said:**
> And how exactly do I do that? I tried by myself but it wasn't exactly straight forward, I saw nowhere to just change the resolution. I went to the X Server Display Configuration > Resolution, but the only two options were Auto and Off, and off was grayed out so I couldn't pick it.For me the options are Auto, Off and all the possible res configs.

To state the obvious, did you scroll down the list?

if yes and its still not there, you may wanna start with a clean slate.

---

### Post by orangeLemon on 2007-11-15
> **Inxsible said:**
> For me the options are Auto, Off and all the possible res configs.

To state the obvious, did you scroll down the list?

if yes and its still not there, you may wanna start with a clean slate.

I obviously scrolled down, but still nothing. I've tried installing from a clean slate. In fact I upgraded from feisty to gutsy and had the same problem, but I thought it was an error during the upgrading so I burnt a CD and installed on a clean partition, and I still have the same error. I'm starting to think it's something to do with my graphics card, since when it's enabled (on any driver) 3D games still won't work.

---

### Post by alienexplorers on 2007-11-15
In your xorg.conf add the following line to your monitor section:
> Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync

To change to another refresh rate run:
> [http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php)

Then try running gksudo nvidia-settings and the resolution and refresh rate should be listed.

---

### Post by orangeLemon on 2007-11-16
> **alienexplorers said:**
> In your xorg.conf add the following line to your monitor section:

To change to another refresh rate run:


Then try running gksudo nvidia-settings and the resolution and refresh rate should be listed.
Nope didn't help anything. It's amazing that my graphics driver was enabled for about a week and everything was working fine, I could pick any resolution, visual effects (Wobbly windows, 3D Cube) worked perfectly, and now for some reason it's messed up. Seems like every Linux Distribution has it out to get me, PCLinux won't work right with OpenOffice, and my mouse moves annoyingly slow, Fedora didn't want to show my Windows Partition, and Ubuntu doesn't want to enable my graphics card. 

I have however been able to set the resolution to 1024 x 768, but it is still set to a 800x600 resolution, meaning that it'll still pan across if I move my mouse to the edge of the screen.

---

### Post by orangeLemon on 2007-11-19
Tried fixing it without help, ended up messing up so bad I had to delete the Linux Partition. Planning on reinstalling, but I know for a fact the problem will still persist (it has on previous reinstalls), so any other ideas on what the problem could be?

---

### Post by orangeLemon on 2007-11-21
Reinstalled, and confirmed that the problem persists. Anybody know the answer yet? Also now if I set the desktop effects (wobbly windows, etc) on, the top of the window (where open, close, minimize is located) is not there.

---

### Post by unxzst on 2007-11-21
same problems here. my available resolutions range from 320x240 through 640x480 including auto...
i cant read the crash report, because its locked. what sort of driver do you have? i have nvidia2 go. i can see on the svga, but also at reduced resolution.

---

### Post by orangeLemon on 2007-11-22
> **unxzst said:**
> same problems here. my available resolutions range from 320x240 through 640x480 including auto...
i cant read the crash report, because its locked. what sort of driver do you have? i have nvidia2 go. i can see on the svga, but also at reduced resolution.
The nvidia-glx is the driver I'm using (if that's what you mean) which was automatically picked up, and I've tried to others and they won't work either. Mine also ranges from 320x240 and 640x480 at some times, it pretty much randomly picks two resolutions every time I try to fix it. Once there was some resolution like 2056 x 1678 (not exactly, but something like that.)

---

