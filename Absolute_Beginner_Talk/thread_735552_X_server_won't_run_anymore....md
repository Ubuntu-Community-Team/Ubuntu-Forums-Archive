---
title: "X server won't run anymore..."
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by henaege on 2008-03-25
When I boot up my machine X doesn't start.  So I log in with my username and password and try running startx.  It tries to do stuff and then prints this message:

waiting for X server to shut down FreeFontPath: FPE "/usr/share/fonts/X11/misc"
refcount is 2, should be 1; fixing;

and then right back to the prompt.  I don't even know what any of that means... I'm running 7.10, which has been working great for about 3 months now, and all of a sudden, this.  Any help or suggestions would be greatly appreciated!

---

### Post by jan quark on 2008-03-25
added some new fonts the last days?

weird thing 
did you changed something, installed, or done some updates related with graphics or fonts?

---

### Post by henaege on 2008-03-25
All I've done is use the update manager to install what it recommended... it was a few days ago and my computer booted fine since then.. there could have been fonts involved but I don't remember, but I do know that I haven't installed any manually...  do you know where I could maybe change that setting it's talking about?

---

### Post by dstew on 2008-03-25
The safest way to reconfigure your xserver is to use the command```
sudo dpkg-reconfigure xserver-xorg
```This command takes you through a text-based reconfiguration that (hopefully) will get your X straightened out. Avoid the temptation to directly edit xorg.conf.

---

### Post by jan quark on 2008-03-25
sry for being late with the answers working on many fronts as it were

try to boot into recovery mode and reconfigure the xserver with 
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

edit 
posted simultaneously with dstew i guess

---

### Post by henaege on 2008-03-25
I tried the reconfiguration several times choosing different options and it still doesn't work... thanks for the suggestion, though.  Any other ideas?

---

### Post by steveneddy on 2008-03-25
> **henaege said:**
> I tried the reconfiguration several times choosing different options and it still doesn't work... thanks for the suggestion, though.  Any other ideas?

Choose "vesa" as the driver and the rest defaults.

Restart and see if you get X.

What video card are you running?

---

### Post by henaege on 2008-03-25
I'm running an nvidia GeForce fx 5500... the vesa thing didn't work and now it's saying

(EE) Failed to initialize GLX extension (Compatible NVIDIA Z driver not found)

as well as the other stuff from before...

---

### Post by smurphy_it on 2008-03-25
Try gksudo nvidia-xconfig

---

### Post by henaege on 2008-03-25
No dice...

gksudo:  error while loading shared libraries:  libpng12.so.0:  cannot open shared object file:  No such file or directory

That can't be good, unless it tells you something interesting that I have no clue about (which is more than likely so)

---

### Post by smurphy_it on 2008-03-25
what about the normal sudo nvidia-xconfig

---

### Post by henaege on 2008-03-26
That took away the message about the video card, but still no X.  When I ran sudo nvidia-xconfig it said:

Using X configuration file:  "etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as 'etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

I guess that's normal though...

---

### Post by smurphy_it on 2008-03-26
Post a reply with the contents of your /etc/X11/xorg.conf file so I / everyone can take a look at it to see if we can help any.

---

### Post by henaege on 2008-03-26
Here's what it says on bootup:

kinit: name_to_dev_t(/dev/disk/by-uuid/5fc95a36-df0c-4601-819e-0da4b616155c) = hda5(3,5)
kinit:  trying to resume from //dev/disk/by-uuid/5fc95a36-df0c-4601-819e-0da4b616155c
kinit:  no resume image, doing normal boot...

I guess I could have posted that earlier...

---

### Post by smurphy_it on 2008-03-26
You should post the contents of your xorg.conf file here (/etc/X11/xorg.conf) and your error log...

In a terminal type dmesg > dmesg.log and paste the contents of that log here.

---

### Post by henaege on 2008-03-26
etc/X11/xorg.conf:

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "VX720"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV34 [GeForce FX 5500]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV34 [GeForce FX 5500]"
    Monitor        "VX720"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by smurphy_it on 2008-03-26
Under the section labelled Section "Device" you will find a line which reads:

driver "nvidia"

and change it to 

driver "nv"

then try startx, or sudo gdm restart

---

### Post by henaege on 2008-03-26
Ok, I'm pretty sure my problem runs a bit deeper... *Breaking News!!*

/dev/hda1 has been mounted 39 times without being checked, check forced.
/dev/hda1:
Inode 9554485 has illegal block(s).

/dev/hda1:  UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.  (i.i., without -a or -p options)
fsck died with exit status 4

So it's running fsck now...  

Inode 9554485 has illegal block(s).  Clear<y>?

Should I press y or not?

---

### Post by smurphy_it on 2008-03-26
Try downloading envy.  As you are in text mode now, I'll try to walk you through some of it.

In your home folder, in the terminal type:

wget [http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu7_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu7_all.deb)

That will download the Envy debian package.

Now type:

sudo dpkg -i envy*.deb

You need the "universe" and Multiverse" repos's enabled now.... If you've been using ubuntu for awhile they probably already are... if not you'll have to edit your /etc/apt/sources.lst

Make sure that all the dependencies were installed by typing:

sudo apt-get install -f 

Now in a terminal type:

sudo envy -t

Hopefully once you get through that wizard you'll be fixed up.

Thanks to the FAQ = [http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu]("http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu")

---

### Post by smurphy_it on 2008-03-26
Yeah sounds like you have a few problems there.

I can't answer the fsck question, never came across it.

Good luck.

---

### Post by henaege on 2008-03-26
So I pressed Y and insanity ensued.  Oh well, if I ever get up and running again I'll be sure to install envy.  I really appreciate the help man, you are awesome.

---

