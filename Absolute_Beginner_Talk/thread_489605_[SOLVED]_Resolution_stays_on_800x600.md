---
title: "[SOLVED] Resolution stays on 800x600"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by bioShark on 2007-07-01
Hi

I am a Linux n00b. I have just installed Feisty 7.04. The installation has gone smoothly, I have made the updates and everything. I have also installed the Nvidia drivers.
I have as video card Nvidia GeForce MX 440.
When I go to System -> Preferences -> Screen Resolution, I have only 800x600 @50 to select from.
After I've installed the drivers when I go to Application -> System Tools -> NVidia settings, I can't select as resolution only "Auto". I guess there it doesn't see my display device, because I can see as description @@@ at 800x600. I have a Dell P780 monitor.
My xorg.conf file in the "Display" section looks like this:

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV17 [GeForce4 MX 440]"
    Monitor        "DELL P780"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
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
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


I don't know what else I could do...but my eyes are starting to hurt me. I hope I have posted all the necessary info, and hope that soon you can give me a solution.

c.u.

---

### Post by moore.bryan on 2007-07-01
[I]this is a common problem, so don't fret; however, it can take a little patience to get it working.
try
```
sudo dpkg-reconfigure xserver-xorg
```
most of the defaults should be good... then restart your xserver with ctrl+alt+backspace and type startx at the prompt.
[/I]

---

### Post by bioShark on 2007-07-02
Hi

I have used that comand already... it configures the xorg.conf file from the beginning, right? But maybee at some point I got tired because after restarting the X server (crtl+alt+backspace) it crashed. So I did a recover of the old xorg.conf file.
Anyway I have noticed that you said that after restarting the xserver with ctrl+alt+backspace yu need to type in startx at the prompt. Well this is not my case, because when I restart the xserver, ubuntu goes back to the login page. No prompt line is visible.

c.u.

---

### Post by moore.bryan on 2007-07-02
[I]okay, well that tells me something.  do you have an intel chip?  if so, the 915resolution package might help.  there are also the [modeline program]("http://xtiming.sourceforge.net/cgi-bin/xtiming.pl") which can help you put a line in your xorg.conf file to force ubuntu to recognize the monitor's specs...

[this post]("http://ubuntuforums.org/showthread.php?p=454217") might help you along, too.
[/I]

---

### Post by bioShark on 2007-07-02
Hi

Yes, I have an Intel processor.
I have tested yesterday with a modeline for the monitor. It was a different program then the one you have posted, but it generated me a modeline. Not good either.

I have noticed on the Nvidia site that GeForce4 is not suported with the standard nvidia driver, instead I should use the nvidia legacy drivers. I will check this when I get home, because right now I am at work.

c.u.

---

### Post by moore.bryan on 2007-07-02
*nvidia's it, then.  the legacy drivers should fix everything and a quick search of the forums should yield a how-to.  good luck!*

---

### Post by bioShark on 2007-07-02
Thanks, and thanks a lot for your time. I will get back with my outcome tonight.

c.u.

---

### Post by bioShark on 2007-07-02
Hi

IT'S WORKING!!!!!!!!!!!!!

Solution:

Manual download to the Nvidia 9639 driver, directly from [www.nvidia.com](www.nvidia.com) . It is the latest one (may 2007). After installing the build-essential :

    $sudo apt-get install build-essential

 from the repository,

   $sudo sh NVIDIA-Linux-x86-1.0-9639-pkg1.run

Then it makes an install of about 2 minutes, and the next time you start the X you have all the resolutions available. 

c.u.

---

### Post by moore.bryan on 2007-07-02
*excellent!*

---

