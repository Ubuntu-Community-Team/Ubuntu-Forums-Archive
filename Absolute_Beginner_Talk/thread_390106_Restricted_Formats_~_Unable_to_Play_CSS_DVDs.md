---
title: "Restricted Formats ~ Unable to Play CSS DVDs"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by fi_ on 2007-03-21
**[COLOR="Red"]Now resolved - many thanks![/COLOR]**


Hi,

I'm unable to play movie DVDs and would appreciate any help please if someone knows a fix.

I'm using Ubuntu version 6.10 (Edgy Eft) on a packard bell laptop EASYNOTE GN45-032.

So far, I've followed the steps in guide to restricted formats [https://help.ubuntu.com/community/RestrictedFormats#head-6524aff77dac67a074cbaf46657ce6c2104341e2]("https://help.ubuntu.com/community/RestrictedFormats#head-6524aff77dac67a074cbaf46657ce6c2104341e2") including installation of libdvdcss2 (version 1.2.5-1) by using:
> sudo /usr/share/doc/libdvdread3/install-css.sh

and extra codecs for Gstreamer by using:
> sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxinelibxine-main1 libxine-extracodecs ogle ogle-gui

I've also tried the troubleshooting guide and obtained the following info from 'setregion':
> fiona@spiral:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: NONE
vendor resets available: 4
user controlled changes resets available: 5
drive plays discs from region(s):, mask=0xFF

Would you like to change the region setting of your drive? [y/n]:n


The applications I have tried using to watch DVDs are: MoviePlayer(Totem), Ogle and gxine. Ogle seems to just quit out while Totem reports 'missing appropriate plugins' and gxine returns to it's splash screen.

Am I possibly missing some extra step(s) that are needed?

---

### Post by rustybronco on 2007-03-21
I installed vlc player works fine it's available in the universe.

[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)
or try..
[http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)

---

### Post by fi_ on 2007-03-21
Thanks Rusty. 

I've just tested VLC - unfortunately it's behavior matches the other 'DVD playing apps' -  it will play an .avi file or 'homemade' DVD perfectly but quits out when I try a commercial movie DVD.

---

### Post by rustybronco on 2007-03-21
I  installed vlc and the required dependencys ( libdvdcss2 and ? i don't recall) and it worked with home made and store bought dvds.

---

### Post by tcrroadie on 2007-03-21
Did you first install libdvdread3?
```

sudo aptitude install libdvdread3 
```

Your installation should have looked like this
```

sudo aptitude install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh
```

You will also need libdvdcss2 to be able to read encripted movie disc.

```
sudo aptitude install libdvdcss2
```

You will also need to install w32codecs in order to play mp3's and .avi's

```
sudo aptitude install w32codecs
```

For installing proprietary codecs on Ubuntu you may want to try installing an application called Automatix.  Automatix will allow you to easily install non free codecs and applications such as Adobe Reader.  Please see the link below for installation instructions on Ubuntu.
[URL="http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu"]
How to install Automatix2[/URL]

---

### Post by fi_ on 2007-03-21
Thanks for your comments tcrroadie.

Yes I have libdvdread3 and libdvdcss2 installed.

W32codecs installed and there is no problem with .avi or mp3 playback.

I will try Automatix2 as a last option if there are no other suggestions...

---

### Post by tcrroadie on 2007-03-21
Have you tried Mplayer?  I believe mplayer is not installed by default so you may need to install it.
```

sudo aptitude install mplayer
```

I love mplayer.  It has always played every video I have thrown at it.  You can try to play your DVD disc with mplayer by launching mplayer and right clicking on the player window and selecting DVD. 

Sorry I can't remember exactly what mplayers menu looks like, I'm on my Apple ibook at the moment. 

If you are still having problems with playback, try opening a terminal window and launching mplayer or vlc from the terminal so that you can use the terminal to help track down your playback problem.  For examply you would open Gnome Terminal and start mplayer 
```

kris@edgy$ mplayer
```

Then try to open a DVD movie and check your terminal window for error messages.  Then you can post back with the error messages you recieve. 

Hope this helps. :)

---

### Post by fi_ on 2007-03-21
Actually I think my installation of **libdvdcss2** might be corrupt...

if I use the command:

sudo /usr/share/doc/libdvdread3/install-css.sh

my terminal session returns:

fiona@spiral:~$ sudo /usr/share/doc/libdvdread3/install-css.sh
Password:
--00:02:11--  [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb)
           => `/tmp/libdvdcss.deb'
Resolving [www.dtek.chalmers.se](www.dtek.chalmers.se)... 129.16.30.198
Connecting to www.dtek.chalmers.se|129.16.30.198|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 25,178 (25K) [text/plain]

100%[====================================>] 25,178       145.57K/s             

00:02:11 (145.03 KB/s) - `/tmp/libdvdcss.deb' saved [25178/25178]

