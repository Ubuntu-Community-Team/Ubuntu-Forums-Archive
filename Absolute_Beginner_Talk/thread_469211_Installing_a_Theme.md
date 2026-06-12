---
title: "Installing a Theme?"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by LollYouSuckZor on 2007-06-09
Well, [http://gnome-look.org/content/show.php/Murrina++Dark%C2%B2?content=59793&PHPSESSID=af150d43b6b9c8e683a7e80460cadf33](http://gnome-look.org/content/show.php/Murrina++Dark%C2%B2?content=59793&PHPSESSID=af150d43b6b9c8e683a7e80460cadf33)
says..
to install it in the, home/user/.themes.

But I only have, home/**usr**, and in there there is no .themes folder.

Im using KDE. 6.10, on GNOME desktop..
I wanted to install this new theme, because the old ones really making me mad.  

I dont have Beryl, or compiz, because they never work for me.


How do I install it? :), and am i installing the right one?

---

### Post by luckyd on 2007-06-09
Wait a second, KDE 6.10 on a Gnome desktop?

---

### Post by diatribe on 2007-06-09
the correct path is /home/your_login/.themes, replace your_login with your login ;p
edit: liucky I think he means maybe kubuntu 6.10 but with gnome?

---

### Post by Sethalos on 2007-06-09
Remember that anything with a . before the name is a hidden directory. So make sure you either click View - Show Hidden Files, or simply click in your /home directory and press CTRL + H.

Hope that helps

---

### Post by LollYouSuckZor on 2007-06-09
Nope.  The folder is there, but NOTHING it happening... It dosent show up in themes or anything

---

### Post by Sethalos on 2007-06-09
Ok, so System - Preferences - Themes - click on Customize - Install - Browse to Theme.

If that doesn't work, just do what I do, I created a folder called Themes in my /home and do the above but install from there.

Hope that helps.

---

### Post by LollYouSuckZor on 2007-06-09
> **Sethalos said:**
> Ok, so System - Preferences - Themes - click on Customize - Install - Browse to Theme.

If that doesn't work, just do what I do, I created a folder called Themes in my /home and do the above but install from there.

Hope that helps.

=[ There is no customize..

---

### Post by diatribe on 2007-06-09
you could also install them using sudo to /usr/share/themes.  but installing them to ~/.themes works, I suspect you are doing something wrong

---

### Post by LollYouSuckZor on 2007-06-09
Hate to ask, But would somebody do a remote desktop and find the problem... Lol.  I about to throw my desktop out of my window. :D!!!1

---

### Post by diatribe on 2007-06-09
also you are uncompressing the .gz file and not just trying to copy that to your themes directory right?

---

### Post by diatribe on 2007-06-09
Look ok are you running gnome or kde to begin with?

---

### Post by LollYouSuckZor on 2007-06-09
> **diatribe said:**
> Look ok are you running gnome or kde to begin with?

GNOME

---

### Post by diatribe on 2007-06-09
ok go into a terminal and type 
ls ~/.themes
and paste the output

---

### Post by LollYouSuckZor on 2007-06-09
> **diatribe said:**
> ok go into a terminal and type 
ls ~/.themes
and paste the output

nic@nic-desktop:~$ ls ~/.themes
[COLOR="Navy"]gtk-2.0[/COLOR]  gtkrc  gtkrc~ [COLOR="Navy"] Murrina Dark² Gummy[/COLOR]
nic@nic-desktop:~$

---

### Post by diatribe on 2007-06-09
ok type
cd ~/.themes/Murr*  and then
ls
and paste output

---

### Post by LollYouSuckZor on 2007-06-09
> **diatribe said:**
> ok type
cd ~/.themes/Murr*  and then
ls
and paste output

```

nic@nic-desktop:~/.themes/Murrina Dark² Gummy$ is
bash: is: command not found
nic@nic-desktop:~/.themes/Murrina Dark² Gummy$

```

---

### Post by diatribe on 2007-06-09
ls not is

---

### Post by LollYouSuckZor on 2007-06-09
> **diatribe said:**
> ls not is


```

nic@nic-desktop:~/.themes/Murrina Dark² Gummy$ ls
gtk-2.0
nic@nic-desktop:~/.themes/Murrina Dark² Gummy$

```

Yeah.  Lol im a idiot, is.. phfs. :)
:o it like, finally somebody who knows that their doing!

---

### Post by diatribe on 2007-06-09
ok seeing as it wants to be ignorant, type 
cd ~/.themes
sudo cp -r Murr* /usr/share/themes
then hit ctrl-alt-bksp to restart the x server
log back in go to theme manager and it should show up then

---

### Post by LollYouSuckZor on 2007-06-09
Nope.

Not showing up.

---

### Post by LollYouSuckZor on 2007-06-09
Ugh.  This never works..

---

### Post by diatribe on 2007-06-09
ok, one more thing to try.  whereever you downloaded the .tar.gz file, open nautilus and the theme manager, and drag the .tar.gz file onto the theme manager and it should show up. if that doesnt work post a screencap of your theme manager because you should ahve a customize button on it

---

### Post by diatribe on 2007-06-09
Second thought if you are clicking theme manager and just scrolling down it prolly wont show, you will have to click customise then I think window controls and select it from there; click theme details and it will be in one of the categories there

---

### Post by LollYouSuckZor on 2007-06-09
Yay! Its right.  It worked.

Thanks alot :D
One more thing, how would I install the kind of MacOSX thing.  Ive always wanted it.. But I never understood how to install it. Would I need Beryl, or something to install it..

---

### Post by diatribe on 2007-06-09
what macosx thing are you talking about?  the panel at the bottom or what?

---

### Post by LollYouSuckZor on 2007-06-09
Oh, The bottom. 

I hate the task bar at the bottom right now.  It's a block -.-.

I wanted the mac osx style.. Im not sure what its called.  But yeah, the panel at the bottom.

---

### Post by diatribe on 2007-06-09
well, there is avant window navigator and kiba dock; avant worked better for me, but for either to work you need a compositor, ie beryl/compiz or xcompmgr.  you could also switch to xfce, as it has built-in compositing. but in short if you want a nice dock/panel at the bottom you will need a compositor.  in gnome you should just be able to click enable desktop effects and then they should work also

---

### Post by LollYouSuckZor on 2007-06-09
I wanted something like this, 

[http://www.youtube.com/watch?v=rvYSZ6zPoac](http://www.youtube.com/watch?v=rvYSZ6zPoac)

which is xcompmgr.

How would I install that?

I have beryl right now, but when I try to open the manager, my screen freezes and I have to restart the x server.

---

### Post by diatribe on 2007-06-09
you can get xcompmgr by typing sudo apt-get install xcompmgr in a terminal, it is really resource heavy though.  what kind of video card do you have?

---

### Post by LollYouSuckZor on 2007-06-09
5200 Nvidia Geforce Generic

---

### Post by diatribe on 2007-06-09
ok then you should be cool for compositing, you can get either xcompmgr the way I said or you could look for some howtos on beryl; I dont know why it would crash like that and dont know anything about it in the first place.  but yea avant window navigator or kiba dock would be the way you want to go prolly

also what happens if you try to enable desktop effects?  does that log you out also?

---

### Post by LollYouSuckZor on 2007-06-09
Im not sure.  I havent got that far. :P

Here.

Add me on aim?


NicZawr

---

### Post by LollYouSuckZor on 2007-06-09
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:55:20 PST 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
	Option		"RenderAccel"		"true"
	Option		"AllowGLXWithComposite" "true"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "TripleBuffer" "True"
    Option         "AddARGBGLXVisuals" "True"
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
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

### Post by diatribe on 2007-06-09
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

#AUTOMATIX REPOS START

#deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
## E17 repository &#8220;edevelop.org&#8221;
#deb [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) feisty e17
#deb-src [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) feisty e17


#deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main

---

