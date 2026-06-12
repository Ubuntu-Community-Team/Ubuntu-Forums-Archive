---
title: "Can't apply visual effects with radeon HD4500"
date: 2009-11-29
forum: Beginner Team
---

### Post by Allyanora on 2009-11-29
Hello, I am a beginner to Ubuntu, I have just upgraded it to version 9.10 and i don't know what is wrong. first, before upgrading, i had sound problems. now I cannot apply visual effects. when i click to apply, it says to me that "Desktop effects cannot be enabled". My mouse looks kind of weird, like it is fractured or something, it is not really full, and so some of radio-buttons when I find on a web-page or other check-buttons and stuff. 

I don't think that my video card does not support this, especially that i don't have it on-board. I have a Dell studio 1555 laptop with this video card:   ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series].

is it really the video card or the Ubuntu is wrongly installed?

---

### Post by ajgreeny on 2009-11-29
9.10 and some ati cards do not mix very well.  If you are using the open source radeon driver that was used immediately when you installed, that may be the problem, and you may need to use the Hardware Drivers utility to install the proprietary driver, but I do not know enough about your card to say for certain what you need.

---

### Post by Allyanora on 2009-11-29
Does anyone know what should I do or search in my computer to give you the information to help me? Because I didn't manage to find on the internet my answer :(

---

### Post by dummy910 on 2009-11-29
The box I type this from has a Radeon 9600 with the RV350 chipset and ALL the 3D visual effects can be enabled if the user chooses to do so.

Here's their xorg.conf file in /etc/X11:
> #   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "ati"
EndSection
Note, this is the default file and drivers that Ubuntu 910 installed, no outside video drivers or tweaks applied, and it all works just fine.

---

### Post by Allyanora on 2009-11-29
> **dummy910 said:**
> The box I type this from has a Radeon 9600 with the RV350 chipset and ALL the 3D visual effects can be enabled if the user chooses to do so.

Here's their xorg.conf file in /etc/X11:
Note, this is the default file and drivers that Ubuntu 910 installed, no outside video drivers or tweaks applied, and it all works just fine.


hmm. didn't manage to do that. I'm afraid I have to install a fresh copy all over again, the version 9.10 from the start, not the updated 9.04 one.  

in my xorg.conf file is this:

#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

If any other ideas... I am open to them.

---

### Post by Shekibobo on 2010-09-02
I'm also having this problem.  Desktop effects don't work for me, and visual processing is pretty slow in general for my HD4500 on a Toshiba Satellite laptop.

Did you ever get this figured out?  I found that using Ubuntu Tweak, and selecting the XUpdates ppa source, then updating, is great for the actual graphics.  Everything ran wonderfully. *However*, every time I booted up, I had to restart X.  My computer would tell me that it was running in "low graphics mode," even though the login splash was at 1600x900 resolution, rather than the 800x600 I seem to be getting now.

I recently reinstalled ubuntu partly because of this inescapable problem, but now I'm back to having crappy graphics, even with the proprietary drivers installed.  Does anyone have any idea?  Maybe someone's figured this out?  I really like the X Update drivers, but I really hate all the extra steps based on conditions that are so obviously false.

---

### Post by Shekibobo on 2010-09-02
Interesting fact.  I just disabled the proprietary drivers and rebooted without doing any of the XUpdate installs.  Everything seems to be working great now.  Boot up works fine, everything's hi-res.  The ATI Catalyst drivers just suck, apparently.  Stay away from them on Ubuntu.

---