(Reading database ... 110329 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.5-1 (using /tmp/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.5-1) ...

fiona@spiral:~$ 

And this was the basis for my belief that I had **libdvdcss2** installed. However, I have just tried to test a manual install of **libdvdcss2** by downloading it from here [http://http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2-dev_1.2.5-1_i386.deb]("http://http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2-dev_1.2.5-1_i386.deb") and then trying to run it - and it returns the error message **'Error: Dependancy is not satisfiable: libc6-dev'**

Unfortunately, I've no idea how to install libc6-dev!

Meanwhile, thanks for the suggestion of mplayer **tcrroadie**, I already have it iinstalled however trying to run it on a DVD currently causes it to freeze with a black window that can't be closed. I will read the manual file and try to use it by command line, so far the attempt:

mplayer dvd://BBCDVD1159

produces:

Playing dvd://BBCDVD1159.
The hostname option must be an integer: BBCDVD1159
Struct dvd, field hostname parsing error: BBCDVD1159
Reading disc structure, please wait...
There are 10 titles on this DVD.
There are 7 chapters in this DVD title.
There are 1 angles in this DVD title.
libdvdread: Invalid title IFO (VTS_01_0.IFO).
libdvdread: Invalid title IFO (VTS_01_0.BUP).
Cannot open the IFO file for DVD title 1.
File not found: 'BBCDVD1159'
Failed to open dvd://BBCDVD1159.

---

### Post by qpwoeiruty on 2007-03-21
> **fi_ said:**
> Unfortunately, I've no idea how to install libc6-dev!

sudo apt-get install libc6-dev ???

---

### Post by scxtt on 2007-03-21
if you want to be sure if libdvdcss2 is installed, do the following:
```
[font=courier]scxtt@madiera-kubuntu [~]
:> aptitude search libdvd
i   libdvdcss2                                - a portable abstraction library for DVD decryption
p   libdvdnav-dev                             - The DVD navigation library, development package
i   libdvdnav4                                - The DVD navigation library
i   libdvdplay0                               - portable abstraction library for DVD menus support
p   libdvdplay0-dev                           - development files for libdvdplay0
p   libdvdread-dev                            - library for reading DVDs (development)
i   libdvdread3                               - library for reading DVDs
v   libdvdread3-dev                           -[/font]
```when i've got a fresh install of ubuntu and i want to watch dvds, all i have to do is:

sudo aptitude install libdvdnav4 libdvdplay0 libdvdread3

and then run the "install css" script that libdvdread provides ...

---

### Post by fi_ on 2007-03-21
Thanks **qpwoeiruty** I wasn't sure of the command line to use (it wasn't found via a search using the gui synaptic package manager). 

Unfortunately it didn't work:

fiona@spiral:~$ sudo apt-get install libc6-dev
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libc6-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libc6-dev has no installation candidate

I have Open Source (universe), Open Source (main), Restricted by copyright (multiverse), Proprietary  drivers (restricted) and Source Code repositories enabled.

---

### Post by scxtt on 2007-03-21
what do you get for the following:
```
[font=courier]:> **aptitude show libc6-dev**
Package: libc6-dev
State: installed
Automatically installed: no
Version: 2.4-1ubuntu12.3
Priority: optional
Section: libdevel
Maintainer: Ubuntu Core Developers <ubuntu-devel@lists.ubuntu.com>
Uncompressed Size: 8061k
Depends: libc6 (= 2.4-1ubuntu12.3), linux-libc-dev
Recommends: gcc | c-compiler
Suggests: glibc-doc, manpages-dev
Conflicts: libstdc++2.10-dev (< 1:2.95.2-15), gcc-2.95 (< 1:2.95.3-9), libpthread0-dev, libdl1-dev, libdb1-dev,
           libgdbm1-dev, libc6-dev (< 2.0.110-1), locales (< 2.1.3-5), libstdc++2.9-dev, netkit-rpc, libc-dev
Replaces: man-db (<= 2.3.10-41), gettext (<= 0.10.26-1), ppp (<= 2.2.0f-24), libgdbmg1-dev (<= 1.7.3-24), ldso (<=
          1.9.11-9), netkit-rpc, netbase (< 4.0), kerberos4kth-dev (< 1.2.2-10), libc6-prof (< 2.3.5-2)
Provides: libc-dev
Description: GNU C Library: Development Libraries and Header Files
 Contains the symlinks, headers, and object files needed to compile and link programs which use the standard C library.[/font]
```

---

### Post by fi_ on 2007-03-21
Thanks **scxtt**. I used the command you suggested:

fiona@spiral:~$ aptitude search libdvd
i   libdvdcss2                      - a portable abstraction library for DVD dec
i   libdvdnav4                      - The DVD navigation library                
i   libdvdread3                     - library for reading DVDs                  

To see if anything extra would happen I tried:

fiona@spiral:~$ sudo aptitude install libdvdnav4 libdvdplay0 libdvdread3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "libdvdplay0"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

Could you possibly explain > and then run the "install css" script that libdvdread provides ... a little more? I'm very new to linux and not sure what you meant.

Thanks folks for all your help so far ~ it's much appreciated btw!

---

### Post by scxtt on 2007-03-21
it looks like **libdvdplay0** isn't installed - could be an issue - since you're getting " Couldn't find any package whose name or description matched "libdvdplay0" "
```
[font=courier]:> aptitude show libdvdplay0
Package: libdvdplay0
State: installed
Automatically installed: no
Version: 1.0.1-7
Priority: optional
**Section: universe/libs**
Maintainer: Sam Hocevar (Debian packages) <sam+deb@zoy.org>
Uncompressed Size: 119k
Depends: libc6 (>= 2.4-1), libdvdread3 (>= 0.9.6)
Description: portable abstraction library for DVD menus support
 libdvdplay is a portable abstraction library for DVD menus navigation support.  It provides low-level functions for DVD
 reading and seeking, as well as access to the DVD data (subtitles, languages, chapters). It also provides the virtual
 machine required for DVD navigation to the client application.

 This package contains the libdvdplay0 runtime library.[/font]
```

" "install css" script " just refers to running **sudo /usr/share/doc/libdvdread3/install-css.sh** ...

---

### Post by fi_ on 2007-03-21
> what do you get for the following: **aptitude show libc6-dev **

This returns:

fiona@spiral:~$ aptitude show libc6-dev
No candidate version found for libc6-dev
Package: libc6-dev
State: not a real package

---

### Post by scxtt on 2007-03-21
what's the output of **cat /etc/apt/sources.list**?

---

### Post by fi_ on 2007-03-21
> what's the output of cat /etc/apt/sources.list?

fiona@spiral:~$ cat /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by scxtt on 2007-03-21
change:

# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe

to:

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe

then do **sudo aptitude update** followed by **sudo aptitude search libdvdplay** and see if it's now aware of that package ...

---

### Post by fi_ on 2007-03-21
Thanks **scxtt**!

I removed the comment symbol, then worked backwards through some of the earlier steps as far as:

aptitude search libdvd

which now returns:

fiona@spiral:~$ aptitude search libdvd
i   libdvdcss2                      - a portable abstraction library for DVD dec
p   libdvdnav-dev                   - The DVD navigation library, development pa
i   libdvdnav4                      - The DVD navigation library                
i   libdvdplay0                     - portable abstraction library for DVD menus
p   libdvdplay0-dev                 - development files for libdvdplay0         
p   libdvdread-dev                  - library for reading DVDs (development)    
i   libdvdread3                     - library for reading DVDs                  
v   libdvdread3-dev 

I then ran the install css script again (sudo /usr/share/doc/libdvdread3/install-css.sh) and then tried using oggle to play a DVD again. No luck so I also rebooted just in case and this time tried VLC media player. It didn't work but I collected VLC's debug messages in case they are any help:

> main debug: adding playlist item `dvd:///dev/hdb' ( dvd:///dev/hdb )
main debug: creating new input thread
main debug: waiting for thread completion
main debug: thread 2993425312 (input) created at priority 0 (input/input.c:263)
main debug: `dvd:///dev/hdb' gives access `dvd' demux `' path `/dev/hdb'
main debug: creating demux: access='dvd' demux='' path='/dev/hdb'
main debug: looking for access_demux module: 2 candidates
dvdnav debug: trying to go to dvd menu
main debug: thread 2966420384 (dvdnav event thread handler) created at priority 0 (dvdnav.c:336)
main debug: using access_demux module "dvdnav"
main debug: meta information:
main debug:   - 'Title' = 'BBCDVD1159'
main debug: `dvd:///dev/hdb' successfully opened
dvdnav debug: DVDNAV_HOP_CHANNEL
dvdnav debug: DVDNAV_VTS_CHANGE
dvdnav debug:      - vtsN=1
dvdnav debug:      - domain=8
dvdnav debug: DVDNAV_CELL_CHANGE
dvdnav debug:      - cellN=1
dvdnav debug:      - pgN=1
dvdnav debug:      - cell_length=2606400
dvdnav debug:      - pg_length=2606400
dvdnav debug:      - pgc_length=2606400
dvdnav debug:      - cell_start=0
dvdnav debug:      - pg_start=0
dvdnav debug: DVDNAV_SPU_CLUT_CHANGE
dvdnav debug: DVDNAV_SPU_STREAM_CHANGE
dvdnav debug:      - physical_wide=0
dvdnav debug:      - physical_letterbox=1
dvdnav debug:      - physical_pan_scan=0
dvdnav debug: buttonUpdate 1
main debug: selecting program id=0
main debug: looking for decoder module: 24 candidates
main debug: using decoder module "spudec"
main debug: thread 2976455584 (decoder) created at priority 0 (input/decoder.c:159)
dvdnav debug: DVDNAV_AUDIO_STREAM_CHANGE
dvdnav debug:      - physical=0
dvdnav warning: cannot get next block (Error reading NAV packet.)
main debug: closing input
main debug: thread 2966420384 joined (dvdnav.c:352)
main debug: removing module "spudec"
main debug: thread 2976455584 joined (input/decoder.c:191)
main debug: killing decoder fourcc `spu ', 0 PES in FIFO
main debug: Program doesn't contain anymore ES
main debug: removing module "dvdnav"
main debug: thread 2993425312 joined (input/input.c:401)
main: nothing to play


---

### Post by scxtt on 2007-03-21
just for my own curiousity, what's the output of **cat /etc/group | grep fiona**?  when i get home (at work) i'll see what kind of console output i get when playing a dvd - cause i don't really see an "error" in what you posted above {aside from "dvdnav warning: cannot get next block (Error reading NAV packet.)", which looks like it doesn't like the disk :confused:}

