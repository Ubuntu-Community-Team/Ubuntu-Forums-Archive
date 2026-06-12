---
title: "Force a higher refresh rate?"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by Drevix on 2007-09-03
I'm still having a minor problem with my screen resolution. (I ran Envy and that improved things) I'm running at 1024x768 but I can't get my refresh rate above 85Hz.  I normally run at 1024x768 at 100Hz, in WinXP anyway. Everything still has a little bit of fuzziness to it. I though it might be a font problem but I'm using the exact same fonts and styles that I'm using in my WinXP desktop, and that's clear and sharp. Is there any way I can force my refresh rate up to 100Hz?

I'm not exactly sure what information from which configuration file to include here, I'm still new at this stuff, so if someone could say what it is that needs to be seen I'll post it.

---

### Post by ddrichardson on 2007-09-03
If you backup /etc/X11/xorg.conf and then change the horizontal and vertical refresh rates to those for you monitor you should be able to get the required modes.

---

### Post by Drevix on 2007-09-03
No need to do that, it's already there. Here's the monitor,device, and screen sections of my xorg.conf file. The HorizSync and Vert Refresh values are correct. I don't know if this matters, but my video card is actually a Geforce4 MX 440 SE.

Whenever I start Ubuntu and go to my Nvidia settings under system tools it always resets to auto config no matter what I do. If I go to system/preferences/screen resolution first, it only shows the refresh options as 50-56 Hz. If I go  back to Nvidia settings and re-select the refresh rate of 85Hz, which is the highest that shows there, I get the quick flick on the monitor and the "Do you want to keep this resolution setting" thing that shows it changed. If I go back to system/preferences/screen resolution after doing that it then shows I'm at a refresh rate of 103Hz, which I'm almost certain isn't running at that rate. Weird stuff, and I can't figure out what's going on.


Section "Monitor"
    Identifier     "Mitsubishi Diamond Plus 72"
    HorizSync       30.0 - 86.0
    VertRefresh     50.0 - 130.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA GeForce4 MX 440"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA GeForce4 MX 440"
    Monitor        "Mitsubishi Diamond Plus 72"
    DefaultDepth    24
    Option         "UseFBDev" "true"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by nonewmsgs on 2007-09-03
Section "Monitor"
Identifier "Mitsubishi Diamond Plus 72"
HorizSync 30.0 - 86.0
VertRefresh 50.0 - 130.0
Option "DPMS"
EndSection


look up your moniter model's specs and it will list the horizSync and vertrefresh and change those numbers to the right ones.

---

### Post by ddrichardson on 2007-09-03
Look into the differences between the MX440 and MX440SE - it may be a slightly different timing that's affecting the mode.

NVNews has quite good linux support forums you may get a good response [here]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14").

---

### Post by Drevix on 2007-09-03
The HorizSync and VertRefresh values are correct for my monitor, absolutely no doubt of that.

---

### Post by nonewmsgs on 2007-09-03
hmmm.   that's weird.

---

### Post by Drevix on 2007-09-04
ddrichardson -

So far as I could find they're basically the same card. The SE has a slightly lower transfer rate, and has the S-video output. It's very hard to find detailed spec information, and I'm not sure a comparison would do me any good. The Nvidia control panel I have in my windows allows me far greater access to settings. Besides the standard timing schemes, I can access and configure the front/back porch, sync polarity, sync width, front end active, on both the horizontal pixels and vertical lines. Plus I can override the default refresh rate for whatever resolution mode I'm in. Generally it's not wise to mess with those setting unless you really know what you're doing. ;-)

With Linux I have no idea what kind of timing schemes it uses, much less how to access and configure it. I'm assuming that at some point it must use some sort of video timing method, but how and where eludes me. At present my display is what I consider to be barely above an acceptable level, and there doesn't seem to be much I can do about improving it. I don't know if it's a software/driver limitation with Linux or my lack of knowledge with the Linux OS. I've only been at it for a little over a week, there's still far too much I don't know – yet.

---

### Post by ddrichardson on 2007-09-04
Linux or rather Xorg, uses modelines to specify resolution, pixel clock, x adn y resolution. Xorg in its present incarnations is better at automatically detecting this correctly. There is a calculator [here]("http://amlc.berlios.de/") which may be worth a try. 

FWIT the MX440SE is not strictly a [MX440 its an MX420 with increased memory bandwidth]("http://en.wikipedia.org/wiki/MX440#GeForce4_MX").

---

### Post by Drevix on 2007-09-04
The AMLC seems to have worked. I had a little trouble downloading and setting up to run it but I was able to after a short bit. No problems with adding the output text to my xorg.conf file, restarted and the modes came up fine, set it to 1024x768 at 100Hz (actually 105Hz). I know that worked because I had to resize my display. Somewhat of a pain in the butt using my monitors controls, I could never quite get it aligned perfectly squared. I still need to tweak my fonts, but I'll see how it goes with some graphics.

---

### Post by ddrichardson on 2007-09-04
Glad it helped, I don't normally recommend extra software but calculating modelines is overly complicated. I think that the problem lies in the autodetection of the card, as the MX440SE is really an MX420.

---

### Post by Anubis on 2007-09-10
> **Drevix said:**
> modes came up fine

Glad your happy with your fix. However, what do you mean by the above quote? Does that mean Ubuntu menu item for screen resolution and refresh rate not gives you valid options? Thats what I was following the thread to find out? Because I have the correct modes and refresh rates, but the menu still gives bogus refresh options, and I followed all the steps. Pretty sure I have my monitor running at 85mhz. Nvidia-settings confirms this, but again, ubuntu resolution menu does not give valid options.

---

