---
title: "How to fix slow trackpad cursor and/or click tapping"
date: 2006-10-04
forum: Apple PPC Users
---

### Post by Jimerson on 2006-10-04
This was written for complete newbies like myself, so it will explain everything thoroughly.

It took me several hours to compile this information and use trial & error, and in doing so noticed that there were many like me who were confused/upset that their cursor moved very slow or their trackpad would not stop acting as a mouse click when tapped. I'm running a G4 iBook, but I believe this will fix the problem on other machines as well. Please let me know if it does not work for you, because I stumbled across several other solutions (that didn't work for me).

The problem, it seems, is that dapper is missing some settings for the synaptic trackpad, so we have to add them, and also make sure they are set correctly. The file we need to edit has owner permissions, which means when you are logged in as a normal user (when you login to ubuntu with your name) you aren't able to save your changes to it. To get around this, we temporarily gain root access.. and you can do this while still being logged in as a user. Hit alt-f2 and a Run Application window should pop up. In the blank field, type "gksudo nautilus". Type in the root password, for me it is the same password I use to login.Now, another window will pop up, it should be titled "root -File Browser". As a warning, be careful when accessing root owned files, they don't have permissions for a reason- you can completely mess things up if you are not careful! Within this root file browser, open the File System. Then open the "etc" folder. Now scroll down to the X11 folder, and finally in the X11 folder, open the xorg.conf file. Don't change anything in this file except what I say to. In xorg.conf, scroll down until find a portion that says "Section "InputDevice"" and "Synaptics Touchpad". Also, it would be wise to back up the portion you change before you change it. To do this copy the entire section that starts with input device, synaptics touchpad, all the way down to where it says "EndSection", go to the text editor in your applications and paste the code into a blank file. Save it to the desktop or somewhere you will be able to recover it easily. Go back to that section, and replace what you see with this:


Section "InputDevice"
    Identifier        "Synaptics Touchpad"
    Driver            "synaptics"
    Option            "SendCoreEvents"    "true"
    Option            "Device"        "/dev/psaux" 
    Option            "Protocol"        "auto-dev"
    Option        "MinSpeed" "0.60"
    Option        "MaxSpeed" "1.10"
    Option        "AccelFactor" " 0.030"
    Option        "EdgeMotionMinSpeed" "200"
    Option        "EdgeMotionMaxSpeed" "200"
EndSection


Now you have to save this file and reboot. You may need to adjust your mouse settings in System->Preferences, but it should move a lot faster now. If you can't get it right, go back into the xorg.conf file and tweak the speed and accel factors. You will have to reboot each time and it may be a hassle, but at least you didn't have to reboot 20+ times just to figure all this out. ; )


-Jimerson

---

### Post by iAndy on 2006-10-20
Thanks for this guide!  It was perfectly simple and clear and worked without a single tiny hitch...thanks!

I do have some questions about the trackpad after doing this now.

My tracking speeds are must better now, thats great...however the sensitivity seems to have been decreased.  As long as a keep my finger on the trackpad and keep it moving it is fine, if I stop for a brief second the trackpad will stop working and will no longer pick up my finger movin across it.  I have to move my finger away and wait a brief second before it seems to wake up again and pick up my finger movements again.  This is highly strange.  It's almost as if it gets stuck...freezes for a few seconds, before unfreezing and carrying on again.

Before the trackpad didn't do this, it was just very slow, but picked up my finger fine every time.

Anyone know why it is doing this and have any suggestions?!  

Like Jimerson I am a beginner when it comes to stuff like this, and are actually trying to write my own how-tos for all of this in simple easy steps!...so If I can do it the nits usually easy enough for most people to do so I am collating all the information I am given to help me and do this tutorial about Ubuntu on a PowerBook, as well as all the little things you also need to do (i.e.: trackpad...wireless etc etc) which I will post on the forum etc when done.

---

### Post by billybag on 2006-11-20
GREAT GUIDE. it worked great, but i have one problem.