---

### Post by fi_ on 2007-03-21
> what's the output of cat /etc/group | grep fiona? 

fiona@spiral:~$ cat /etc/group | grep fiona
admx4fiona
dialoutx20cupsys,fiona
cdromx24haldaemon,fiona
floppyx25haldaemon,fiona
audiox29fiona
dipx30fiona
videox44fiona
plugdevx46haldaemon,fiona
lpadminx109fiona
scannerx111cupsys,hplip,fiona
fionax1000:
adminx114fiona

This is a little mangled - I had to remove colons because the forum software was convinced eash line was an img link!

> when i get home (at work) i'll see what kind of console output i get when playing a dvd - cause i don't really see an "error" in what you posted above {aside from "dvdnav warning: cannot get next block (Error reading NAV packet.)", which looks like it doesn't like the disk }

No problem - thanks for trying!

I'll switch to another DVD for testing although I've tried before others as I've had this issue for a month.

Meanwhile I also stumbled on the format that produces debug info **tcrroadie** suggested:

> fiona@spiral:~$ mplayer -vo xv dvd://
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T5200  @ 1.60GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

Playing dvd://.
Reading disc structure, please wait...
There are 10 titles on this DVD.
There are 7 chapters in this DVD title.
There are 1 angles in this DVD title.
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00002724)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x002b3744)!!
DVD successfully opened.
MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  9400.0 kbps (1175.0 kbyte/s)
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
AC3: 2.0 (stereo)  48000 Hz  192.0 kbit/s
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
alsa-init: using device default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
a52: CRC check failed!  
a52: error at resampling
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 1024x576 Planar YV12 
a52: CRC check failed!  5.601 ct:  0.000   1/  1 ??% ??% ??,?% 0 0 
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  8.308 ct: -0.008   3/  3 ??% ??% ??,?% 0 0 
a52: error at resampling
a52: CRC check failed!  8.097 ct: -0.020   6/  6 ??% ??% ??,?% 1 0 
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  8.381 ct: -0.024   7/  7 ??% ??% ??,?% 2 0 
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  8.240 ct: -0.028   8/  8 ??% ??% ??,?% 3 0 
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  8.494 ct: -0.032   9/  9 ??% ??% ??,?% 4 0 
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  8.400 ct: -0.044  12/ 12 ??% ??% ??,?% 7 0 
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  8.654 ct: -0.048  13/ 13 ??% ??% ??,?% 8 0 
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  8.520 ct: -0.056  15/ 15 47%  1%  3.3% 10 0 
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
a52: CRC check failed!  
a52: error at resampling
alsa-uninit: pcm closed-8.860 ct: -0.060  16/ 16 65%  1%  3.7% 11 0 

