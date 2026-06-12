---
title: "[SOLVED] 1280x768 resolution?"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-10-28
Hi, bit of a newb here, I'm using mint linux ubuntu based OS and it did not detect my 1280x768 wide screen resolution on install. 

I have 915resolution installed so if someone could guide me through a step by step process on doing this?

I have an Intel chip set. I'm confused by this picture:
[IMG]http://i71.photobucket.com/albums/i123/broinjc/Screenshot-3.png[/IMG]

thanks for your help, sorry i'm lazy to read up on it myself. 

staticvoid

**EDIT: just to move the answer up here:**
next post down, follow julian67's instructions, and then if you have a flickering problem, don't forget:
> When at the 1280x768@30 resolution that flickers and looks horrible which is what comes up as the default, all that you need to do is hit the Fn-F5 key and it switches to the 60Hz refresh rate. I tried to do many other things on the Ubuntu side, ie changing to the 60Hz in the Screen manager, but it messes up the system pushing a 640x480 resolution that you have to go into recover mode and then the /etc/X11 to reset the xorg.conf to a previously good state.

keep reading, hope you can get your problems fixed! I did!!  :D

---

### Post by julian67 on 2007-10-28
You might be able to fix it by editing (as root) the file /etc/X11/xorg.conf 

First back up your current xorg.conf

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Now to edit the file. You can use your usual text editor such as gedit, leafpad, kate, mousepad etc. 

The relevant part of it will look something like this

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV44A [GeForce 6200]"
    Monitor        "DELL 1504FP"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```

You can change each of the Modes lines to read ```
Modes      "1280x768" "1024x768" "800x600" "720x400" "640x480"
``` or similar, basing it on *your* xorg.conf *not* mine.  Save the file. 

You will need to restart X so close all running applications and ```
<Ctrl><Alt><Backspace>
``` and log back in. If this doesn't work I'd suspect the wrong driver is being used i.e you are using vesa driver instead of i810. If this doesn't work then post your xorg.conf

I've owned 3 laptops that use Intel 855 or 915 graphics and in older versions of Ubuntu and other distros needed 915resolution to be installed and configured but since Edgy it has worked out of the box for me. I'm surprised Mint didn't do this.

---

### Post by lgwwin on 2007-10-30
My Fujitsu P5010 laptop has similar problem.
Graphic chip is Intel 82852/82888 GM/GME

I run ubuntu 7.10, and the system has the 1280x768 resolution, but the refresh rate doesn't work correctly. The screen flashes seriously.

I have search and try to solve the problem for 2 days. But all the methods don't work.

Hope anyone can help.

---

### Post by staticvoid on 2007-11-03
Hey thanks guys. Igwwin: in Ubuntu 7.10 there is a new graphical interface to set up your LCD screen correctly. If you find the model number of your screen you can set it up to work. Or search the internet for what you refresh reates and stuff are and you can use the graphical xorg editor to put in the correct values.

It looks like you have been having this problem with previous versions of ubuntu. Sorry bout that : /

check out chacha.com and search with a guide. Its cool.

oh and your laptop has a natural problem with its screen rez it looks like. cnet said
"The bad: *Overly dense screen resolution*; crowded keyboard; short warranty."

ok, bye, hope you get it figured out. I'll edit my xorg.conf mode lines. right now I use the 915resolution hack and have to resart X every time because I have the 915resolution line of code running in a file it reads before resarting. wierd.

sv

---

### Post by julian67 on 2007-11-03
> **staticvoid said:**
> 

oh and your laptop has a natural problem with its screen rez it looks like. cnet said
"The bad: *Overly dense screen resolution*; crowded keyboard; short warranty."

[I]
Overly dense screen resolution????[/I] Genuine meaningless bee ess from cnet.  Did someone masquerading as a journalist actually get paid to write that nonsense? I had a P7010D, same adapter, screen and resolution and it was great, but of course in Windows you don't have such fine control over the size of icons, taskbar, fonts etc and the XP desktop either looks too small at normal sizes or cartoonish at large size.  Using openSUSE it looked great.

---

### Post by rickdog on 2007-11-03
Have you tried the venerable old:

sudo dpkg-reconfigure -phigh xserver-xorg

method and just pick the resolutions you want?

---

### Post by staticvoid on 2007-11-04
yeah, you can never trust cnet :P

reconfigureing would work best. ubuntu 7.10 recognized my 1280x760 rex automatically. linux mint still does not.

---

### Post by kevink on 2008-01-10
The underlying problem was not resolved in this thread, but since this thread is what Google is finding for this issue, I thought I would post the solution that Igwwin found. When at the 1280x768@30 resolution that flickers and looks horrible which is what comes up as the default, all that you need to do is hit the Fn-F5 key and it switches to the 60Hz refresh rate.  I tried to do many other things on the Ubuntu side, ie changing to the 60Hz in the Screen manager, but it messes up the system pushing a 640x480 resolution that you have to go into recover mode and then the /etc/X11 to reset the xorg.conf to a previously good state.

---

### Post by staticvoid on 2008-01-11
thanks, I'll put it up top and mark this as solved.

---