now my cursor is TOOO FAST. i am not sure which OPTIONs to change. Minspeed, Maxspeed, accelfactor.....

anyone know what does what?

---

### Post by Ertaius on 2007-02-08
Hello,

This is a thought, I think you were having the same sensitivity issue before, but you didn't notice how hard you pressed on the trackpad to get it to move?  In any case, try adding these other two (they should work if you find that the trackpad doesn't have this problem if you take your finger off and right away use it again pressing hard)


Option                 "FingerLow"      "7"
Option                 "FingerHigh"      "8"

you may need to change the values, remember that these two are integer values, not float.

FingerLow- When your finger pressure goes below this value, it will count as a release.

FingerHigh- When your finger pressure goes above this value, it will count as a touch.

Best of luck to you.


"Nowadays most people die of a sort of creeping common sense, and discover when it is too late that the only things one never regrets are one's mistakes."
             ~Oscar Wilde

---

### Post by darkmediator on 2007-12-15
Wonderful! I had this problem occurring recently and this solution worked like charm!:guitar:

---

### Post by erfahren on 2007-12-15
took him several hours? Darn, wished he just asked me! - that original post is about a year old though...

(This post has been edited for clarification.)

I also hate that tap-to-click thing. I'd end up clicking on things unintentionally. It's the very first thing I disable on a fresh install. 

Do this a couple times and you guys will have it committed to memory.

Anyway, go to the terminal and first make a backup of your current xorg.conf (always good to have)
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_back

```
then open it in gedit (with root permissions) to edit it (we use "gksudo" for gedit since it's a GUI based app)
```

gksudo gedit /etc/X11/xorg.conf

```
scroll down to that section the OP mentioned (under Section "InputDevice" Identifier "Synaptics Touchpad") 
and enter the line:
```

Option           "MaxTapTime"                "0"

```
save and restart X for changes to take place (ctrl+alt+backspace)

--------------------------------------------------------------------------------------------------------------------------

There are a couple of packages available in the Ubuntu repos that have additional configuration options for Synaptic Touchpads now:
**QSynaptics** 
-and-
**GSynaptics**

 (personally I think I like GSynaptics better)

to install just do:
```

sudo apt-get install gsynaptics

```

(for either package a line needs to be added in that same Synaptics Touchpad section of xorg.conf )
```

Option          "SHMConfig"             "on"

```
... the first time you go to use GSynaptics it'll tell you that.

(note: I've tried both now, but seem to have better luck with GSynaptics)

---

### Post by Gen2ly on 2007-12-16
If I remember correctly there is a man entry for synaptics.  It tells all the options that can be used in xorg.conf.  Or possibly its synclient.

---

### Post by Jimerson on 2007-12-22
> **erfahren said:**
> took him several hours? Darn, wished he just asked me! - that original post is about a year old though...




I recall asking around the IRC chat for awhile, but no one could help me out.. I was a complete newb back then with no idea what I was doing. But I suppose not much has changed since then. ; )

---

### Post by erfahren on 2007-12-23
> **Jimerson said:**
> I recall asking around the IRC chat for awhile, but no one could help me out.. I was a complete newb back then with no idea what I was doing. But I suppose not much has changed since then. ; )
I was kind of joking when I wrote that line, it wasn't meant to be critical and I aplogize if it came off that way. it always sucks seeing someone struggle with an annoyance that you know there's an easy fix for. 

I honestly cannot see how anyone would like that feature. I end up clicking on things inadvertantly. When I first got my notebook I brought Windows to a screeching halt clicking on something I didn't intend to.

So trying to figure out how to disable tap-to-click was one of the first things I had to search for when I was new to Ubuntu as well. At first I thought that maybe it couldn't be done (I was naive), but then figured that there was absolutely no way that I could be the only Linux user in the entire world that couldn't stand that feature, and alas, I wasn't! (I can't stand the vertical scroll feature either, maybe my hands are just too big and clumsy for all of the different peculiarities of these things. - lol)

anyway Jimerson, glad to see you're still around!

---

### Post by anthonylane13 on 2007-12-27
Thanks for this post.  Unfortunately, it has not stopped my trackpad from clicking when tapped.  I would really like to disable this feature.  I am using a powerbook g4 (gigabit ethernet) and I just installed feisty today :-)
Any help would be really appreciated as I am a hopeless noob!

---

### Post by erfahren on 2007-12-27
> **anthonylane13 said:**
> Thanks for this post.  Unfortunately, it has not stopped my trackpad from clicking when tapped.  I would really like to disable this feature.  I am using a powerbook g4 (gigabit ethernet) and I just installed feisty today :-)
Any help would be really appreciated as I am a hopeless noob!
I guess you've already checked your mouse settings (through System > Preferences) to see if you're able to change it there.

did you try doing the second part of my post above (entering the "Option MaxTapTime 0" part) and restart X? 

do this if you don't mind. in the terminal enter:
```