Exiting... (Quit)


---

### Post by scxtt on 2007-03-21
have you tried running any of the video players as root (w/ sudo)?

---

### Post by fi_ on 2007-03-21
> have you tried running any of the video players as root (w/ sudo)?

I just tried mplayer (with a different DVD). It produced very similar output and a popup warning that I seemed to be trying to view an encrypted DVD without installling CSS decryption:

fiona@spiral:~$ sudo mplayer -vo xv dvd://
Password:
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T5200  @ 1.60GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

Playing dvd://.
Reading disc structure, please wait...
There are 10 titles on this DVD.
There are 7 chapters in this DVD title.
There are 1 angles in this DVD title.
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00002724)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x002b3744)!!
DVD successfully opened.
MPEG-PS file format detected.


MPlayer interrupted by signal 2 in module: video_read_properties
fiona@spiral:~$ sudo mplayer -vo xv dvd://
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T5200  @ 1.60GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

Playing dvd://.
Reading disc structure, please wait...
There are 4 titles on this DVD.
There are 28 chapters in this DVD title.
There are 1 angles in this DVD title.
libdvdread: Error cracking CSS key for /VIDEO_TS/VIDEO_TS.VOB (0x00000160)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00001280)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_0.VOB (0x002625e0)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x00262600)!!
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_0.VOB (0x0026e040)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_1.VOB (0x0026e060)!!
DVD successfully opened.

---

### Post by scxtt on 2007-03-21
hmm, that's interesting ... i use kaffeine myself - so i'll see what i get when i try from my PC @ home ( in about 2 hours :-\ ) ...

---

### Post by fi_ on 2007-03-21
I'm going to crash out - somehow it's almost 3am already - g'night :)

---

### Post by scxtt on 2007-03-22
here's what i get when i do **kaffeine dvd://**

```
[font=courier]:> kaffeine dvd://
/dev/dvb/adapter0/frontend0 : : No such file or directory
QLayout "unnamed" added to QWidget "unnamed", which already has a layout
libdvdnav: Using dvdnav version 1.1.2 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Attempting to use device /dev/sda1 mounted on / for CSS authentication
libdvdread: Could not open /dev/sda1 with libdvdcss.
libdvdread: Can't open /dev/sda1 for reading
libdvdread: Device /dev/sda1 inaccessible, CSS authentication not available.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/scxtt/.dvdnav/.map'
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
libdvdnav: Using dvdnav version 1.1.2 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdnav: DVD Title: THE_BIG_LEBOWSKI
libdvdnav: DVD Serial Number: 33226672
libdvdnav: DVD Title (Alternative): WIDESCREEN_R0
libdvdnav: Unable to find map file '/home/scxtt/.dvdnav/THE_BIG_LEBOWSKI.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000141
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000052a2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000d0f8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0031a100
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0031a104
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00332e5e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00332e62
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x003b3cab
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x003b3caf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x003ca4c7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003ca4cb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003ca4e2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003ca4e6
libdvdread: Elapsed time 0
libdvdread: Found 6 VTS's
libdvdread: Elapsed time 0[/font]
```i really didn't configure kaffeine in any way - it's part of kubuntu by default and it uses xine as the engine ... all i do after initial install is what i described above ...

do you have xine installed? (but it makes no sense that none of the one's you tried before don't work) ...
```
[font=courier]> aptitude search xine | grep "i   "
i   amarok-xine                     - xine engine for the amaroK audio player
i   kaffeine-xine                   - Xine engine for kaffeine media player
i   libxine-extracodecs             - the xine video/media player library, binar
i   libxine1                        - the xine video/media player library, binary[/font]
```

---

### Post by fi_ on 2007-03-22
> do you have xine installed? 

fiona@spiral:~$ aptitude search xine | grep "i   "
i   gxine                           - the xine video player, GTK+/Gnome user int
i   libxine-extracodecs             - the xine video/media player library, binar
i   libxine-main1                   - the xine video/media player library, trans
i   libxine1                        - the xine video/media player library, binar
i   libxinerama1                    - X11 Xinerama extension library            
i   totem-xine                      - A simple media player for the Gnome deskto
p   xine-ui                         - the xine video player, user interface

---

### Post by tcrroadie on 2007-03-22
I'm feeling that this is getting more complex than it should be.  I was reading over this thread again and noticed that you tried installing neccessary dvd libraries and codecs without the universe repositories enabled.  At least it looked that way to me.  

Why don't we just try reinstalling the dvd libraries and codecs again.  

I'm at work at the moment so please forgive me if some of the command line options are off.  

Step 1.  Reinstall DVD read support again.  

   1.  First enable all available repositories including backports. 

```
sudo nano /etc/apt/sources.list
```

   2.  Rebuild the apt cache. 

```
sudo apt-get clean
```
```

sudo apt-get update
```

    3.  Then reinstall DVD support.  Please see man apt-get if my option for reinstall is not correct. 
