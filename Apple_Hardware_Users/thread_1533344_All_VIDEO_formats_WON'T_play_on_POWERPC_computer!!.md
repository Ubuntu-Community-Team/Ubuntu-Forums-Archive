---
title: "All VIDEO formats WON'T play on POWERPC computer?!?!"
date: 2010-07-17
forum: Apple Hardware Users
---

### Post by 828688 Ben on 2010-07-17
Every video (I have tried almost every video format out there) I try to play in vlc player and movie player won't play. When I try to play a video I get a black screen, but I do hear sound (the sound always works). 

I am using Ubuntu 10.04 LTS (as of typing this, everything is up to date).

Here are the specs of my computer:
> Hardware Overview:

  Model Name:    Power Mac G5
  Model Identifier:    PowerMac7,3
  Processor Name:    PowerPC G5  (3.0)
  Processor Speed:    2 GHz
  Number Of CPUs:    2
  L2 Cache (per CPU):    512 KB
  Memory:    1.5 GB
  Bus Speed:    1 GHz
  Boot ROM Version:    5.2.4f1

ATA Bus:

PIONEER DVD-RW  DVR-109:

  Model:    PIONEER DVD-RW  DVR-109
  Revision:    A912
  Detachable Drive:    No
  Protocol:    ATAPI
  Unit Number:    0
  Socket Type:    Internal
  Low Power Polling:    Yes
  Power Off:    No

PIONEER DVD-RW  DVR-109:

  Firmware Revision:    A912
  Interconnect:    ATAPI
  Burn Support:    Yes (Apple Shipping Drive)
  Cache:    2000 KB
  Reads DVD:    Yes
  CD-Write:    -R, -RW
  DVD-Write:    -R, -RW, +R, +R DL, +RW
  Write Strategies:    CD-TAO, CD-SAO, CD-Raw, DVD-DAO
  Media:    Insert media and refresh to show available burn speeds

ATI Radeon 9600:

  Chipset Model:    ATY,RV351
  Type:    Display
  Bus:    AGP
  Slot:    SLOT-1
  VRAM (Total):    128 MB
  Vendor:    ATI (0x1002)
  Device ID:    0x4150
  Revision ID:    0x0000
  ROM Revision:    113-A58504-112
  Displays:
HF237:
  Resolution:    1920 x 1080 @ 60 Hz
  Depth:    32-Bit Color
  Core Image:    Hardware Accelerated
  Main Display:    Yes
  Mirror:    Off
  Online:    Yes
  Quartz Extreme:    Supported
  Rotation:    SupportedAlso, (not sure if this helps) extra visual effects (in appearance preferences)  works just fine for me.

Here are some of my installed plugins that I already have installed:
[IMG]http://lh6.ggpht.com/_FI33gwIVx5s/TEJMbZBCMiI/AAAAAAAAAUw/8xQrf98duno/Screenshot-1.png[/IMG]

Am I missing anything? Does this have to do with me having a powerpc processor? How do i fix this?

**_What am I doing wrong???_**


Thanks,
Ben

---

### Post by rjcalifornia on 2010-07-17
Hello there! First of all, VLC for the Power Architecture is broken. You have to compile it if you want to use it....


However there is an easier solution: Install Xine. Xine will play almost every video. 

Open Terminal, type this:

```
sudo apt-get install xine-ui
```

Good Luck!

Visit [milocker.com]("http://www.milocker.com")!

---

### Post by 828688 Ben on 2010-07-18
Darn, same problem as with vlc player and movie player (no video (black screen), but working sound).

Not sure if this helps, but here is my xine installation in terminal: 

> ben@ben-desktop:~$ sudo apt-get install xine-ui
[sudo] password for ben: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libreadline5 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin
  libxine1-console libxine1-ffmpeg libxine1-misc-plugins libxine1-x libxvmc1
Suggested packages:
  libxine1-doc libxine-doc
The following NEW packages will be installed:
  libreadline5 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin
  libxine1-console libxine1-ffmpeg libxine1-misc-plugins libxine1-x libxvmc1
  xine-ui
