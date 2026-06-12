---
title: "how to change screen resolution for Nvidia?"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-02-27
I have an Nvidia card that can run at 1280 x 1024 @ 60 Hz in Windows XP but like others Ubuntu Draker forces max screen resolution into 1024 x 768 @ 60 Hz.

I installed Automatix then I could install the Nvidia drivers settings program.  But that program  only allows me selecting the CRT option, yet I'm using a TFT monitor and there's no resolution option in the Nvidia program.

I'm using this TFT 17" monitor:
[http://h10010.www1.hp.com/wwpc/au/en/ho/WF06b/1090681-1124275-1124303-1124303-1124303-12314700-66938169.html](http://h10010.www1.hp.com/wwpc/au/en/ho/WF06b/1090681-1124275-1124303-1124303-1124303-12314700-66938169.html)
How can I turn up my resolution to proper size?

---

### Post by v8YKxgHe on 2007-02-27
This is what I hate about X ... unable to change resolution 'on-the-fly'. Ok, in terminal do:

```
gksudo gedit /etc/X11/xorg.conf
```

Then find:

> Section "Screen"

and look for something like this:

> SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection


See where it says Modes? Put "1280x1024" infront of "1024x768" like I have.

Regards,

---

### Post by kinson on 2007-02-27
Is there any way to adjust the frequency too?

I can get "1280x1024" on mine, but at 60hz only...and that kinda hurts my eyes. I'd be happy with something like 72/75hz.

Cheres,
Kinson

---

### Post by igknighted on 2007-02-27
60hz is the standard for an LCD display IIRC... im not sure its wise to attempt 72/75 hz

EDIT:  If you know the frequency ranges of your monitor, you can manually add them to xorg.conf, as they might not have been detected properly.  Don't do this unless you know for sure what they are, as you could damage you monitor (or X wont start).

---

### Post by kinson on 2007-02-27
> **igknighted said:**
> 60hz is the standard for an LCD display IIRC... im not sure its wise to attempt 72/75 hz

EDIT:  If you know the frequency ranges of your monitor, you can manually add them to xorg.conf, as they might not have been detected properly.  Don't do this unless you know for sure what they are, as you could damage you monitor (or X wont start).

Bleh, my mistake, sorry. Its not 1280x1024 (I was wondering why you were talking about LCD's). I'm using a 4:3 CRT monitor. When I installed Ubuntu, it defaulted to the 1280(or something) resolution @60hz, now I'm running 1024x768@72(or something)hz. I just wanna push it one higher(like what Ubuntu defaulted to in my monitor) at 75hz. 

Under the display settings in Ubuntu, I have the option to push it one higher than 1024x768, but it doesn't allow me a higher frequency range :(

---

### Post by igknighted on 2007-02-27
> **kinson said:**
> Bleh, my mistake, sorry. Its not 1280x1024 (I was wondering why you were talking about LCD's). I'm using a 4:3 CRT monitor. When I installed Ubuntu, it defaulted to the 1280(or something) resolution @60hz, now I'm running 1024x768@72(or something)hz. I just wanna push it one higher(like what Ubuntu defaulted to in my monitor) at 75hz. 

Under the display settings in Ubuntu, I have the option to push it one higher than 1024x768, but it doesn't allow me a higher frequency range :(

Do you have a manual for the monitor?  If you don't, try the manufacturer's website.  Your other option would be to run 'sudo dpkg-reconfigure xserver-xorg' and try to set up the screen res and refresh as best you can (preferably in advanced mode with your monitor's stats, but if you can't find those, try the 'medium' level, it might help.

EDIT: Also, what graphics driver are you running?  If its an open one (like ati/radeon or nv) it might not support that high a res/freq.

---

### Post by jingo811 on 2007-02-27
Editing xorg.conf didn't work for my Nvidia card it's still the same resolution even when doing it GUI wise after configuration in file.  Even after reboot. :( 
> Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV40 [GeForce 6200?]"
    Driver         "nvidia"
    Option	   "NoLogo"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40 [GeForce 6200?]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
 [COLOR="Red"]   SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection[/COLOR]
EndSection

[IMG]http://i16.tinypic.com/4344uwp.png[/IMG]
[http://i16.tinypic.com/4344uwp.png](http://i16.tinypic.com/4344uwp.png)

---

### Post by jingo811 on 2007-03-07
bump 1. editing that file still doesn't reveal higher resolutions for my Nvidia card.

---