```

sudo apt-get -reinstall install libdvdread3
sudo /usr/share/doc/libdvdread3/install-css.sh
```


    4.  Reinstall nonfree codecs. 
```
sudo apt-get -reinstall install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs
```

Then try playing a DVD.  

Hope this helps. :)

---

### Post by lahook on 2007-03-22
have you tried playing older dvd's?
i can play most dvd's without problems, but some won't play. ie casino royale, open season.
i think it has something to do with Sony's new encryption. these dvd's are from Sony.
They start to play then quit and lockup and makes it hard to eject the dvd.
playing these dvd's on windows one player wouldn't play it ,but Interactive Video would.

could this be the problem?
any thoughts?

---

### Post by tcrroadie on 2007-03-22
^^^lahook^^^

Great suggestion.  I was also woundering about this, but just wanted to retrace the steps used for installation of dvd support.  

fi_ posted the problem right here in the output he recieved from mplayer.  I think you may be right though.  

```
Playing dvd://.
Reading disc structure, please wait...
There are 10 titles on this DVD.
There are 7 chapters in this DVD title.
There are 1 angles in this DVD title.
[B]libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00002724)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x002b3744)!![/B]
DVD successfully opened.
MPEG-PS file format detected.

```

---

### Post by fi_ on 2007-03-22
Thanks **tcrroadie**

> Why don't we just try reinstalling the dvd libraries and codecs again.

I'm at work at the moment so please forgive me if some of the command line options are off.

Step 1. Reinstall DVD read support again. 

1. First enable all available repositories including backports. 

sudo nano /etc/apt/sources.list

Done!

> 2. Rebuild the apt cache.

sudo apt-get clean

Done!

> sudo apt-get update

I had a bit of a problem here:
[HTML]
fiona@spiral:~$ sudo apt-get update
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Translation-en_US               
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US   
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports Release.gpg [191B]      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/main Translation-en_US         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/universe Translation-en_US     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/multiverse Translation-en_US   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Packages                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Sources                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/main Packages                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/restricted Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/universe Packages         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/multiverse Packages       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/main Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/restricted Sources             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/universe Sources               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-backports/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources             
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg                                 
  Could not connect to archive.ubuntu.com:80 (91.189.89.8), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.89.8), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.89.8), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.89.8), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.89.8), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (91.189.89.8), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.89.8), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.89.8), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.89.8), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.89.8), connection timed out
Fetched 3B in 40m0s (0B/s)                          
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg)  Could not connect to archive.ubuntu.com:80 (91.189.89.8), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.89.8), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.89.8), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.89.8), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.89.8), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg)  Could not connect to archive.ubuntu.com:80 (91.189.89.8), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.89.8), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.89.8), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.89.8), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.89.8), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.[/HTML]


> 3. Then reinstall DVD support. Please see man apt-get if my option for reinstall is not correct.


No problem with syntax was correct except '-reinstall' needs to be '--reinstall'

> 
sudo apt-get --reinstall install libdvdread3
sudo /usr/share/doc/libdvdread3/install-css.sh

Done!

> sudo apt-get --reinstall install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs

Done!
> Then try playing a DVD. 

Alas, very similar output. I'm using an old region 2 DVD (Monty Python & The Holy Grail) for testing btw ~ thanks for your suggestion **lahook** :)

[HTML]fiona@spiral:~$ sudo mplayer -vo xv dvd://
Password:
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T5200  @ 1.60GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

Playing dvd://.
Reading disc structure, please wait...
There are 4 titles on this DVD.
There are 28 chapters in this DVD title.
There are 1 angles in this DVD title.
libdvdread: Error cracking CSS key for /VIDEO_TS/VIDEO_TS.VOB (0x00000160)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00001280)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_0.VOB (0x002625e0)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x00262600)!!
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_0.VOB (0x0026e040)
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_1.VOB (0x0026e060)!!
DVD successfully opened.
MPEG-PS file format detected.
demux: File doesn't contain the selected audio or video stream.
MPEG: FATAL: EOF while searching for sequence header.
Video: Cannot read properties.
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
AC3: 2.0 (dolby)  48000 Hz  192.0 kbit/s
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
alsa-init: using device default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   0.0 (00.0) of 5303.1 ( 1:28:23.1) ??,?% 
alsa-uninit: pcm closed

Exiting... (End of file)[/HTML]

---

### Post by fazza on 2007-03-22
have you tried automatix yet? my laptop still has problems, but can normally  manage dvds now :)

---

### Post by tcrroadie on 2007-03-22
The error output you recieved from apt when you ran "sudo apt-get update" showed that apt bombed on the universe and multiverse repositories listed in your apt sources list.  

You should have recieved errors when trying to install packages from these repositories.  Did you?

I would suggest trying to use the U.S repositories.  Just remove the gb from the repository urls. 

1.  First backup your apt sources list.  

```
sudo cp /etc/apt/sources.list /etc/atp/sources.list.old
```

2.  Then make it look like this.  


```
deb http://archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
```

3.  Then run 
```
sudo apt-get clean 

sudo apt-get update
```

Then rerun the steps I listed in my previous post.  Please post any errors you recieve from apt.

If you still have problems with your sources.list, I'll post my sources.list from my machine when I get home. 

I hate to be repetitive, but something is not right.

---

### Post by fi_ on 2007-03-22
Thanks **tcrroadie**
> 
1. First backup your apt sources list.

sudo cp /etc/apt/sources.list /etc/atp/sources.list.old

This returned an error message:

