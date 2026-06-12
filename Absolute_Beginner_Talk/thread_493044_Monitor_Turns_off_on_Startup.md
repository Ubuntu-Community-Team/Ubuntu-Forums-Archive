---
title: "Monitor Turns off on Startup"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by jon.carstens on 2007-07-05
I'm brand new to using linux. Just tried it out the other day and I really enjoy it. So I decided to install it and I've run into my first problem.

Back when I first put in my Ubuntu LiveCD and tried to boot it would not work. I would push the Start/Install button and the monitor would turn off. So I figured out that I just had to change the screen resolution to match my monitor's native resolution of 1280x1024 by pressing F4 before I started. So before I started Ubuntu I had to do that everytime or it wouldn't work.

So now that I have successfully installed a dual boot of WinXP and Ubuntu I have the same problem. I get the dual boot menu at startup and if I select Ubuntu it starts to load but as soon as it tries to switch to the GUI the monitor turns off.

So I honestly believe that the solution is to change the default screen resolution to 1280x1024. So how do I do this without being able to load Ubuntu?

P.S. I'm at work and I don't have the machine with me so lets try to brainstorm a lot of ideas and I'll try them when I get home.

---

### Post by kosmic on 2007-07-05
Ok when you get to GRUB choose to boot with the safe mode kernel with should be the 2nd kernel in your list.


ubuntu wil boot in console mode

then edit your xorg.conf

nano /etc/X11/xorg.confg

and look for this section 

> 
Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation GeForce 7300 LE"
    Monitor        "Assus"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection



Look at the dephault depth and change the resolution in that field.

Example if you r default dept is 24 then ou need to change where it says :

SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection

---

### Post by jon.carstens on 2007-07-05
I'm sorry but I only partially understand what your saying here.

I understand what to do to find that section but I don't understand what to edit.

I see where you talking about 'default depth' but what exactly and I changing here?

---

### Post by jon.carstens on 2007-07-05
So if my depth is 24 then I what do I change in this:

SubSection "Display"
Depth 24
Modes "1680x1050" "1024x768" "800x600" "640x480"
EndSubSection

---

### Post by jon.carstens on 2007-07-05
I think I may have figured it all out and fixed the problem.

---

### Post by kosmic on 2007-07-06
ok, Only now I've seen your reply.

Hope it is all working now :)

---

