---
title: "[SOLVED] Monitor stuck at low resolution"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by dave00001 on 2008-02-06
I just got a new monitor (Acer 22" W) which is capable of 1680x1050 resolution....  Problem is, when I go to System -> Preferences ->  Screen Resolution, I can only select a max of 1280x1024.  I have an nvidia geforce 6200 OC card, and yes I have the correct driver (nvidia glx-new) which is enabled.  I play some games on here which require 3d on my card, so know it's working...
Does anybody know how I can up my resolution?? It's stuck at 50 Hz and I can't take full advantage of my nice new monitor!

---

### Post by xpod on 2008-02-06
I just bought a new 22" belinea myself so try opening a terminal via Applications>accesories>terminal and typing in(copy/paste)
```
sudo dpkg-reconfigure xserver-xorg
```

Hit enter,enter password....then,make sure you choose the Nvidia driver for the X-Server option then accept the defaults(tab-enter) for the rest till you come to the RES section.Use the arrow keys to scroll to your desired RES then space bar to accept it.
Then carry on with accepting the defaults till the end.
Once done hit CTRL-ALT-Backspace to rebbot your X-Server(display).
Hopefully you`ll have the right RES......hopefully:)

Good luck.

---

### Post by emarkd on 2008-02-06
That is probably what you'll have to do, but make a backup of your /etc/X11/xorg.conf file beforehand.  Just in case...

---

### Post by xpod on 2008-02-06
> That is probably what you'll have to do, but make a backup of your /etc/X11/xorg.conf file beforehand. Just in case...

#-o
Not that i did myself mind you:-\"
I do *if* i ever start messing with my xorg.conf via a text editor though.
Which i never really need to of course.

zzzz time for moi so good luck either way dave00001....and goodnight:)

---

### Post by Rocket2DMn on 2008-02-06
> **emarkd said:**
> That is probably what you'll have to do, but make a backup of your /etc/X11/xorg.conf file beforehand.  Just in case...

The reconfiguration script makes an autobackup in the format xorg.conf.YearMonthDayTime in the /etc/X11 directory.  Just FYI :)

---

### Post by dave00001 on 2008-02-06
Thanks for the quick help! 
Unfortunately, I just tried

sudo dpkg-reconfigure xserver-xorg

and nothing has changed....  Any other suggestions?

---

### Post by Rocket2DMn on 2008-02-06
> **dave00001 said:**
> Thanks for the quick help! 
Unfortunately, I just tried

sudo dpkg-reconfigure xserver-xorg

and nothing has changed....  Any other suggestions?

Did you restart X with CTRL+ALT+BACKSPACE?  Also, what is your video card - are you sure it supports the higher resolution?

---

### Post by dave00001 on 2008-02-06
Yes, I restarted..  but nothing has changed.

I have an NVIDIA GeFORCE 6200 OC, which should support 2048x1536 at 85 Hz

I'm wondering whether this is a problem with my /etc/x11/xorg.conf file?? though I tend not to want to change this, or have to deal with bigger problems if things go wrong ;)

---

### Post by Rocket2DMn on 2008-02-06
Can you post your xorg.conf file here?
```
cat /etc/X11/xorg.conf
```

---

### Post by dave00001 on 2008-02-06
here is the result:  note that I only included what I think is the important stuff - I don't want this post to be too long..


Section "Device"
        Identifier      "nVidia Corporation NV44A [GeForce 6200]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV44A [GeForce 6200]"
        Monitor         "SyncMaster"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1280x1024"     "1024x768"      "800x600"      "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
EndSection
Section "Module"
        Load            "glx"
EndSection




My guess is that it's not recognizing my monitor as an "acer AL2216W", but rather just as a "Syncmaster" - my previous CRT monitor.  Even in the "screens and graphics" section, I can't get seem to find my exact monitor there...

Anyway here it is, let me know what you think.

---

### Post by Rocket2DMn on 2008-02-07
OK, under the modes part it doesn't show 1680x1050 which means you didn't select that as an option when you did the dpkg reconfiguration.
You can do it again, and when you do select the "nvidia" driver like you have, but on the resolutions screen use TAB to move around and SPACEBAR to select your monitor's max resolution and everything less.  They will all appear as options afterward.
So do the reconfiguration as shown in post 2, then restart X with CTRL+ALT+BACKSPACE

---

### Post by dave00001 on 2008-02-07
Wow, thanks Rocket2DMn...   I forgot to select the resolutions with the spaceber  :P

It's working now, 1680 x 1050, at 61 Hz.  Solved.

---

### Post by lolzlolz on 2008-02-07
i had a problem like this but to fix i had to get a new gfx card -.- my card didnt work with x anyways gratz

---

### Post by xpod on 2008-02-12
> Wow, thanks Rocket2DMn... I forgot to select the resolutions with the spaceber :P

It's working now, 1680 x 1050, at 61 Hz. Solved.
__________________

Good Stuff!!!!
Mind and read those 2nd posts properly in future:lolflag:

:-\"O:)

---

### Post by ynnek63 on 2008-04-20
> **xpod said:**
> I just bought a new 22" belinea myself so try opening a terminal via Applications>accesories>terminal and typing in(copy/paste)
```
sudo dpkg-reconfigure xserver-xorg
```

Hit enter,enter password....then,make sure you choose the Nvidia driver for the X-Server option then accept the defaults(tab-enter) for the rest till you come to the RES section.Use the arrow keys to scroll to your desired RES then space bar to accept it.
Then carry on with accepting the defaults till the end.
Once done hit CTRL-ALT-Backspace to rebbot your X-Server(display).
Hopefully you`ll have the right RES......hopefully:)

Good luck.

OK, stupid noob question. How come when I enter the above commands to reconfigure the xserver, it just takes me thru screen after screen of keyboard settings without ever asking me about my video card or monitor? I am trying to install Kubuntu hardy and am having the same issues with my AL2216W monitor. I can only get 640 x 480. My card is an EVGA 8800GTS 320Mb. 

Here is part of my xorg.conf file:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg "
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us   "
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
        Load            "glx"
EndSection

---

### Post by Rocket2DMn on 2008-04-20
> **ynnek63 said:**
> OK, stupid noob question. How come when I enter the above commands to reconfigure the xserver, it just takes me thru screen after screen of keyboard settings without ever asking me about my video card or monitor? I am trying to install Kubuntu hardy and am having the same issues with my AL2216W monitor. I can only get 640 x 480. My card is an EVGA 8800GTS 320Mb. 

Here is part of my xorg.conf file:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg "
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us   "
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
        Load            "glx"
EndSection

Ubuntu Hardy is using a newer version of X which relies more on autodetection, so xorg.conf is getting used less, and as you noticed, reconfiguring does not ask about video/monitor stuff.  It's driving me insane, but this thread is dead, so you should post a new thread for help in the Hardy Development Forum - [http://ubuntuforums.org/forumdisplay.php?f=305](http://ubuntuforums.org/forumdisplay.php?f=305)
Good luck.

---

### Post by ynnek63 on 2008-04-20
> **Rocket2DMn said:**
> Ubuntu Hardy is using a newer version of X which relies more on autodetection, so xorg.conf is getting used less, and as you noticed, reconfiguring does not ask about video/monitor stuff.  It's driving me insane, but this thread is dead, so you should post a new thread for help in the Hardy Development Forum - [http://ubuntuforums.org/forumdisplay.php?f=305](http://ubuntuforums.org/forumdisplay.php?f=305)
Good luck.

Will do and thanks for the quick response!

---