fiona@spiral:~$ sudo cp /etc/apt/sources.list /etc/atp/sources.list.old
Password:
cp: cannot create regular file `/etc/atp/sources.list.old': No such file or directory

So I made a backup to my home directory:

fiona@spiral:~$ sudo cp /etc/apt/sources.list  /home/fiona/sources.list.old

> 2. Then make it look like this. 

Done! My sources.list now matches the text in this block exactly.

> 3. Then run:

sudo apt-get clean 

sudo apt-get update

The cleaning command was fine but the update still eventaully timed out on several updates:

[HTML]
fiona@spiral:~$ sudo apt-get clean
fiona@spiral:~$ sudo apt-get update
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]
Ign http://security.ubuntu.com edgy-security/main Translation-en_US            
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US 
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com edgy-security Release
Hit http://security.ubuntu.com edgy-security/main Packages               
Hit http://security.ubuntu.com edgy-security/restricted Packages
Hit http://security.ubuntu.com edgy-security/universe Packages
Hit http://security.ubuntu.com edgy-security/multiverse Packages
Hit http://security.ubuntu.com edgy-security/main Sources
Hit http://security.ubuntu.com edgy-security/restricted Sources
Hit http://security.ubuntu.com edgy-security/universe Sources
Hit http://security.ubuntu.com edgy-security/multiverse Sources
Err http://archive.ubuntu.com edgy Release.gpg                                 
  Could not connect to archive.ubuntu.com:80 (91.189.89.6), connection timed out
Err http://archive.ubuntu.com edgy/main Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.89.6), connection timed out
Err http://archive.ubuntu.com edgy/restricted Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.89.6), connection timed out
Err http://archive.ubuntu.com edgy/universe Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.89.6), connection timed out
Err http://archive.ubuntu.com edgy/multiverse Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.89.6), connection timed out
Err http://archive.ubuntu.com edgy/universe Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.89.6), connection timed out
Err http://archive.ubuntu.com edgy-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (91.189.89.6), connection timed out
Err http://archive.ubuntu.com edgy-updates/main Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.89.6), connection timed out
Err http://archive.ubuntu.com edgy-updates/restricted Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.89.6), connection timed out
Err http://archive.ubuntu.com edgy-updates/universe Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.89.6), connection timed out
Err http://archive.ubuntu.com edgy-updates/multiverse Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.89.6), connection timed out
Err http://archive.ubuntu.com edgy-backports Release.gpg
  Could not connect to archive.ubuntu.com:80 (91.189.89.6), connection timed out
Err http://archive.ubuntu.com edgy-backports/main Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.89.6), connection timed out
Err http://archive.ubuntu.com edgy-backports/restricted Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.89.6), connection timed out
Err http://archive.ubuntu.com edgy-backports/universe Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.89.6), connection timed out
Err http://archive.ubuntu.com edgy-backports/multiverse Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.89.6), connection timed out
Fetched 1B in 1h4m0s (0B/s)                         
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg  Could not connect to archive.ubuntu.com:80 (91.189.89.6), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2  Could not connect to archive.ubuntu.com:80 (91.189.89.6), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_US.bz2  Could not connect to archive.ubuntu.com:80 (91.189.89.6), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2  Could not connect to archive.ubuntu.com:80 (91.189.89.6), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_US.bz2  Could not connect to archive.ubuntu.com:80 (91.189.89.6), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2  Could not connect to archive.ubuntu.com:80 (91.189.89.6), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg  Could not connect to archive.ubuntu.com:80 (91.189.89.6), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_US.bz2  Could not connect to archive.ubuntu.com:80 (91.189.89.6), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_US.bz2  Could not connect to archive.ubuntu.com:80 (91.189.89.6), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/i18n/Translation-en_US.bz2  Could not connect to archive.ubuntu.com:80 (91.189.89.6), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/i18n/Translation-en_US.bz2  Could not connect to archive.ubuntu.com:80 (91.189.89.6), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/Release.gpg  Could not connect to archive.ubuntu.com:80 (91.189.89.6), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/i18n/Translation-en_US.bz2  Could not connect to archive.ubuntu.com:80 (91.189.89.6), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/i18n/Translation-en_US.bz2  Could not connect to archive.ubuntu.com:80 (91.189.89.6), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/i18n/Translation-en_US.bz2  Could not connect to archive.ubuntu.com:80 (91.189.89.6), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/i18n/Translation-en_US.bz2  Could not connect to archive.ubuntu.com:80 (91.189.89.6), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.[/HTML]

At this point I was concerned that I had made a mistake somewhere when manually editing sources.list and so I went back and copy / pasted the exact text (i.e the entire file contents) from this thread. This is how I can be sure that the contents of this file now exactly match. I then repeated step 3, which produced the same timeout errors again.

4. Reisntalling DVD support (I've carried on with this step so that I can post the error messages).

fiona@spiral:~$  sudo apt-get --reinstall install libdvdread3
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of libdvdread3 is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

It seemed sensible to stop here!

> I hate to be repetitive, but something is not right.

Please don't worry about that, I appreciate your help.

---

### Post by tcrroadie on 2007-03-22
> 1. First backup your apt sources list.

sudo cp /etc/apt/sources.list /etc/atp/sources.list.old

Oops.  I had a typo in their.  Your copy destination should have read /etc/apt/sources.list.old.  Sorry about that.  But you still did a great job.  

Hey by the way.  You are doing a great job so far.  

I think that your main problem is stemming from an issue with your apt sources list.  For future reference, if you ever recieve any error messages after running "sudo apt-get update", take note of them because you may run into problems installing packages, like what is happening here. 

```
fiona@spiral:~$ sudo apt-get --reinstall install libdvdread3
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reinstallation of libdvdread3 is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Thanks for posting this message from apt.  As we can see, apt cannot install libdvdread3 because of an issue with your source.list.  Apt is having a problem downloading package information from the remote servers.  

For future reference.  Always take note of the meassage printed on the screen from apt.  If you run into problems, it will greatly speed up problem solving.  Just for this reason, I always install and maintain my packages from a terminal using apt-get or aptitude. 

