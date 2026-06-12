---
title: "My grafic card fails I tried to install Xliv"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by stevand on 2006-12-23
I did as begginer something that I do not know exactly but I was impressed with the Xgl/Compiz ... then I went to [http://www.ubuntu.com/](http://www.ubuntu.com/) and just wanted to change some wall paper and then I saw A Very Special and Early Gift - Xgl and compiz 
and followed strictly
[http://www.ubuntuforums.org/showthread.php?t=131267](http://www.ubuntuforums.org/showthread.php?t=131267)

My guide is REALLY outdated. Instead use this site:

[http://knowledge76.com/index.php/XGL...z_Nvidia_32bit](http://knowledge76.com/index.php/XGL...z_Nvidia_32bit)

HOWEVER I was full not paying attention to 
Proceed at you own risk. This is new experimental stuff and I hope you are a little command line savy (or can call someone that is) because if something messes up you might be stuck on the command line.

Don't say I didn't warn you.

And I followed [http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit)

site and then it happened that I changed 

/etc/X11/xorg.conf

by running sudo dpkg-reconfigure -phigh xserver-xorg

since I could not change 

client glx vendor string: NVIDIA Corporation
[...]
OpenGL vendor string: Mesa

and when I restarted ubuntu I forgot that I did this and now I am at command line 

I have a lot of DATA on UBUNTU and research stuff and it is important for me to get it to work back 

HELP WOULD BE APPRECIATED ENORMOSLY 

THANKS 

Stevan

---

### Post by stevand on 2006-12-23
I still can approach and do sudo apt-get install .. and go through directories ...

moreover the file that was etc/X11/xorg.conf had a saved copy etc/X11/xorg.conf.2000345683
and which I looked at and it seems these two files are identical .....

I hpe so someone can take me out of this mess

thanks again

---

### Post by stevand on 2006-12-23
Additionally when I restart the Ubuntu it gives me a message

Failed to start X server (your graphical interface) It is likely it is not set up correctly. Would you like to view the X server output to diagnose the problem;

I am using Ubuntu 6.06.1 

this is all info that might help

---

### Post by stevand on 2006-12-23
I also tried approach of TAURUS master
[http://ubuntuforums.org/showthread.php?t=293177&highlight=stevand](http://ubuntuforums.org/showthread.php?t=293177&highlight=stevand)

that helped me already and I conducted same steps like in this previous Thread

but  X server graphical interface is still broken

---

### Post by stevand on 2006-12-23
THere is additional info that pops up 

GDM: Xserver not found: /usr/bin/Xgl :0 :0 -fullscreen -ac  -accel glx:pbuffer -accel xv:fbo -kb -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt?
Error Command could not be executed!

Please install the X server or correct GDM configuration and restart GDM


If this helps somehow ....
thanks again

---

### Post by stevand on 2006-12-23
there is a post
that should help regarding this problem 
[http://ubuntuforums.org/showthread.php?t=322379&highlight=install+the+X+server](http://ubuntuforums.org/showthread.php?t=322379&highlight=install+the+X+server)

however several times I did the pocedure in this post and did not work as questions that I am providing are not correct I suppose

I have ubuntu instal onmy IBM laptop T30
and all informatio regarding laptop are given here 

[http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-58227#display](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-58227#display)

still I was not able to do it althought this should work ....

if there is some additional trick that has to be done .... it will be great to find out

---

### Post by stevand on 2006-12-24
Now I got the following message

debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process

it seems I tried this so many times and then I see in config.dat a lot of stuff 
like
Name; xserver-x0rg/config/null_string error
Value:True
Templaete 
Owner


actually now I have to config.dat
and config.dat-old files


PLEAS HELP AS IT SEEMS I MIGHT MAKE MORE PROBLEMS

---

### Post by spockrock on 2006-12-24
can you post your xorg.conf?

---

### Post by stevand on 2006-12-24
Finally
I noticed when I restart the system when it boots it says 
ubuntu kernel 2.6.15.21 i686

and I installed

Ubuntu 6.06.1 

should I degrade somehow .. and then try to fix

---

### Post by stevand on 2006-12-24
I have to write it since it is on laptop and I do not know how to get it to Desktop
just 5 minutes

---

### Post by spockrock on 2006-12-24
just one question is there a file /usr/bin/Xgl, as one of there errors you posted, says that could not be executed.

---

### Post by stevand on 2006-12-24
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

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
     # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
        Option           "XkbOptions"   "ctrl:nocaps"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "HorizScrollDelta"          "0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier       "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
        Driver           "ati"
        Bus ID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option         "DMPS"
EndSection

Section  "Screen"
          Identifier        "Default Screen"
          Device            "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
          Monnitor           "Generic Monitor"
          Default Depth        15
      SubSection "Display"
                Depth           1
                Modes          "1024x768"
      EndSubsection
           SubSection "Display"
                Depth           4
                Modes          "1024x768"
      EndSubsection
      SubSection "Display"
                Depth           8
                Modes          "1024x768"
      EndSubsection
      SubSection "Display"
                Depth           15
                Modes          "1024x768"
      EndSubsection
      SubSection "Display"
                Depth           16
                Modes          "1024x768"
      EndSubsection
      SubSection "Display"
                Depth           24
                Modes          "1024x768"
      EndSubsection
EndSection
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice      "Synaptic Touchpad"
EndSection
Section "DRI"
        Mode    0666
EndSection


Finally it think I did not miss anything ..... I do not know why I have all these options 1 , 4, 8 , 15, 16  ,24

maybe this is problem ...


more over I have several xorg.conf.#numbers

and when I ls -l
those are one that I generated while I was trying to xfix problem 
I also have xorg.conf.backup

thanks for help ... it will be great to get thinks back

---

### Post by stevand on 2006-12-24
no there is no file /usr/bin/Xgl

---

### Post by spockrock on 2006-12-24
why are you following an nvida guide when your xorg.conf is saying you have an ati card???

Also does your /etc/gdm/gdm-custom.conf have this at the end of the file?

```

[servers]
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -kb
flexible=true

```

because if so remove it and I think your x server should work fine.

---

### Post by stevand on 2006-12-24
Yes it has

[servers]
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -kb
flexible=true

at the end of /etc/gdm/gdm-custom.conf

I am fool I do not know much ...

---

### Post by spockrock on 2006-12-24
plx remove that stuff or make it look like this,

```

#[servers]
#0=Xgl

#[server-Xgl]
#name=Xgl server
#command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -kb
#flexible=true
```

Also you have a gfx card made that has an ati gpu, not an nvidia gpu.  if you are serious about installing xgl/aiglx or beryl, use an ati guide plx.

---

### Post by stevand on 2006-12-24
I did it so file gdm.conf-custom at the end looks like this


#[servers]
#0=Xgl

#[server-Xgl]
#name=Xgl server
#command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -kb
#flexible=true

---

### Post by spockrock on 2006-12-24
right and then when you do sudo /etc/init.d/gdm restart what happens??

---

### Post by stevand on 2006-12-24
I got it back although  I have some fuzzy background like it is not sharp like it used to be 

can I change something to put it back to 1024 x 768 resolution that I had before

---

### Post by stevand on 2006-12-24
Or let me ask how to put optimal parameters for X server since now some other apllications
do not work ....
Paraview it just crashes
should I change resolution somehow or is there any safe way to do it

---

### Post by spockrock on 2006-12-24
if you installed the ATI drivers before?? and yes getting your resolutions back is easy, but if you haven't install the ati drivers.
go here on how to,

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI?action=show&redirect=BinaryDriverHowto%2Fati](https://help.ubuntu.com/community/BinaryDriverHowto/ATI?action=show&redirect=BinaryDriverHowto%2Fati)

---

### Post by stevand on 2006-12-24
How I can find out if ati drivers are installed or not is any way to check that first ....
I made a mess already so I have to be more caoution since some applications I will have I assume to reinstall 
tnx

---

### Post by spockrock on 2006-12-24
> **stevand said:**
> How I can find out if ati drivers are installed or not is any way to check that first ....
I made a mess already so I have to be more caoution since some applications I will have I assume to reinstall 
tnx

ok well if you wanna see if you have ati drivers installed, open terminal and sudo nano /etc/X11/xorg.conf

find this section
```

Section "Device"
Identifier "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
Driver "ati"
Bus ID "PCI:1:0:0"
EndSection
```

change the this line
```
Driver "ati"
```
to
```
Driver "fglrx"
```

save, exit and then in terminal do sudo /etc/init.d/gdm restart

if x fails, then sudo nano /etc/X11/xorg.conf and change the "fglrx" to "ati" and do sudo /etc/init.d/gdm restart

and you should get x back and working if you did everything right.

---

### Post by stevand on 2006-12-24
I returned everything as it was, however I am getting the following message when I run some applications

stevand@stevand-laptop:~$ paraview
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Aborted
stevand@stevand-laptop:~$



Should I go to /etc/gdm/gdm-custom.conf  and errase

#[servers]
#0=Xgl

#[server-Xgl]
#name=Xgl server
#command=/usr/bin/Xgl :0 -fullscreen -ac -accel glxbuffer -accel xv:fbo -kb
#flexible=true

all off this in order to get other stuff to work ....

and if I do "glxinfo" this happenes 


stevand@stevand-laptop:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 16 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 16 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Puzzeld what to do:confused:

---

