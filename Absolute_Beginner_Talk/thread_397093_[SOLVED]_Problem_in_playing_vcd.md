---
title: "[SOLVED] Problem in playing vcd"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by Hutom on 2007-03-30
I can't play vcd in totem movie player. I have tried both **totem- xime** and **totem - gstream**. None of them worked. **vlc player** too did not work. When I open the cd and double click on the .dat file (the default name is as usual avseq01.dat) the following message pops up -- 

" [COLOR="Red"]**Cannot open avseq01.dat**[/COLOR]

The filename "avseq01.dat" indicates that this file is of type "MPEG video". The contents of the file indicate that the file is of type "plain text document". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "plain text document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. "

When I reinserted the disc the totem movie player window opened. But then a message came -- 

"**There is no input plugin to handle the location of this movie**". 

I have also tried automatix. Nothing is working. So need your help. :(

---

### Post by Jonam on 2007-03-30
Have a look at this thread:

[http://www.ubuntuforums.org/showthread.php?t=380953](http://www.ubuntuforums.org/showthread.php?t=380953)

I (and others) have had some fun getting VCDs working. Gxine, Xine and Mplayer work reliably. I cannot get Totem and VLC to work at all. Try Mplayer from the command line as follows:

mplayer -v -identify vcd://

Hope this helps.

Jonam

---

### Post by Hutom on 2007-03-31
Dear, how can I install mplayer? I am using ubuntu 6.1.  I checked this forum and found that it could be installed through multiverse. So I checked these tabs -- system>administration>software sources . I found that multiverse is already activated. Then I searched the synaptic package manager for 'mplayer'. But there I did not find 'mplayer'. Instead, I found 'kmplayer'. Now, I don't know whether they are same. I think they are not. So what to do?

---

### Post by Maestro23 on 2007-03-31
> **Hutom said:**
> Dear, how can I install mplayer? I am using ubuntu 6.1.  I checked this forum and found that it could be installed through multiverse. So I checked these tabs -- system>administration>software sources . I found that multiverse is already activated. Then I searched the synaptic package manager for 'mplayer'. But there I did not find 'mplayer'. Instead, I found 'kmplayer'. Now, I don't know whether they are same. I think they are not. So what to do?

If you have all your repositories enabled, you should see mplayer in there.  kmplayer is mplayer for KDE.  Make sure you have the w32codecs installed as well.

You can go in terminal and type:

> sudo aptitude install mplayer

Double check your repositories: [https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

---

### Post by Hutom on 2007-03-31
Well, I again checked the software sources. Made all the repositories enabled. Then I reloaded. Following message came --

"[COLOR="Red"]Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preference.[/COLOR] "

Then a second window came with the message --

"[COLOR="Red"]An error occured

The following details are provided:

E: Malformed line 5 in source list /etc/apt/sources.list (dist parse)
E: Unable to lock the list directory[/COLOR] "

Then I closed all the windows and typed --
'sudo aptitude install mplayer'
in the terminal. The following reply came--

[COLOR="Red"]E: Malformed line 5 in source list /etc/apt/sources.list (dist parse)
E: Malformed line 5 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.[/COLOR]

See,  I'm very new to Linux and cannot handle it comfortably. It is only 3 days back I installed it and have not yet explored it to a satisfactory level. Don't know really where to get what. So please don't mind if you find my actions little foolish. I need your help to make life little easy.

---

### Post by Maestro23 on 2007-03-31
Need to look at your [COLOR="Red"]/etc/apt/sources.list[/COLOR]

Open a terminal and type:

> cat /etc/apt/sources.list

This will list the contents of your [COLOR="Red"]sources.list [/COLOR]file.  Then copy/past that output here.

---

### Post by Hutom on 2007-03-31
Reply is here --

# 
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy restricted


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse #Added by software-properties
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted #Added by software-properties
#AUTOMATIX REPOS END

---

### Post by Hutom on 2007-03-31
I was trying to install mplayer, which I didn't find in package manager in spite of having all repositories enabled. I tried to re enable it through the software sources tab.   Following error occurred --

"[COLOR="Red"]Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preference.[/COLOR] "

I tried to check my source list. Typed "[COLOR="Red"]cat /etc/apt/sources.list[/COLOR]" in the terminal. Following reply came --

> #
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy restricted


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse #Added by software-properties
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted #Added by software-properties
#AUTOMATIX REPOS END

I tried to remove AUTOMATIX. Now my add/remove is not working. It says,

[COLOR="Red"]This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.[/COLOR]

So, what should I do now?

---

### Post by Hutom on 2007-03-31
Problem resolved.:guitar:

---

### Post by Hutom on 2007-03-31
Sorry, problem partially resolved. Repository download and add remove are working fine now. Thanks a lot to Maestro23. However I still cannot open a vcd.

---

### Post by Maestro23 on 2007-03-31
> **Hutom said:**
> Sorry, problem partially resolved. Repository download and add remove are working fine now. Thanks a lot to Maestro23. However I still cannot open a vcd.

What is the error you get when you try open a vcd?

---

### Post by Hutom on 2007-03-31
Totem - xine says --

[COLOR="Red"]Totem could not play 'vcd:///media/cdrom0'.
There is no input plugin to handle the location of this movie[/COLOR]

Then I opened Mplayer to open disc. It says --
 Fatal error.
Error opening/initializing the selected video_out(-vo) device.

---

### Post by Jonam on 2007-04-01
You can try a different video device. Mplayer has the following available:

Available video output drivers:
        xmga    Matrox G200/G4x0/G550 overlay in X11 window (using /dev/mga_vid)
        mga     Matrox G200/G4x0/G550 overlay (/dev/mga_vid)
        tdfxfb  3Dfx Banshee/Voodoo3/Voodoo5
        3dfx    3dfx (/dev/3dfx)
        xvmc    XVideo Motion Compensation
        xv      X11/Xv
        x11     X11 ( XImage/Shm )
        xover   General X11 driver for overlay capable video output drivers
        gl      X11 (OpenGL)
        gl2     X11 (OpenGL) - multiple textures version
        dga     DGA ( Direct Graphic Access V2.0 )
        sdl     SDL YUV/RGB/BGR renderer (SDL v1.1.7+ only!)
        ggi     General Graphics Interface (GGI) output
        fbdev   Framebuffer Device
        fbdev2  Framebuffer Device
        aa      AAlib
        caca    libcaca
        dxr3    DXR3/H+ video out
        xvidix  X11 (VIDIX)
        cvidix  console VIDIX
        null    Null video output
        mpegpes Mpeg-PES to DVB card
        yuv4mpeg        yuv4mpeg output for mjpegtools
        png     PNG file
        jpeg    JPEG file
        gif89a  animated GIF output
        tga     Targa output
        pnm     PPM/PGM/PGMYUV file
        md5sum  md5sum of each frame

The command to select xv driver would be:

mplayer -vo xv vcd://

Suggest you try the xv, gl, x11 first or you might find one that matches your video card. Check the output of mplayer to see if it complains about the driver. Typically, this might be something like:

FATAL: Could not initialize video filters (-vf) or video output (-vo).

Hope this helps.

Jonam

---

### Post by Hutom on 2007-04-01
I typed the command, "mplayer -vo xv vcd://". Here is the reply,


> MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 2800+ (Family: 15, Model: 4, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
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

Playing vcd://.
track 01:  adr=1  ctrl=4  format=2  00:02:00  mode: 3
track 02:  adr=1  ctrl=4  format=2  00:21:21  mode: 3
MPEG-PS file format detected.
MPEG: No audio stream found -> no sound.
VIDEO:  MPEG1  352x288  (aspect 8)  25.000 fps  1100.0 kbps (137.5 kbyte/s)
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 352 x 288 (preferred colorspace: Mpeg PES)
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
VDec: vo config request - 352 x 288 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.30:1 - prescaling to correct movie aspect.
VO: [xv] 352x288 => 376x288 Planar YV12 
V:   0.0   1/  1 ??% ??% ??,?% 0 0 

Exiting... (End of file)



I think I need the appropriate codec. What I don't know is which codec, where to find that and how to install that.

---

### Post by Jonam on 2007-04-01
I installed libmpeg3-1 and libxine-extracodecs to fix a no sound problem with VCDs. These can be found in the standard repositories through Synaptic package manager. That being said, my output from mplayer is the same for the video section, only the last bit appears different (no audio in yours) - here it is:

==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 352 x 288 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 44100 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
Starting playback...
VDec: vo config request - 352 x 288 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 352x288 => 384x288 Planar YV12
A:   6.7 V:   7.3 A-V: -0.563 ct: -0.536 134/134  8%  1%  1.2% 4 0
alsa-uninit: pcm closed

Exiting... (End of file)

You might also want to try putting vcd://2 to play the second track (which I assume is the movie).

Jonam

---

### Post by Maestro23 on 2007-04-01
Resticted Formats (Codecs): [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Hutom on 2007-04-02
Thank you guys. Problem is almost resolved. I have installed the codecs. But vcd was not working. Then, thanks to jonam, [COLOR="Red"]vcd://2[/COLOR] is working. Both audio and video are coming fine. All xv, gl, x11 are working. But the problem now is when I type,  [COLOR="Red"]mplayer -vo gl vcd://2[/COLOR] a small mplayer window opens and starts playing the vcd. However it does not show me an options menu. So I cannot full screen it, cannot control the volume. It just plays on its own and does not allow me to control it in any way. But I think a little more effort can fix the problem.

---

### Post by kwidzin on 2007-04-20
> **Hutom said:**
> I can't play vcd in totem movie player. I have tried both **totem- xime** and **totem - gstream**.
Just switch from totem %m to totem vcd:// under gconf editor (/desktop/gnome/volume_manager). Totem-xine playing vcd without any issue.

---

### Post by feistybird on 2007-04-24
My gxine used to work fine to play vcd with the previous 6.10, but not any more after upgraded to Feisty. 

totem-gstreamer & totem-xine doesn't work neither.

Only "mplayer vcd://2" worked.

---

### Post by Jonam on 2007-04-30
@Hutom

You should be able to right click over the mplayer window and get a menu of options.

@feistybird

I have never been able to get VCDs to work with either version of totem. Gxine, Xine and Mplayer work reliably for me. I am using Dapper.

Jonam

---

### Post by Hutom on 2008-03-30
Thanks to all. Just changed the value to **vcd2** and things are working.

---