I'll tell you what.  Give me a couple of hours to get home and test the repositories in my source.list on my system at home.  I'm at work at the moment and don't have an Ubuntu Linux machine available to me.  I'll just post my apt sources.list for you to use and you should be good to go.  

Hang in their.  Your almost there. :)

---

### Post by tcrroadie on 2007-03-22
Just curious. 

Please post the output of these to lines. 

```
sudo aptitude show libdvdread3
```

And the output of this.  This line will run a script that should install css decryption if libdvdread3 is installed correctly.

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

Thanks.

---

### Post by fi_ on 2007-03-22
Thanks **tcrroadie**!
> Please post the output of these two lines:

sudo aptitude show libdvdread3

[HTML]fiona@spiral:~$ sudo aptitude show libdvdread3
Password:
Package: libdvdread3
State: installed
Automatically installed: no
Version: 0.9.6-3ubuntu1
Priority: optional
Section: libs
Maintainer: Daniel Baumann <daniel@debian.org>
Uncompressed Size: 184k
Depends: libc6 (>= 2.4-1)
Suggests: libdvdcss2, wget
Description: library for reading DVDs
 libdvdread provides the functionality that is required to access many DVDs. It
 parses IFO files, reads NAV-blocks, and performs CSS authentication and
 descrambling. 
 
 libdvdread currently uses libdl to dynamically probe for libdvdcss at runtime.
 If found, libdvdcss will be used to decrypt sections of the DVD as necessary.[/HTML]

> And the output of this:

sudo /usr/share/doc/libdvdread3/install-css.sh

[HTML]fiona@spiral:~$ sudo /usr/share/doc/libdvdread3/install-css.sh
--21:26:18--  http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb
           => `/tmp/libdvdcss.deb'
Resolving www.dtek.chalmers.se... 129.16.30.198
Connecting to www.dtek.chalmers.se|129.16.30.198|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 25,178 (25K) [text/plain]

100%[====================================>] 25,178       154.85K/s             

21:26:19 (154.28 KB/s) - `/tmp/libdvdcss.deb' saved [25178/25178]

(Reading database ... 110437 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.5-1 (using /tmp/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.5-1) ...
[/HTML]

Btw **fazza** I'm still putting off automatix while users like **tcrroadie** and **scxtt** are patient enough to help me try and fix the problem at a more manual  level because 1) I'm learning much more this way and 2) I'm not sure automatrix would work any better while I have a repositories problem. I didn't mean to ignore your post though & thanks for the suggestion.

---

### Post by tcrroadie on 2007-03-22
> **fi_ said:**
> Thanks **tcrroadie**!


[HTML]fiona@spiral:~$ sudo aptitude show libdvdread3
Password:
Package: libdvdread3
State: installed
Automatically installed: no
Version: 0.9.6-3ubuntu1
Priority: optional
Section: libs
Maintainer: Daniel Baumann <daniel@debian.org>
Uncompressed Size: 184k
Depends: libc6 (>= 2.4-1)
Suggests: libdvdcss2, wget
Description: library for reading DVDs
 libdvdread provides the functionality that is required to access many DVDs. It
 parses IFO files, reads NAV-blocks, and performs CSS authentication and
 descrambling. 
 
 libdvdread currently uses libdl to dynamically probe for libdvdcss at runtime.
 If found, libdvdcss will be used to decrypt sections of the DVD as necessary.[/HTML]



[HTML]fiona@spiral:~$ sudo /usr/share/doc/libdvdread3/install-css.sh
--21:26:18--  http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb
           => `/tmp/libdvdcss.deb'
Resolving www.dtek.chalmers.se... 129.16.30.198
Connecting to www.dtek.chalmers.se|129.16.30.198|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 25,178 (25K) [text/plain]

100%[====================================>] 25,178       154.85K/s             

21:26:19 (154.28 KB/s) - `/tmp/libdvdcss.deb' saved [25178/25178]

(Reading database ... 110437 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.5-1 (using /tmp/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.5-1) ...
[/HTML]

Btw **fazza** I'm still putting off automatix while users like **tcrroadie** and **scxtt** are patient enough to help me try and fix the problem at a more manual  level because 1) I'm learning much more this way and 2) I'm not sure automatrix would work any better while I have a repositories problem. I didn't mean to ignore your post though & thanks for the suggestion.

I don't see anything wrong here.  dvdcss support looks to be installed correctly.  I am really wondering if the playback problems you are having is really do to the disc you are using.  Do you have any more commercial DVD movie disc available to try?  

I have to apologize for my previous error on editing your apt source list.  I forgot that there is "us" in front of archive.ubuntu.com  I am including my source.list from my machine in an attachment for you to use.  You can do with it what you please.  It should work for you.  

Ohh, by the way, the Automatix team is in the process of moving to a new server.  So you will not be able to use Automatix until it is back up.  You can find installation instructions on the Ubuntu Guide. 

[How to install Automatix2 on Ubuntu]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu")

My apt sources.list.  Also see attachment.
```

# 
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
#deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse


#deb http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse universe
#deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse universe
#deb http://security.ubuntu.com/ubuntu edgy-security universe
#deb-src http://security.ubuntu.com/ubuntu edgy-security universe

## Automatix repo
deb http://www.getautomatix.com/apt edgy main

#AUTOMATIX REPOS START

deb http://archive.canonical.com/ubuntu edgy-commercial main

deb http://dl.google.com/linux/deb/ stable non-free

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
#AUTOMATIX REPOS END

#Beryl Repository
deb http://ubuntu.beryl-project.org/ edgy main

#Nvidia beta driver
deb http://albertomilone.com/drivers/edgy/nonlegacy/32bit binary/

## E17 repository "edevelop.org"
deb http://edevelop.org/pkg-e/ubuntu edgy e17
deb-src http://edevelop.org/pkg-e/ubuntu edgy e17

## E17 Repository "e17.dunnewind.net"
#deb http://e17.dunnewind.net/ubuntu edgy e17
#deb-src http://e17.dunnewind.net/ubuntu edgy e17
```

