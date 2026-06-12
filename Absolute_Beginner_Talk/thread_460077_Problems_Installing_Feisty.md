---
title: "Problems Installing Feisty"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by Aurora Borealis on 2007-05-31
I'm trying to install CE Feisty, but the installation window is so huge the bottom hangs off the screen so I can't access the buttons. All the usual methods don't work for this: dragging the edges or a corner, using the resize option...nothing. Ironically, I can resize windows I open from the start menu, such as browser screens or the help frame, but for some reason, not the install window. So I can't finish the install because pressing enter doesn't enter my information, but keeps opening the time zone menu. Anyone know how to fix the install window?

---

### Post by seetho on 2007-05-31
Under Gnome you can hold down Alt key and then left mouse click (and hold down) on anywhere in a window and drag it around.

If you have problems installing with the LiveCD then you should use the Alternate CD and install in text mode.  It is much faster and cleaner.

---

### Post by Inxsible on 2007-05-31
> **Aurora Borealis said:**
> I'm trying to install CE Feisty, but the installation window is so huge the bottom hangs off the screen so I can't access the buttons. All the usual methods don't work for this: dragging the edges or a corner, using the resize option...nothing. Ironically, I can resize windows I open from the start menu, such as browser screens or the help frame, but for some reason, not the install window. So I can't finish the install because pressing enter doesn't enter my information, but keeps opening the time zone menu. Anyone know how to fix the install window?
 
Maybe your screen resolution isnt set right. Why dont you change the screen resolution to an acceptable level before you start the installation process.
 
Maybe that could help !

---

### Post by Aurora Borealis on 2007-05-31
> **seetho said:**
> Under Gnome you can hold down Alt key and then left mouse click (and hold down) on anywhere in a window and drag it around.

If you have problems installing with the LiveCD then you should use the Alternate CD and install in text mode.  It is much faster and cleaner.
 Thank you for your reply. Yep-I tried the alt trick, too. Maybe I will have to use the alternate. Will I still have gui after?

---

### Post by Aurora Borealis on 2007-05-31
> **Inxsible said:**
> Maybe your screen resolution isnt set right. Why dont you change the screen resolution to an acceptable level before you start the installation process.
 
Maybe that could help !

Thank you for your reply. Okay-I'll try it. Is it going to mess it up for the other installs? I have edgy, I've used fedora, everything looks okay, so if I change it, will it change it for everything else, too? (Yep, I'm a computer dummy.)

---

### Post by Aurora Borealis on 2007-05-31
What should I set it to?

---

### Post by seetho on 2007-05-31
> **Aurora Borealis said:**
> Thank you for your reply. Yep-I tried the alt trick, too. Maybe I will have to use the alternate. Will I still have gui after?

The test mode install is basically the same as the gui install except that everything is done in text mode.  It is a guided install so should not be hard.

After successfull install you will restart into your brand new Gnome desktop.  Good luck.

---

### Post by Inxsible on 2007-05-31
> **Aurora Borealis said:**
> What should I set it to?
 
Whats the size of your monitor ?
 
i think 1280x1024 would be good. Depends on your monitor size tho.

---

### Post by seetho on 2007-05-31
> **Aurora Borealis said:**
> What should I set it to?

As long as you can get it to at least 1024x768 you are good to go.  You can fix the resolution later after the install.

---

### Post by Aurora Borealis on 2007-05-31
Okay-I went to screen resolution and it has a drop down menu with only two resolutions: 800x600, and 640x600. Is there a way to add to the drop menu and get the right resolution? I checked the help and it said to use the drop-down, but this doesn't have the right resolution.

Edit: the monitor is 17 inches.

The thing is, I can't finish the install because I can't get to the buttons on the bottom. Except you did mention there was another kind of install available-the text mode. I'll see if I can get that.

---

### Post by Inxsible on 2007-05-31
> **Aurora Borealis said:**
> Okay-I went to screen resolution and it has a drop down menu with only two resolutions: 800x600, and 640x600. Is there a way to add to the drop menu and get the right resolution? I checked the help and it said to use the drop-down, but this doesn't have the right resolution.

So its definitely the screen resolutiion that is the problem. You will need to edit the xorg.conf file to add more resolutions.

But before that, what size is your monitor, and what is the maximum size you KNOW your monitor supports ?

---

### Post by seetho on 2007-05-31
You could just install in text mode using the alternate CD.  Leave the tweaking till after you get the system up.  It's really not that difficult.

---

### Post by Inxsible on 2007-05-31
> **seetho said:**
> You could just install in text mode using the alternate CD.  Leave the tweaking till after you get the system up.  It's really not that difficult.

I'd second that recommendation !!

---

### Post by Aurora Borealis on 2007-05-31
the monitor is 17". I don't know what the maximum it allows is, but I hit the options button on the monitor (It's a Dell) and it said what the resolution is set to and that the optimum is 1280x1024. That sounds like a big difference to me. I didn't see a way to change it on the monitor itself, though. How do I alter the xorg.conf file? I'll see if I can get the alternate cd. The thing that confuses me is that 17" isn't  particularly unusual size.

---

### Post by Inxsible on 2007-05-31
```
gksudo gedit /etc/X11/xorg.conf
```
 
Look for a section that looks somewhat like this
```

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    #Enable 32-bit ARGB GLX Visuals
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```
 
Add the resolution that you know your monitor can support. Make sure you have the proprietary drivers installed first. Add the higher resolutions before the lower ones

---

### Post by Aurora Borealis on 2007-05-31
Thank you for the information. Hm. I have the right settings there-just not in the pull-down menu. I don't know. Oh well.

---

