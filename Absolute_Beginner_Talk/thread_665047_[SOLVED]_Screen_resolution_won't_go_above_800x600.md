---
title: "[SOLVED] Screen resolution won't go above 800x600"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by ladybumavere on 2008-01-11
First off I'd just like to say that I've been using Ubuntu and Linux in general for less than a week, so this might be some simple fix, yet I don't know really what I'm doing. So far I've tried several fixes found in the forums for this as well as on google and nothing is working.

Here's my problem:

I'm running an old Voodoo3 3000 card in my PC with an old CTX VL700 CRT monitor and I cannot get the screen resolution to go past 800x600.  I do have the option to run 640x480 which I choose not to use.  I've tried running the dpkg-reconfigure xserver-xorg command several different times and different ways.  Including the advanced portion and actually putting in the Hsync & Vsync rates to no avail.  Every time I reboot it just shows me a black screen with white text that flashes 3 times then I get a message that it cannot run on the settings I've put in and asks me to run in low graphics mode or to configure.  When I choose to configure I can select my monitor and video card drivers from the configure screen but it will not allow me to test it or click ok no matter what I do; I can only cancel and go back to 800x600.  

It's just really upsetting because so far I'm enjoying Ubuntu much much more than Windows yet this is a huge deterrent.

I'd really love some help,
Thanks a lot.

---

### Post by billgoldberg on 2008-01-11
Sorry buddy, the only advice I can give you is to try the "restriced drivers manager' and reboot or change xorg.conf and add the wanted resolution there next to 800x600

---

### Post by ladybumavere on 2008-01-11
I just attempted the "Restricted Drivers Manager" and this is what it tells me.


"Your hardware does not need any restricted drivers."

---