Time to take the dog for a walk.  Talk later.  :)

---

### Post by fi_ on 2007-03-22
Thanks **tcrroadie**

I read your sources.list and then edited mine to include the 'us' prefix in the first 3 sections. I haven't added any # characters to the final section because I wasn't sure about that. My sources.list file now looks this:

[HTML]deb http://archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
[/HTML]

I then used the command:

sudo apt-get clean

Which seemed fine (no response message produced).

Followed by:

sudo apt-get update

This only gets to 99% again and then begins to time out as follows:

[HTML]fiona@spiral:~$ sudo apt-get clean 
fiona@spiral:~$ sudo apt-get update
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]
Ign http://security.ubuntu.com edgy-security/main Translation-en_US            
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US      
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US        
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US      
Hit http://security.ubuntu.com edgy-security Release                           
Hit http://security.ubuntu.com edgy-security/main Packages                     
Hit http://security.ubuntu.com edgy-security/restricted Packages               
Hit http://security.ubuntu.com edgy-security/universe Packages                 
Hit http://security.ubuntu.com edgy-security/multiverse Packages               
Hit http://security.ubuntu.com edgy-security/main Sources                      
Hit http://security.ubuntu.com edgy-security/restricted Sources                
Hit http://security.ubuntu.com edgy-security/universe Sources                  
Hit http://security.ubuntu.com edgy-security/multiverse Sources                
99% [Connecting to archive.ubuntu.com (91.189.89.6)] [Connecting to us.archive.
[/HTML]

After 10mins I used ctrl C to quit out of the update because I'm running out of time for tonight and was pretty sure that it wouldn't work but I can capture the full message tomorrow night after work if it's helpful.

I swapped my test DVD for another old region 2 movie (The Matrix) and then swapped to an oldish region 1 DVD (Criterion Edn of Seven Samurai) and retested VLC and movie player totem - but the error messages were no different.

Thanks for your help today - I'll have access to my laptop again tomorrow night to try again.

---

### Post by cowlip on 2007-03-22
Do you know if your dvd drive has any firmware updates?  DVDs woudn't work in Windows XP/Linux (they only worked in Windows 98 ) until I updated the firmware itself.

---

### Post by fenian on 2007-03-22
From the info in your original post it looks as though you do not have a regionfree dvd drive and the region has not been set at all.This is the output I get when running regionset on my regionfree dvd drive...

> $ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not retrieve region code settings of the drive!
This could mean your drive is region free and doesn't need any setting.
Would you like to change the region setting of your drive? [y/n]:

I believe you will need to set the region code to something (usually the region you live in or where most of your dvds are from-for me in the US its region1 a list of codes is[ here]("http://en.wikipedia.org/wiki/DVD_region_code").After setting the region libdvdread3 should work with CSS and mplayer (or whatever app you use) to play dvds from any region.


From the ubuntu wiki...
     >  Most players (eg mplayer/vlc) with most DVD drives are able to ignore the value of the region setting. However, it must have been set to something; if it hasn't been initialized, even non-region-restricted DVDs won't play. Also, if it is necessary to crack the CSS key, it can sometimes take up to a few minutes to do so.


---

### Post by fi_ on 2007-03-23
Thanks **cowlip** I have checked packard bell's and Panasonic's website (Panasonic make the DVD drive) and googled without any luck.

Thanks **fenian**

> From the info in your original post it looks as though you do not have a regionfree dvd drive and the region has not From the info in your original post it looks as though you do not have a regionfree dvd drive and the region has not been set at all... ...I believe you will need to set the region code to something (usually the region you live in or where most of your dvds are from

[B]
Wayhey you were completely correct!!! [/B]I had misunderstood the output from regionset earlier (like a fool I thought it meant I had a 'region free' DVD drive). Once I used regionset to fix this as region 2 ALL my DVD playback apps work. Phew!

Btw for **tcrroadie** I managed to get the repositories working now without any errors - cheers to you for help with this!

[SIZE="3"]**Thank you so much to ALL the helpful people on this thread - I really appreciated your guidance.** :-)[/SIZE]

---

### Post by lukemack on 2007-04-16
Hi,

I think I may have a similar problem - I am unable to play commercial DVDs. I am in the UK. mplayer output is as follows:

```
luke@DeepThought:~$ sudo mplayer -vo xv dvd://
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU:               Intel(R) Pentium(R) 4 CPU 2.00GHz (Family: 15, Model: 2, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

Playing dvd://.
Reading disc structure, please wait...
There are 2 titles on this DVD.
There are 1 chapters in this DVD title.
There are 1 angles in this DVD title.
DVD successfully opened.
MPEG-PS file format detected.
MPEG: No audio stream found -> no sound.
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  9800.0 kbps (1225.0 kbyte/s)
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 1024x576 Planar YV12 
V:   0.6  22/ 22 30%  4%  0.0% 0 0 

Exiting... (End of file)

```

i dont seem to have regionset on my system. Just before exiting (above) the percentages after V: begin to increase and a black player window appears briefly before quiting. I;ve tried all installed players - VLC, totem, mplayer, ogle etc and all just quit with the exception of totem which errors out:

could not read from resource.

would really appreciate any help! I also tried the -vf spp and scale options in the above error - same result i.e application quits

---

### Post by lukemack on 2007-04-16
i installed regionset which gives the following output:

luke@DeepThought:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 2, mask=0xFD

Would you like to change the region setting of your drive? [y/n]:

I selected no as it is a region 2 disc and the drive seems to be set to region 2.

---

### Post by DavidHuttlestonJr on 2007-04-24
Thanks to everyone for this thread, my problems were solved with regionset as well.  Cheers!

---