0 upgraded, 12 newly installed, 0 to remove and 0 not upgraded.
Need to get 4,545kB/4,565kB of archives.
After this operation, 11.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid/main libreadline5 5.2-7build1 [138kB]
Get:2 [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid/main libxcb-shape0 1.5-2 [9,500B]
Get:3 [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid/main libxcb-shm0 1.5-2 [9,206B]
Get:4 [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid/main libxcb-xv0 1.5-2 [13.0kB]
Get:5 [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid/main libxine1-bin 1.1.17-1ubuntu3 [1,270kB]
Get:6 [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid/main libxine1-misc-plugins 1.1.17-1ubuntu3 [895kB]
Get:7 [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid/main libxine1-x 1.1.17-1ubuntu3 [145kB]
Get:8 [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid/main libxine1-console 1.1.17-1ubuntu3 [40.6kB]
Get:9 [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid/main libxine1 1.1.17-1ubuntu3 [1,610B]
Get:10 [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid/main libxine1-ffmpeg 1.1.17-1ubuntu3 [429kB]
Get:11 [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) lucid/universe xine-ui 0.99.5+cvs20070914-2.1 [1,593kB]
Fetched 4,545kB in 3s (1,177kB/s)   
Selecting previously deselected package libreadline5.
(Reading database ... 108913 files and directories currently installed.)
Unpacking libreadline5 (from .../libreadline5_5.2-7build1_powerpc.deb) ...
Selecting previously deselected package libxcb-shape0.
Unpacking libxcb-shape0 (from .../libxcb-shape0_1.5-2_powerpc.deb) ...
Selecting previously deselected package libxcb-shm0.
Unpacking libxcb-shm0 (from .../libxcb-shm0_1.5-2_powerpc.deb) ...
Selecting previously deselected package libxcb-xv0.
Unpacking libxcb-xv0 (from .../libxcb-xv0_1.5-2_powerpc.deb) ...
Selecting previously deselected package libxine1-bin.
Unpacking libxine1-bin (from .../libxine1-bin_1.1.17-1ubuntu3_powerpc.deb) ...
Selecting previously deselected package libxine1-misc-plugins.
Unpacking libxine1-misc-plugins (from .../libxine1-misc-plugins_1.1.17-1ubuntu3_powerpc.deb) ...
Selecting previously deselected package libxvmc1.
Unpacking libxvmc1 (from .../libxvmc1_2%3a1.0.5-1ubuntu1_powerpc.deb) ...
Selecting previously deselected package libxine1-x.
Unpacking libxine1-x (from .../libxine1-x_1.1.17-1ubuntu3_powerpc.deb) ...
Selecting previously deselected package libxine1-console.
Unpacking libxine1-console (from .../libxine1-console_1.1.17-1ubuntu3_powerpc.deb) ...
Selecting previously deselected package libxine1.
Unpacking libxine1 (from .../libxine1_1.1.17-1ubuntu3_powerpc.deb) ...
Selecting previously deselected package libxine1-ffmpeg.
Unpacking libxine1-ffmpeg (from .../libxine1-ffmpeg_1.1.17-1ubuntu3_powerpc.deb) ...
Selecting previously deselected package xine-ui.
Unpacking xine-ui (from .../xine-ui_0.99.5+cvs20070914-2.1_powerpc.deb) ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Setting up libreadline5 (5.2-7build1) ...

Setting up libxcb-shape0 (1.5-2) ...

Setting up libxcb-shm0 (1.5-2) ...

Setting up libxcb-xv0 (1.5-2) ...

Setting up libxine1-bin (1.1.17-1ubuntu3) ...

Setting up libxine1-misc-plugins (1.1.17-1ubuntu3) ...

Setting up libxvmc1 (2:1.0.5-1ubuntu1) ...

Setting up libxine1-x (1.1.17-1ubuntu3) ...

Setting up libxine1-console (1.1.17-1ubuntu3) ...

Setting up libxine1 (1.1.17-1ubuntu3) ...

Setting up libxine1-ffmpeg (1.1.17-1ubuntu3) ...

Setting up xine-ui (0.99.5+cvs20070914-2.1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
ben@ben-desktop:~$ 


Any ideas??


Thanks,
Ben

---

### Post by linuxopjemac on 2010-07-18
I am afraid that video is not very well supported in Ubuntu/PPC. Ask Conal, he has experience.

[http://ubuntuforums.org/showthread.php?t=1385579&highlight=conal](http://ubuntuforums.org/showthread.php?t=1385579&highlight=conal)

---

### Post by 828688 Ben on 2010-07-18
I tried the suggested link, followed the instructions perfectly, and still, no video (black screen) and working audio.

Any ideas????


Thanks,
Ben

---

### Post by linuxopjemac on 2010-07-18
nope, sorry...I would switch to Debian...

---

### Post by zeroti on 2010-07-18
This may be related:

[http://ubuntuforums.org/showthread.php?t=1461635](http://ubuntuforums.org/showthread.php?t=1461635)

Are you also currently unable to enable visual effects in the Appearance preference pane?

---

### Post by 828688 Ben on 2010-07-18
Nope, visual effects work fine for me, AFTER I did the following modifications:

I disabled KMS for my radeon card AND I used this for my xorg.conf file:
> Section "Device"
    Identifier    "Radeon 9600"
    Driver        "ati"
    Option        "DynamicClocks" "true"
    Option        "AGPMode" "4"
    Option        "AGPFastWrite" "true"
    Option        "UseFBDev" "false"
    Option        "DRI" "true"
    Option        "GARTSize" "64"
    Option        "AddARGBGLXVisuals" "true"
    Option        "XAANoOffscreenPixmaps"
    Option        "DisableGLXRootClipping" "true"
    Option        "AllowGLXWithComposite" "true"
    Option        "EnablePageFlip" "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"    
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Radeon 9600"
    Monitor        "Configured Monitor"
    DefaultDepth 24
SubSection "Display"
    Depth 24
    Modes "1920x1080"
EndSubSection
EndSection

Section "DRI"
    Mode 0666
EndSection

Section "Extensions"
    Option        "Composite" "Enable"
EndSection  


Could this be because I disabled KMS (just a guess)???



Thanks,
Ben

---

### Post by rjcalifornia on 2010-07-19
probably... change it back...

---

### Post by sha.goyjo on 2010-07-19
> **rjcalifornia said:**
> probably... change it back...

Okay, a few notes. If you re-enable KMS you are going to lose 3d rendering, more than likely. I have yet to get KMS DRI to run on a powerpc. But that's just me. Maybe you'll have more luck.

I don't think this is a codec problem. Not to start trolling, but I really hate it when people push their own personal pet software on a problem instead of trying to make the software of the end user work. Unless there is a real. I don't think xine, or any other video player is going to solve this problem. 

As far as switching to debian goes, I'm not quite sure how much that will help. I'd do some more research first before making that move. As you know, ubuntu is based on a modified version of Debian Sid. There is no real guarantee that your problem won't crop up there again. There is always the possibility that a distro swap will solve your problem, but all that really means is that there is a difference in the compiles or config files between those distros. Find the diff and you can get the same result without leaving ubuntu.

So, enough of my ranting. I think that (from what little I know about video) something is going wrong in the initialization of the video window itself. By that I do not mean the player, but the space inside the player where it displays video. This is why the issue seems to exist in every player you use. In order to confirm this, can you give us the output of trying to run vlc on a file in the terminal?

Also, you might want to try these steps (from [http://ubuntuforums.org/showthread.php?t=459020):](http://ubuntuforums.org/showthread.php?t=459020):)
fix video rendering with certain apps that show only a black screen when run under Beryl:
1. set VLC->Settings->Preferences->Video->Output modules->X11 video output
2. set Mplayer->Preferences->Video->X11
3. for Mplayer firefox plugin: MAY need to edit /etc/mplayer/mplayer.conf:
replace line near top that says: #-vo=xv, with this: -vo=gl #changes video output driver from xv to gl. (n.b.: at least one person reported not being able to resize windows if using -vo=x11)

Let me know if any of this helps.

Sha

---

### Post by 828688 Ben on 2010-07-19
_YES_, vlc player now works for video files!!! However, flah still does not work in firefox and movies on dvd's don't play corretly.
Here is what playing a dvd looks like:
Image at: [http://picasaweb.google.com/105894630625974900772/NewAlbum6310358PM#5495680714058692386](http://picasaweb.google.com/105894630625974900772/NewAlbum6310358PM#5495680714058692386)
I don't know if this helps, but here is what my mplayer.conf looks like (this is what it looks like before I modified it (which, by the way, did not work)):
> #
# MPlayer configuration file
#
# Configuration files are read system-wide from /etc/mplayer/mplayer.conf
# and per user from ~/.mplayer/config, where per-user settings override
# system-wide settings, all of which are overrriden by the command line.
#
# The configuration file settings are the same as the command line
# options without the preceding '-'.
#
# See the CONFIGURATION FILES section in the man page
# for a detailed description of the syntax.


##################
# video settings #
##################

# Specify default video driver (see -vo help for a list).
# vo=xv,x11

# FBdev driver:
#
# mode to use (read from fb.modes)
#fbmode = 640x480-120
#
# location of the fb.modes file
#fbmodeconfig = /etc/fb.modes

# Specify your monitor timings for the vesa and fbdev video output drivers.
# See /etc/X11/XF86Config for timings. Be careful; if you specify settings
# that exceed the capabilities of your monitor, you may damage it.
#
# horizontal frequency range (k stands for 1000)
#monitor-hfreq = 31.5k-50k,70k
#
# vertical frequency range
#monitor-vfreq = 50-90
#
# dotclock (or pixelclock) range (m stands for 1000000)
#monitor-dotclock = 30M-300M

# Start in fullscreen mode by default.
#fs=yes

# Change to a different videomode when going fullscreen.
#vm=yes

# Override the autodetected color depth, may need 'vm=yes' as well.
#bpp=0

# Enable software scaling (powerful CPU needed) for video output
# drivers that do not support hardware scaling.
#zoom=yes

# standard monitor size, with square pixels
#monitoraspect=4:3

# Use this for a widescreen monitor, non-square pixels.
#monitoraspect=16:9

# Keep the player window on top of all other windows.
#ontop=yes


##################
# audio settings #
##################

# Use pulse, then alsa, then SDL video with the aalib subdriver by default.
ao=pulse,alsa,sdl:aalib

# Use SDL audio driver with the esd subdriver by default.
#ao = sdl:esd

# Specify the mixer device.
#mixer = /dev/mixer

# Resample the sound to 44100Hz with the lavcresample audio filter.
#af=lavcresample=44100


##################
# other settings #
##################

stop-xscreensaver=yes

# Pretend to be Window Media Player.
# Fixes playback when playlist and media file use the same URL.
#user-agent=NSPlayer/4.1.0.3856

# Drop frames to preserve audio/video sync.
#framedrop = yes

# Specify your preferred skin here (skins are searched for in
# /usr/local/share/mplayer/skins/<name> and ~/.mplayer/skins/<name>).
#skin = Abyss

# Resample the font alphamap.
# 0     plain white fonts
# 0.75  very narrow black outline (default)
# 1     narrow black outline
# 10    bold black outline
#ffactor = 0.75

# cache settings
#
# Use 8MB input cache by default.
#cache = 8192
#
# Prefill 20% of the cache before starting playback.
#cache-min = 20.0
#
# Prefill 50% of the cache before restarting playback after the cache emptied.
#cache-seek-min = 50

# DVD: Display English subtitles if available.
#slang = en

# DVD: Play English audio tracks if available.
#alang = en

###################
# DVDNAV Settings #
###################
#vc=ffmpeg12,

# You can also include other configuration files.
#include = /path/to/the/file/you/want/to/includeIs there something else I can modify (in this file) to try to get it to work?

Thanks for the help,
Ben

---

### Post by zeroti on 2010-07-19
I'm not sure if you've done this, but if you haven't, give this a shot:

```
sudo apt-get install ubuntu-restricted-extras
```

and check this out:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

You could also try playing dvds in vlc. Just go to Media -> Open Disk.

As for flash, there is no official support from Adobe for PPC Linux. However, there is lightspark, which seems like a promising open-source alternative coming up:

[http://ubuntuforums.org/showthread.php?t=1533742](http://ubuntuforums.org/showthread.php?t=1533742)

Good luck. I don't really know much about mplayer.conf, but from reading the top of it, it looks like you should preferably make changes to ~/.mplayer/config where ~ is your home directory.

---

### Post by khelben1979 on 2010-07-21
I've actually been able to watch some YouTube at my old Powerbook G3 lombard (Debian Lenny installed at the time) using [gnash]("http://en.wikipedia.org/wiki/Gnash"), but the speed was terrible, of course. :)

You might want to try it out!

---

### Post by imrazor on 2010-07-21
> **khelben1979 said:**
> I've actually been able to watch some YouTube at my old Powerbook G3 lombard (Debian Lenny installed at the time) using [gnash]("http://en.wikipedia.org/wiki/Gnash"), but the speed was terrible, of course. :)

You might want to try it out!

I've found gnash to be *very* slow playing youtube videos on PPC64, but it does play them. I basically use it to preview videos before grabbing them with a Firefox extension for local viewing, which works flawlessly. I also had to use a Greasemonkey script to fool gnash and/or youtube that the videos were embedded.

I also had some trouble getting local videos to play on my G5. I believe I rectified most of this by running:

# apt-get install ubuntu-restricted-extras

and also by running:

# gstreamer-properties

and then selecting either X11 or Xv output. I only had X11 output available until I disabled KMS and installed a preconfigured Xorg.conf very similar to one already posted in this thread (I have a Radeon 9700 Pro flashed with a Mac ROM), though I did apply a couple of performance tweaks. Xv was then available with much better performance.

Oddly enough VLC won't play videos off my HFS+ drive even though totem has absolutely no problem playing them. If I move the videos to my ext4 drive, VLC will play them perfectly. Can anyone explain that behavior? I've already changed my Linux UID to match the one on the HFS+ volume (namely 501.)

---

### Post by JoeMac42 on 2010-07-23
how would I go about turning on/off kms?

---

### Post by zeroti on 2010-07-23
> **JoeMac42 said:**
> how would I go about turning on/off kms?

look here:

[http://ubuntuforums.org/showthread.php?t=1460926&page=2](http://ubuntuforums.org/showthread.php?t=1460926&page=2)

---

### Post by JoeMac42 on 2010-07-23
Ok, so I'm thinking this doesn't apply to me since my windtunnel G4 uses the nouveau driver with an nVidia GeForce 6600, not ATI

---