cat /etc/X11/xorg.conf

```
that will show the contents of your /etc/X11/xorg.conf file. Post the output here.

---

### Post by anthonylane13 on 2007-12-27
Thanks for the fast reply

the contents of my xorg.conf file as follows:

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "MinSpeed" "0.60"
Option "MaxSpeed" "1.10"
Option "AccelFactor" " 0.030"
Option "EdgeMotionMinSpeed" "200"
Option "EdgeMotionMaxSpeed" "200"
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
        Identifier      "ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
        Driver          "ati"
        BusID           "PCI:0:16:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Color LCD"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
        Monitor         "Color LCD"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x854"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x854"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x854"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x854"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x854"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x854"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

Thanks

---

### Post by anthonylane13 on 2007-12-27
Done it!!
Really sorry - I did read your post about adding the maxtaptime option, but because you were talking about downloading other programs to edit this function, I thought I would have to do that too and I didn't know how.
Needless to say, it doesn't click when I tap anymore.
:-)
Thanks again.

---

### Post by erfahren on 2007-12-27
> **anthonylane13 said:**
> Done it!!
Really sorry - I did read your post about adding the maxtaptime option, but because you were talking about downloading other programs to edit this function, I thought I would have to do that too and I didn't know how.
Needless to say, it doesn't click when I tap anymore.
:-)
Thanks again.
that's good, glad you got it.

sometimes I don't arrange my posts in a very clear manner! sry!

basically all I was saying is that immediately after doing a fresh install of Ubuntu I go and make the MaxTapTime entry so it takes effect after the first reboot.

Then I go and install gSynaptics (just through Synaptic Package Manager or using "sudo apt-get install gsynaptics") to make any final adjustments. I included that because those programs may not have been in the Ubuntu repositories at the time the original post was written.

I think I'll go back and edit my post to clarify all that.

---

### Post by anthonylane13 on 2007-12-28
This is strange!

It works, but when I use the suspend function, my trackpad starts tap - clicking when I wake up my computer...

the xorg.conf file remains unchanged.

Is there another file which deals with the trackpad?

@sometimes I don't arrange my posts in a very clear manner! sry! (don't know how to quote - sry!)

Don't apologise.  I probably read it in too much of a hurry...

Any thoughts?

---

### Post by erfahren on 2007-12-28
that is strange, I don't think there's any other file for it.

the only thing I can suggest to try is to remove the settings you put into your xorg.conf and try using GSynaptics. I have pretty good luck with it. - just refer to the second part of my first post.

I did look at the [synaptics man page]( http://linux.die.net/man/5/synaptics) and looked into the "SHMConfig" option. I originally thought it was just a setting that those other configuration utilities (like gsynaptics) needed, but it apparently enables the additional touchpad settings to access shared memory to load. You might just try adding that line and see if that does it.

There was also another tip in the comments of [this tutorial](http://ubuntu-tutorials.com/2006/12/10/tweaking-your-synaptics-touchpad-laptops-ubuntu-6061-610/) - (8th one down)
- to retain the double-tap settings at restart they added the line: Option &#8220;TapButton1&#8243; &#8220;0&#8243;

---