### Post by Shazaam on 2008-01-11
Check these out....
[http://ubuntuforums.org/showthread.php?t=18106&highlight=Voodoo3+3000](http://ubuntuforums.org/showthread.php?t=18106&highlight=Voodoo3+3000)
[http://ubuntuforums.org/showthread.php?t=212175&highlight=Voodoo3+3000&page=2](http://ubuntuforums.org/showthread.php?t=212175&highlight=Voodoo3+3000&page=2)

There are others that are pretty old.

---

### Post by ladybumavere on 2008-01-11
> **Shazaam said:**
> Check these out....
[http://ubuntuforums.org/showthread.php?t=18106&highlight=Voodoo3+3000](http://ubuntuforums.org/showthread.php?t=18106&highlight=Voodoo3+3000)
[http://ubuntuforums.org/showthread.php?t=212175&highlight=Voodoo3+3000&page=2](http://ubuntuforums.org/showthread.php?t=212175&highlight=Voodoo3+3000&page=2)

There are others that are pretty old.



From everything I've been reading,.. I think I just need to buy a new video card.


Thank you for your help.

---

### Post by ladybumavere on 2008-01-11
Here's my xorg.conf if this could help someone find the specific problem.





Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "3Dfx Interactive, Inc. Voodoo 3"
        Driver          "voodoo"
        BusID           "PCI:0:8:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "CTX VL700"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "3Dfx Interactive, Inc. Voodoo 3"
        Monitor         "CTX VL700"
        DefaultDepth    16
        SubSection "Display"
                Modes           "1280x1024" "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

---

### Post by Hospadar on 2008-01-11
could you post a copy of your /etc/X11/xorg.conf file?  we might be better able to advise you if we can see how it's currently setup.

When you did dpkg-reconfigure xserver-xorg what did you select?  there's one page in the dialog where you select resolutions with the spacebar and press enter to continue, the first time I was setting up a system I thought enter selected and couldn't figure things out for the longest time. so you may want to have a look at that.

I don't think the voodoo cards do any opengl support, so no restricted drivers should be needed. (since the voodoo cards came back in the day when you had to pick between opengl and directx)

I suppose it's *possible* that higher resolutions arn't supported, but that seems unlikely

---

### Post by ladybumavere on 2008-01-11
> **Hospadar said:**
> could you post a copy of your /etc/X11/xorg.conf file?  we might be better able to advise you if we can see how it's currently setup.

When you did dpkg-reconfigure xserver-xorg what did you select?  there's one page in the dialog where you select resolutions with the spacebar and press enter to continue, the first time I was setting up a system I thought enter selected and couldn't figure things out for the longest time. so you may want to have a look at that.

I don't think the voodoo cards do any opengl support, so no restricted drivers should be needed. (since the voodoo cards came back in the day when you had to pick between opengl and directx)

I suppose it's *possible* that higher resolutions arn't supported, but that seems unlikely



The first few times I selected 1280x1024, 1024x768, 800x600, and 640x480.  On this last attempt I tried taking out the lower resolutions completely but still has done nothing.

---

### Post by coolbrook on 2008-01-12
I resolved this same problem earlier today.

One thing you might want to check is that PCI Bus ID.  I configured it to point to the wrong location so there was a conflict between my onboard video and my PCI card.

Do you have more xorg.conf files in your x11 directory?  If so then take a close look at their contents and see if the BusID is different in them.  Then try entering it during the dpkg reconfigure.

---

### Post by ladybumavere on 2008-01-12
> **coolbrook said:**
> I resolved this same problem earlier today.

One thing you might want to check is that PCI Bus ID.  I configured it to point to the wrong location so there was a conflict between my onboard video and my PCI card.

Do you have more xorg.conf files in your x11 directory?  If so then take a close look at their contents and see if the BusID is different in them.  Then try entering it during the dpkg reconfigure.



Yes, there are actually all these xorg.conf's in there...

xorg.conf                 xorg.conf.27              xorg.conf.70
xorg.conf.1               xorg.conf.28              xorg.conf.71
xorg.conf.10              xorg.conf.29              xorg.conf.72
xorg.conf.100             xorg.conf.3               xorg.conf.73
xorg.conf.101             xorg.conf.30              xorg.conf.74
xorg.conf.102             xorg.conf.31              xorg.conf.75
xorg.conf.103             xorg.conf.32              xorg.conf.76
xorg.conf.104             xorg.conf.33              xorg.conf.77
xorg.conf.105             xorg.conf.34              xorg.conf.78
xorg.conf.106             xorg.conf.35              xorg.conf.79
xorg.conf.107             xorg.conf.36              xorg.conf.8
xorg.conf.108             xorg.conf.37              xorg.conf.80
xorg.conf.109             xorg.conf.38              xorg.conf.81
xorg.conf.11              xorg.conf.39              xorg.conf.82
xorg.conf.110             xorg.conf.4               xorg.conf.83
xorg.conf.111             xorg.conf.40              xorg.conf.84
xorg.conf.112             xorg.conf.41              xorg.conf.85
xorg.conf.113             xorg.conf.42              xorg.conf.86
xorg.conf.114             xorg.conf.43              xorg.conf.87
xorg.conf.115             xorg.conf.44              xorg.conf.88
xorg.conf.116             xorg.conf.45              xorg.conf.89
xorg.conf.117             xorg.conf.46              xorg.conf.9
xorg.conf.118             xorg.conf.47              xorg.conf.90
xorg.conf.119             xorg.conf.48              xorg.conf.91
xorg.conf.12              xorg.conf.49              xorg.conf.92
xorg.conf.120             xorg.conf.5               xorg.conf.93
xorg.conf.121             xorg.conf.50              xorg.conf.94
xorg.conf.122             xorg.conf.51              xorg.conf.95
xorg.conf.13              xorg.conf.52              xorg.conf.96
xorg.conf.14              xorg.conf.53              xorg.conf.97
xorg.conf.15              xorg.conf.54              xorg.conf.98
xorg.conf.16              xorg.conf.55              xorg.conf.99
xorg.conf.17              xorg.conf.56              xorg.conf.failsafe
xorg.conf.18              xorg.conf.57              xorg.conf.failsafe.bak
xorg.conf.19              xorg.conf.58              
xorg.conf.2               xorg.conf.59              
xorg.conf.20              xorg.conf.6              
xorg.conf.20080111152512  xorg.conf.60
xorg.conf.20080111173537  xorg.conf.61         
xorg.conf.20080111192747  xorg.conf.62 



Why are there so many, and what do they all do?

---

### Post by eapache on 2008-01-12
I think your monitor refresh rates are bad. If it was a graphics card problem you wouldn't be getting any picture at all. Try changing to these under your monitor section:

HorizSync    30.0 - 65.0
VertRefresh  50.0 - 120.0

Write down what is there now so you can switch back if they don't work.

---

### Post by ladybumavere on 2008-01-12
> **eapache said:**
> I think your monitor refresh rates are bad. If it was a graphics card problem you wouldn't be getting any picture at all. Try changing to these under your monitor section:

HorizSync    30.0 - 65.0
VertRefresh  50.0 - 120.0

Write down what is there now so you can switch back if they don't work.



Nope, unfortunately that did not work.  Although I looked up the Hsync and Vsync rates and the ones I had entered before were specific to my monitor.

Also, here's the message I get when I first boot up Ubunutu:

"Ubuntu is running in low-graphics mode.
Your screen and graphics card could not be detected correctly.  To use higher resolutions, visual effects or multiple screens, you have to configure the display yourself."

And when I try to configure it, I can only select "Cancel."
It will not allow me to select "Test" or "OK."

---

### Post by ladybumavere on 2008-01-12
Ok, well I've fixed the problem by creating a new one.  I had my old monitor still in the basement (Envision 710e) which is a pile of garbage, hence the reason for using the CTX.  I decided to just see what would happen if I swapped them out.  I swapped them, rebooted, reconfigured the xorg.conf, rebooted and voilà... 1280x1024.

But the reason I stopped using this old monitor is because it has a problem distinguishing between a very dark color and black and the screen becomes blurry when used at 1280x1024.  Which neither of these are a HUGE problem per se, but I do a lot of digital graphic design on my PC and I need to be able to see what these images are going to look like, not blurry or all black.


Basically, is my only hope to buy a new monitor?


Suggestions?

---

### Post by nikoPSK on 2008-01-12
after reading through all this you might as well just reconfigure xorg.
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

Regards,
nikoPSK

---

### Post by coolbrook on 2008-01-13
> **ladybumavere said:**
> Yes, there are actually all these xorg.conf's in there...


Why are there so many, and what do they all do?

I could be wrong but, as far as I know, they're your attempts to configure. The only one in use is the xorg.conf.

---

### Post by ladybumavere on 2008-01-17
problem resolved with the purchase of a new video card.

and i realize that yes i probably configured the xorg.conf wrong.

oh well. problem fixed.

---

### Post by nikoPSK on 2008-01-17
goody, please mark this thread as "SOLVED". :)

---

### Post by ladybumavere on 2008-01-18
> **nikoPSK said:**
> goody, please mark this thread as "SOLVED". :)



I honestly don't know how to do that.

:oops: :oops: :oops: :oops: :oops: :oops:

---

### Post by lswest on 2008-01-18
at the top of the thread there is a drop-down menu called "thread tools" and under which is an option that says "mark thread as solved"

---

### Post by nikoPSK on 2008-01-18
> **ladybumavere said:**
> I honestly don't know how to do that.

:oops: :oops: :oops: :oops: :oops: :oops:

Like this:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

nikoPSK

---

