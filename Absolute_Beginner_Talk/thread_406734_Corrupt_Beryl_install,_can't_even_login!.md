---
title: "Corrupt Beryl install, can't even login!"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by ChrisUK on 2007-04-11
Hi all.

I installed Ubuntu 6.10 yesterday for the first time. I have never used Linux before so I am quite new to all of this.
I followed the Ubuntu guide on Wiki on how to install software, etc. I got to Beryl and followed the guide shown here: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29)

I got to this part:
>     * Add this to xorg.conf "Screen" section 

# Enable 32-bit ARGB GLX Visuals
    Option "AddARGBGLXVisuals" "True"

# If you are using an older version of compiz that
# does not support rendering into the Composite
# Overlay Window, you will need to disable clipping
# of GLX rendering to the X Root window with this
# option, or you will get a blank screen after
# starting compiz:
    Option "DisableGLXRootClipping" "True"

    * Add this to xorg.conf "Device" section 

Option          "TripleBuffer" "true"

    * Restart X with ctrl+alt+backspace 

As soon as I hit ctrl+alt+backspace my screen went black, then it came up with a horrible looking blue screen with weird text saying "Failed to start the X server (your graphical interface) it is likely that it is not setup properly. Would you like to view the X server output to diagnose the problem?"
I went on "No" and it said "The X server is now disabled. Restart GDM when it is configured properly".
I restarted my PC and now the login screen is black and it only asks for the password. So I put my pass in and it says "Incorrect password", I have tried it about 10 times and I am sure the pass is correct.
I did backup the xorg.conf as asked in the guide, but it is useless because I can't even login!

Please help, I am tempted to just reinstall Ubuntu now... :(

---

### Post by freebird54 on 2007-04-11
Well you can try <ctrl><alt><F1> and login in that way. Then:

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

assuming that xprg.conf.backup was the name yolu chose for your xorg.conf backup :)

A long way from needing a re-install!

---

### Post by ChrisUK on 2007-04-11
> **freebird54 said:**
> Well you can try <ctrl><alt><F1> and login in that way. Then:

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

assuming that xprg.conf.backup was the name yolu chose for your xorg.conf backup :)

A long way from needing a re-install!

I did try ctrl_alt_F1 which took me to the login screen, but it keeps saying the pass is incorrect. :confused:

---

### Post by freebird54 on 2007-04-11
I hate to ask - any chance that CAPS LOCK status has changed?  (been there - done that!)

---

### Post by ChrisUK on 2007-04-11
You are right, it was caps lock. It was using & instead of 7. :) 

I logged in and typed the command you gave, it said; "cp: cannot stat '/etc/X11/xorg.conf.backup'.
I used the same command to backup as shown in the guide, I just copied and pasted.

Any idea's? :(

---

### Post by freebird54 on 2007-04-11
Ought to have worked if that is the name of the backup file.  Have you checked with

```
ls -l /etc/X11/x*
```

to see what's there?  Sudo was on the front of the command?  X11 was capitalized :) ?

hard to see what you're doing from here...

---

### Post by ChrisUK on 2007-04-11
Ooooh yeah!

It looks like I didn't use a capital X and I was using xll instead of X11.

All seems to be working OK now, and surprisingly even Beryl seems to be working... 

Thanks very, very much for the help... :KS

---

### Post by freebird54 on 2007-04-11
These things are fussy - but rewarding when you get it!  I await the successful implementation of the DWIM command on ANY Operating system -and I WILL buy it when it happens....

DWIM - **D**o **W**hat **I** **M**ean !!

---

### Post by ChrisUK on 2007-04-11
Sorry to be a pest, but I don't think Beryl is working as it should.

I can see Beryl is installed in "Applications > system tools", and I can see the Icon in the top right corner, but nothing has changed - my icons, desktop, etc. is all still the same and the Beryl commands are not working.
I tried to install it again following the Ubuntu guide link in my first post, but the problem always happen when I edit the xorg.conf file and press ctrl + alt + F1.
Is there another/easier way to install Beryl?

---

### Post by freebird54 on 2007-04-11
What change are you making to your xorg.conf?  And - if the 'jewel' is there - Beryl has loaded.  There are a number of options available by right-clicking the jewel, including how it should render, what base it should use etc - that can be modified and tried.  It is pretty good at exiting back to 'Metacity' (normal window manager) when something is wrong...

Hope this helps

---

### Post by ChrisUK on 2007-04-11
Hi.

In the guide I followed on UbuntuGuide in Wiki, it said:

> Add this to xorg.conf "Screen" section

# Enable 32-bit ARGB GLX Visuals
Option "AddARGBGLXVisuals" "True"

# If you are using an older version of compiz that
# does not support rendering into the Composite
# Overlay Window, you will need to disable clipping
# of GLX rendering to the X Root window with this
# option, or you will get a blank screen after
# starting compiz:
Option "DisableGLXRootClipping" "True"

* Add this to xorg.conf "Device" section

Option "TripleBuffer" "true"

* Restart X with ctrl+alt+backspace

That's where I keep getting the xorg problems, maybe I put the text in the wrong place, I don't really know.

I have right clicked on the red gem and went to "Select window manager" and it seems it is stuck on "Metacity", when I try to change it to "Beryl" it causes my windows to flicker a few times, then nothing happeneds and it is back to the default "Metacity".

---

### Post by freebird54 on 2007-04-11
Have you tried them individually as yet?

As for location, I would suspect you got that right.  If you post the sections you put them in, we can be sure :)  If it were MY xorg.conf, those would look like this:

```
Section "Device"
        Identifier  "ATI Radeon 9550"
        Driver      "fglrx"
        Option      "UseFBDev" "true"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        **Option      "TripleBuffer" "true"**
        BusID       "PCI:1:0:0"
EndSection
```

```
Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Radeon 9550"
        Monitor    "Samsung_900iFT"
        **Option     "AddARGBGLXVisuals" "True"**
        **Option     "DisableGLXRootClipping" "True"**
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

```

in case that gives any more clues.  I would definitely try them separately though, not sure you need them all!

---

### Post by ChrisUK on 2007-04-12
I just tried it with device and the X server failed again after pressing ctrl + at + backspace.

My "Device" looks very different from yours... I don't know if it's because I'm using an NVidia card or not, but here's what it looks like as default:

> Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

My screen looks like this:

> Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1200"
	EndSubSection
EndSection

Thanks for the help so far, I just can't wait to get this working! :(

---

### Post by freebird54 on 2007-04-12
Not too sure about what workarounds/mods are needed with that driver, sorry!  Had enough fun getting ATI to work!

The place where I picked those settings up did not specify as to which card - but they may well have been for ATI because ATI wants to run XGL to get Beryl going, but I have seen that AIGLX is preferred for NVidia.  Over to the next 'expert'??

AS this has become mainly about Beryl - you may want to try this question on another forum - specifically the **Desktop Effects & Customization** forum here in Ubuntuland.  You will get quicker, and hopefully more focused answers there on Beryl issues. We have you begun on this, it's as far as we can sure what we're doing for you!

---

### Post by ChrisUK on 2007-04-12
It's OK, I will ask on the section you recommended, this thread is getting a bit messy now and I guess people wouldn't want to read the whole thing. 
Thank you very much for all your help, at least I now have an idea of what is causing the problem.

Thanks.

My new thread: [http://ubuntuforums.org/showthread.php?p=2440319#post2440319](http://ubuntuforums.org/showthread.php?p=2440319#post2440319)

---

